
"""
wrb_scenario_analysis_simple.py

Simplified WRB scenario analysis pipeline that *does not use ECL scalars*.
It:
 - reads MST (reference) and latest-quarter actuals
 - computes MST % ratios (R_*)
 - merges MST ratios with current-quarter exposures
 - projects future EAD and ECL using MST %s directly
 - pivots & exports results for Tableau

Author: ChatGPT (adapt to your environment)
"""

import os
import pandas as pd
import numpy as np
from datetime import datetime

# ---------- CONFIG / GLOBALS ----------
# Update this path to point to your global_inputs.csv or set paths directly below.
GLOBAL_INPUTS_CSV = "global_inputs.csv"

# Default dimension columns used in MST grouping and merges
DIM_COLS = ['approach', 'entity', 'country', 'product', 'fin_business_unit']

# ----------------- Utilities -----------------
def read_global_inputs(path=GLOBAL_INPUTS_CSV):
    """
    Expect a CSV with two columns: key, value
    Keys (example): working_folder, WRB_Ref_Q_FileName, WRB_Curr_Q_FileName, WRB_Curr_Q_BCRS_FN, WRB_Curr_Q_Digital_FN, actuals_year, curr_q_folder
    Returns a dict.
    """
    if not os.path.exists(path):
        raise FileNotFoundError(f"Global inputs file not found at {path}")
    g = pd.read_csv(path, header=None, index_col=0).to_dict()[1]
    return g

def ensure_dir(path):
    if not os.path.exists(path):
        os.makedirs(path, exist_ok=True)

def safe_read_csv(path):
    if not os.path.exists(path):
        raise FileNotFoundError(f"File not found: {path}")
    # read with flexible options
    return pd.read_csv(path, encoding='ISO-8859-1', dtype=str)

# ----------------- I/O & Cleanup -----------------
def read_input_files(inputs):
    """
    inputs: dict with keys pointing to filenames/paths for the MST ref + current quarter files.
    Returns pandas DataFrames: mst_df, curr_df, bcrs_df, digital_df
    """
    mst_path = inputs.get('WRB_Ref_Q_FileName')
    curr_path = inputs.get('WRB_Curr_Q_FileName')
    bcrs_path = inputs.get('WRB_Curr_Q_BCRS_FN')
    digital_path = inputs.get('WRB_Curr_Q_Digital_FN')

    mst_df = safe_read_csv(mst_path)
    curr_df = safe_read_csv(curr_path)
    bcrs_df = safe_read_csv(bcrs_path)
    digital_df = safe_read_csv(digital_path)

    return mst_df, curr_df, bcrs_df, digital_df

def basic_cleanup_numeric(df, numeric_cols):
    """
    Remove commas, spaces; coerce numeric columns to float; fillna(0).
    """
    for col in numeric_cols:
        if col in df.columns:
            # remove thousand separators and whitespace
            df[col] = df[col].astype(str).str.replace(r'[,\s]', '', regex=True).replace({'nan':''})
            df[col] = pd.to_numeric(df[col], errors='coerce').fillna(0.0)
        else:
            df[col] = 0.0
    return df

def standardize_columns_for_working(df):
    """
    Ensure expected columns exist (Scenario, projection_period, EAD_IFRS, EAD_IFRS_NDF, EAD_IFRS_DF, ECL_NDF, ECL_DF).
    Do not rename original dimension columns here; assume they exist.
    """
    expected = ['Scenario', 'projection_period', 'EAD_IFRS', 'EAD_IFRS_NDF', 'EAD_IFRS_DF', 'ECL_NDF', 'ECL_DF']
    for c in expected:
        if c not in df.columns:
            df[c] = 0.0
    return df

