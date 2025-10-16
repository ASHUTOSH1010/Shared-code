import pandas as pd

def handle_new_portfolios(curr_full, mst_trends):
    """
    Identify and append new portfolios that exist in current data (curr_full)
    but are missing in reference MST (mst_trends).
    """

    # Common dimension keys used to identify unique portfolios
    dim_cols = ['approach', 'entity', 'country', 'product', 'fin_business_unit']

    # Identify new portfolios (present in current but not in MST)
    mst_keys = mst_trends[dim_cols].drop_duplicates()
    curr_keys = curr_full[dim_cols].drop_duplicates()

    new_keys = pd.merge(curr_keys, mst_keys, on=dim_cols, how='left', indicator=True)
    new_keys = new_keys[new_keys['_merge'] == 'left_only'].drop(columns='_merge')

    if new_keys.empty:
        print("✅ No new portfolios found.")
        return mst_trends

    print(f"🆕 Found {len(new_keys)} new portfolios. Creating dummy projection entries...")

    # Attach dummy Year 0 data (copy from curr_full where available)
    new_portfolios = pd.merge(curr_full, new_keys, on=dim_cols, how='inner')
    new_portfolios['new_portfolio'] = 1

    # Assign projection and scenario combinations (replicates across all MST combos)
    scenarios = mst_trends['Scenario'].unique()
    projection_periods = mst_trends['projection_period'].unique()

    dummy_entries = []
    for scn in scenarios:
        for yr in projection_periods:
            temp = new_portfolios.copy()
            temp['Scenario'] = scn
            temp['projection_period'] = yr
            dummy_entries.append(temp)

    new_portfolios_expanded = pd.concat(dummy_entries, ignore_index=True)

    # For Y>0, set EAD/ECL same as Y0 or 0 depending on your logic
    new_portfolios_expanded.loc[
        new_portfolios_expanded['projection_period'] > 0,
        ['EAD_IFRS', 'EAD_IFRS_NDF', 'EAD_IFRS_DF', 'ECL', 'ECL_NDF', 'ECL_DF']
    ] = 0

    # Combine with MST trends
    combined = pd.concat([mst_trends, new_portfolios_expanded], ignore_index=True)

    print(f"✅ Added {len(new_portfolios_expanded)} dummy rows for new portfolios.")
    return combined