# ----------------- Reference Trends (MST) - Simple -----------------
def fn_WRB_Ref_Q_Trends_simple(WRB_Ref_Q):
    """
    Compute MST % ratios (R_*) grouped by DIM_COLS + Scenario + projection_period.
    Returns grouped DataFrame with R_EAD_DF_PC, R_EAD_NDF_PC, R_ECL_NDF_PC, R_ECL_DF_PC.
    """
    df = WRB_Ref_Q.copy()

    # Ensure numeric columns exist and are numeric
    numeric_cols = ['EAD_IFRS', 'EAD_IFRS_NDF', 'EAD_IFRS_DF', 'ECL_NDF', 'ECL_DF']
    df = basic_cleanup_numeric(df, numeric_cols)

    # Keep group keys that are present in df
    group_keys = [c for c in DIM_COLS if c in df.columns] + ['Scenario', 'projection_period']
    # aggregate
    agg_cols = numeric_cols
    grouped = df.groupby(group_keys, as_index=False)[agg_cols].sum()

    # Compute MST percentages (with guard)
    grouped['R_EAD_DF_PC'] = np.where(grouped['EAD_IFRS'] > 0,
                                      grouped['EAD_IFRS_DF'] / grouped['EAD_IFRS'], 0.0)
    grouped['R_EAD_NDF_PC'] = np.where(grouped['EAD_IFRS'] > 0,
                                       grouped['EAD_IFRS_NDF'] / grouped['EAD_IFRS'], 0.0)

    grouped['R_ECL_NDF_PC'] = np.where(grouped['EAD_IFRS_NDF'] > 0,
                                       grouped['ECL_NDF'] / grouped['EAD_IFRS_NDF'], 0.0)
    grouped['R_ECL_DF_PC'] = np.where(grouped['EAD_IFRS_DF'] > 0,
                                      grouped['ECL_DF'] / grouped['EAD_IFRS_DF'], 0.0)

    # Clip EAD splits to [0,1] (ECL% may be >1 in edge cases; keep as is but warn)
    grouped['R_EAD_DF_PC'] = grouped['R_EAD_DF_PC'].clip(0.0, 1.0)
    grouped['R_EAD_NDF_PC'] = grouped['R_EAD_NDF_PC'].clip(0.0, 1.0)

    return grouped

# ----------------- Merge MST trends with Current Quarter -----------------
def merge_current_and_ref(curr_full, mst_trends):
    """
    Merge current-quarter exposures (curr_full) with MST trends (mst_trends) on DIM_COLS + Scenario + projection_period.
    Returns merged DF (long). Use indicator to check merge quality.
    """
    left_keys = [c for c in DIM_COLS if c in curr_full.columns]
    # we'll merge on scenario & projection_period as well; if curr doesn't have projection_period
    merge_on = left_keys.copy()
    if 'Scenario' in curr_full.columns and 'Scenario' in mst_trends.columns:
        merge_on.append('Scenario')
    if 'projection_period' in mst_trends.columns:
        merge_on.append('projection_period')

    merged = pd.merge(curr_full, mst_trends, on=merge_on, how='left', indicator=True)
    # _merge shows 'both', 'left_only' (current had rows MST missing), 'right_only' (MST rows with no current match)
    return merged

# ----------------- Final Metrics (no scalars) -----------------
def fn_WRB_final_metrics_no_scalars(merged_df, curr_ead_col='EAD_IFRS'):
    """
    Use MST ratios directly (no ECL scalars) to compute:
      - EAD_DF_Yi, EAD_NDF_Yi
      - ECL_DF_Yi, ECL_NDF_Yi
    merged_df should contain current EAD (curr_ead_col) and MST ratio columns R_EAD_DF_PC, R_ECL_DF_PC, R_ECL_NDF_PC.
    """
    df = merged_df.copy()

    # Ensure current EAD numeric
    if curr_ead_col not in df.columns:
        raise KeyError(f"Expected current EAD column '{curr_ead_col}' in merged_df")
    df[curr_ead_col] = pd.to_numeric(df[curr_ead_col], errors='coerce').fillna(0.0)

    # Prepare YO splits from current if present (fallback)
    df['YO_EAD_NDF'] = pd.to_numeric(df.get('EAD_IFRS_NDF', 0)).fillna(0.0)
    df['YO_EAD_DF']  = pd.to_numeric(df.get('EAD_IFRS_DF',  0)).fillna(0.0)
    df['YO_R_EAD_DF_PC'] = np.where(df[curr_ead_col] > 0, df['YO_EAD_DF'] / df[curr_ead_col], 0.0)
    df['YO_R_EAD_NDF_PC'] = np.where(df[curr_ead_col] > 0, df['YO_EAD_NDF'] / df[curr_ead_col], 0.0)

    # ECL YO% fallbacks
    df['YO_R_ECL_NDF_PC'] = np.where(df['YO_EAD_NDF'] > 0,
                                     pd.to_numeric(df.get('ECL_NDF', 0)).fillna(0.0) / df['YO_EAD_NDF'],
                                     0.0)
    df['YO_R_ECL_DF_PC'] = np.where(df['YO_EAD_DF'] > 0,
                                    pd.to_numeric(df.get('ECL_DF', 0)).fillna(0.0) / df['YO_EAD_DF'],
                                    0.0)

    # Ensure MST R_* columns exist, else set NaN (we will fill with YO fallback)
    for c in ['R_EAD_DF_PC', 'R_EAD_NDF_PC', 'R_ECL_DF_PC', 'R_ECL_NDF_PC']:
        if c not in df.columns:
            df[c] = np.nan

    # Fill MST R*s with YO fallback where MST missing
    df['R_EAD_DF_PC'] = df['R_EAD_DF_PC'].fillna(df['YO_R_EAD_DF_PC'])
    df['R_EAD_NDF_PC'] = df['R_EAD_NDF_PC'].fillna(df['YO_R_EAD_NDF_PC'])
    df['R_ECL_DF_PC'] = df['R_ECL_DF_PC'].fillna(df['YO_R_ECL_DF_PC'])
    df['R_ECL_NDF_PC'] = df['R_ECL_NDF_PC'].fillna(df['YO_R_ECL_NDF_PC'])

    # Normalize NDF = 1 - DF (trust DF if present)
    df['R_EAD_NDF_PC'] = np.where(df['R_EAD_DF_PC'].notna(), 1.0 - df['R_EAD_DF_PC'], df['R_EAD_NDF_PC'])
    df['R_EAD_DF_PC'] = df['R_EAD_DF_PC'].clip(0.0,1.0)
    df['R_EAD_NDF_PC'] = df['R_EAD_NDF_PC'].clip(0.0,1.0)

    # Compute projected EAD for each row (applied to Year-0 EAD)
    df['EAD_DF_Yi'] = df[curr_ead_col] * df['R_EAD_DF_PC']
    df['EAD_NDF_Yi'] = df[curr_ead_col] - df['EAD_DF_Yi']

    # Project ECL using MST ECL% directly (no scalar)
    df['ECL_DF_Yi'] = df['EAD_DF_Yi'] * df['R_ECL_DF_PC']
    df['ECL_NDF_Yi'] = df['EAD_NDF_Yi'] * df['R_ECL_NDF_PC']

    # Cap ECLs at EADs
    df['ECL_DF_Yi'] = np.minimum(df['ECL_DF_Yi'], df['EAD_DF_Yi'])
    df['ECL_NDF_Yi'] = np.minimum(df['ECL_NDF_Yi'], df['EAD_NDF_Yi'])
    df['ECL_Total_Yi'] = df['ECL_DF_Yi'] + df['ECL_NDF_Yi']
    df['EAD_Total_Yi'] = df['EAD_DF_Yi'] + df['EAD_NDF_Yi']

    # Optional: round outputs to cents
    df['ECL_DF_Yi'] = df['ECL_DF_Yi'].round(2)
    df['ECL_NDF_Yi'] = df['ECL_NDF_Yi'].round(2)
    df['ECL_Total_Yi'] = df['ECL_Total_Yi'].round(2)
    df['EAD_DF_Yi'] = df['EAD_DF_Yi'].round(2)
    df['EAD_NDF_Yi'] = df['EAD_NDF_Yi'].round(2)

    # Drop helper YO columns (optional)
    helper_cols = ['YO_EAD_NDF','YO_EAD_DF','YO_R_EAD_DF_PC','YO_R_EAD_NDF_PC','YO_R_ECL_NDF_PC','YO_R_ECL_DF_PC']
    for c in helper_cols:
        if c in df.columns:
            df.drop(columns=[c], inplace=True)

    return df

# ----------------- Pivot Results for Tableau -----------------
def fn_pivot_results(df_long, index_cols=None, projection_col='projection_period'):
    """
    Convert long rows (with projection_period column) into wide format with Year-suffixed columns.
    Example output columns: EAD_DF_2025, ECL_Total_2027, etc.
    """
    if index_cols is None:
        index_cols = [c for c in DIM_COLS if c in df_long.columns] + ['Scenario']

    # Columns to pivot (we pivot EAD_DF_Yi, EAD_NDF_Yi, ECL_DF_Yi, ECL_NDF_Yi, ECL_Total_Yi)
    pivot_vars = [c for c in ['EAD_DF_Yi','EAD_NDF_Yi','ECL_DF_Yi','ECL_NDF_Yi','ECL_Total_Yi'] if c in df_long.columns]
    # Build wide by stacking pivot_vars one by one
    wide = df_long.copy()
    # create a year label from projection_period (if it's numeric) - if projection_period is an index like 0..26 you may want to offset to year: e.g., actuals_year + projection_period
    # For now, assume projection_period holds integer offset; we will just use it as suffix
    wide_cols = index_cols.copy()
    # create a pivot for each pivot_var and join
    result = wide[index_cols + [projection_col] + pivot_vars].copy()
    # melt and pivot to have variable + projection as columns then consolidate
    melted = result.melt(id_vars=index_cols + [projection_col], value_vars=pivot_vars,
                         var_name='metric', value_name='value')
    # create metric_year column
    melted['metric_year'] = melted['metric'] + "_" + melted[projection_col].astype(str)
    # pivot
    pivoted = melted.pivot_table(index=index_cols, columns='metric_year', values='value', aggfunc='sum').reset_index()
    # flatten columns
    pivoted.columns.name = None
    return pivoted

# ----------------- Export -----------------
def export_outputfiles(df_mst_trends, df_merged_proj, df_pivoted, out_folder):
    ensure_dir(out_folder)
    timestamp = datetime.now().strftime("%Y%m%d%H%M%S")
    mst_fn = os.path.join(out_folder, f"WRB_MST_Trends_{timestamp}.csv")
    merged_fn = os.path.join(out_folder, f"WRB_Projections_Long_{timestamp}.csv")
    pivot_fn = os.path.join(out_folder, f"WRB_Projections_Pivot_{timestamp}.csv")

    df_mst_trends.to_csv(mst_fn, index=False)
    df_merged_proj.to_csv(merged_fn, index=False)
    df_pivoted.to_csv(pivot_fn, index=False)

    print("Exported:", mst_fn, merged_fn, pivot_fn)
    return mst_fn, merged_fn, pivot_fn

# ----------------- Main pipeline -----------------
def main(global_inputs_path=GLOBAL_INPUTS_CSV):
    # Load global inputs
    inputs = read_global_inputs(global_inputs_path)
    working_folder = inputs.get('working_folder', '.')
    curr_q_folder = inputs.get('curr_q_folder', '')  # optional
    output_base = os.path.join(working_folder, 'outputs')
    # read input files
    mst_df, curr_df, bcrs_df, digital_df = read_input_files(inputs)
    print("Read files:", mst_df.shape, curr_df.shape, bcrs_df.shape, digital_df.shape)

    # Clean numeric columns in MST & current pieces
    numeric_cols = ['EAD_IFRS', 'EAD_IFRS_NDF', 'EAD_IFRS_DF', 'ECL_NDF', 'ECL_DF']
    mst_df = standardize_columns_for_working(mst_df)
    curr_df = standardize_columns_for_working(curr_df)
    bcrs_df = standardize_columns_for_working(bcrs_df)
    digital_df = standardize_columns_for_working(digital_df)

    mst_df = basic_cleanup_numeric(mst_df, numeric_cols)
    curr_df = basic_cleanup_numeric(curr_df, numeric_cols)
    bcrs_df = basic_cleanup_numeric(bcrs_df, numeric_cols)
    digital_df = basic_cleanup_numeric(digital_df, numeric_cols)

    # Combine current quarter sources
    curr_full = pd.concat([curr_df, bcrs_df, digital_df], axis=0, ignore_index=True)
    # Make sure current EAD column exists, named 'EAD_IFRS'
    if 'EAD_IFRS' not in curr_full.columns:
        raise KeyError("EAD_IFRS (current EAD) missing from current quarter files")

    # 1) Generate MST trends (R_*)
    mst_trends = fn_WRB_Ref_Q_Trends_simple(mst_df)
    print("MST trends shape:", mst_trends.shape)

    # 2) Build a 'template' of projection periods you want to keep (optional)
    # If MST has many scenarios, you may want to keep only certain ones (T0/Base/CPY_Excl_SA/PTR_Excl_SA)
    keep_scenarios = inputs.get('keep_scenarios', "T0,Base,CPY_Excl_SA,PTR_Excl_SA").split(',')
    mst_trends = mst_trends[mst_trends['Scenario'].isin(keep_scenarios)]

    # 3) For projection, ensure each current row is repeated for every projection_period we need.
    # Approach: merge current file with mst_trends on DIM + Scenario; because mst_trends has projection_periods,
    # the left rows will be repeated for each projection year where mst_trends exist for that portfolio.
    merged = merge_current_and_ref(curr_full, mst_trends)
    print("Merged shape (curr x mst):", merged.shape)
    # Show merge diagnostics
    if '_merge' in merged.columns:
        merge_counts = merged['_merge'].value_counts().to_dict()
        print("Merge indicator counts:", merge_counts)

    # 4) Compute projections without scalars
    projected = fn_WRB_final_metrics_no_scalars(merged, curr_ead_col='EAD_IFRS')
    print("Projected shape:", projected.shape)

    # 5) Pivot for tableau
    pivoted = fn_pivot_results(projected)
    print("Pivoted shape:", pivoted.shape)

    # 6) Export outputs
    out_folder = os.path.join(output_base, inputs.get('curr_q_folder', 'current_q_outputs'))
    exported = export_outputfiles(mst_trends, projected, pivoted, out_folder)
    print("Pipeline completed. Exported files:", exported)


if __name__ == "__main__":
    # Run main (adjust path to your global_inputs.csv if needed)
    main()











nnnnnmnnnnnnnnnnn
import pandas as pd
import numpy as np

def hierarchical_merge(curr_expanded, mst_trends, key_sets):
    """Try merging with progressively reduced key sets."""
    merged = None
    unmatched = curr_expanded.copy()

    for keys in key_sets:
        if unmatched.empty:
            break

        m = pd.merge(unmatched, mst_trends, on=keys, how='left', indicator=True)

        matched = m[m['_merge']!='left_only'].copy()
        unmatched = m[m['_merge']=='left_only'][curr_expanded.columns]  # keep original cols for next iteration

        if merged is None:
            merged = matched
        else:
            merged = pd.concat([merged, matched], ignore_index=True)

    # Still unmatched after all merges: fill MST columns with NaN
    if not unmatched.empty:
        unmatched_mst_cols = [c for c in mst_trends.columns if c not in curr_expanded.columns]
        for c in unmatched_mst_cols:
            unmatched[c] = np.nan
        merged = pd.concat([merged, unmatched], ignore_index=True)

    return merged

def fn_WRB_final_metrics_no_scalars(df):
    """Compute projections, Year-0 override, cumulative LI."""
    df = df.copy()

    # --- Project exposures and ECL ---
    df['EAD_DF_Yi'] = df['EAD_IFRS'] * df['R_EAD_DF_PC']
    df['EAD_NDF_Yi'] = df['EAD_IFRS'] - df['EAD_DF_Yi']
    df['ECL_DF_Yi'] = df['EAD_DF_Yi'] * df['R_ECL_DF_PC']
    df['ECL_NDF_Yi'] = df['EAD_NDF_Yi'] * df['R_ECL_NDF_PC']
    df['ECL_Total_Yi'] = df['ECL_DF_Yi'] + df['ECL_NDF_Yi']

    # --- Force Year 0 to actuals ---
    mask0 = df['projection_period']==0
    df.loc[mask0,'EAD_DF_Yi']    = df.loc[mask0,'EAD_IFRS_DF']
    df.loc[mask0,'EAD_NDF_Yi']   = df.loc[mask0,'EAD_IFRS_NDF']
    df.loc[mask0,'ECL_DF_Yi']    = df.loc[mask0,'ECL_DF']
    df.loc[mask0,'ECL_NDF_Yi']   = df.loc[mask0,'ECL_NDF']
    df.loc[mask0,'ECL_Total_Yi'] = df.loc[mask0,'ECL_DF'] + df.loc[mask0,'ECL_NDF']

    # --- Compute baseline ECL_Total at Year 0 per portfolio ---
    group_cols = ['approach','entity','country','product','fin_business_unit','Scenario']
    baseline = df.loc[mask0, group_cols + ['ECL_Total_Yi']].rename(columns={'ECL_Total_Yi':'ECL_Total_Y0'})

    # merge baseline back
    df = df.merge(baseline, on=group_cols, how='left')

    # --- Compute cumulative LI ---
    df['CUMM_LI_Yi'] = (df['ECL_Total_Yi'] - df['ECL_Total_Y0']).clip(lower=0)

    return df

def run_projection(curr_full, mst_trends):
    """Full pipeline from current + MST → projected metrics."""

    # Step 1: get all projection periods from MST
    proj_periods = mst_trends['projection_period'].unique()
    proj_periods_df = pd.DataFrame({'projection_period': proj_periods})

    # Step 2: cross join current rows with all projection periods
    curr_full = curr_full.copy()
    curr_full['_tmpkey'] = 1
    proj_periods_df['_tmpkey'] = 1
    curr_expanded = pd.merge(curr_full, proj_periods_df, on='_tmpkey').drop('_tmpkey', axis=1)

    # Step 3: hierarchical merge
    key_sets = [
        ['approach','entity','country','product','fin_business_unit','Scenario','projection_period'],
        ['approach','entity','country','product','Scenario','projection_period'],
        ['approach','entity','country','Scenario','projection_period']
    ]
    merged = hierarchical_merge(curr_expanded, mst_trends, key_sets)

    # Step 4: rename current columns back to standard names
    merged2 = merged.rename(columns={
        'EAD_IFRS_x':'EAD_IFRS',
        'EAD_IFRS_NDF_x':'EAD_IFRS_NDF',
        'EAD_IFRS_DF_x':'EAD_IFRS_DF',
        'ECL_NDF_x':'ECL_NDF',
        'ECL_DF_x':'ECL_DF'
    })

    # Step 5: run projections + cumulative LI
    projected = fn_WRB_final_metrics_no_scalars(merged2)

    return projected

    projected = run_projection(curr_full, mst_trends)

# See your results
cols = ['Scenario','projection_period','EAD_DF_Yi','EAD_NDF_Yi','ECL_DF_Yi','ECL_NDF_Yi','ECL_Total_Yi','CUMM_LI_Yi']
print(projected[cols].head(20))
