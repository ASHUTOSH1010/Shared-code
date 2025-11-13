# --- 0) Setup
strict_keys   = ['approach','entity','country','product','fin_business_unit','projection_period']
fallback_keys = ['entity','country','product','projection_period']

# Only bring non-key columns from the right side to avoid dupes
mst_non_strict = [c for c in mst_trends.columns if c not in strict_keys]
mst_non_fallback = [c for c in mst_trends.columns if c not in fallback_keys]

# --- 1) Strict merge
strict_merged = (
    WRB_Curr_Q
    .merge(
        mst_trends[strict_keys + mst_non_strict],
        on=strict_keys,
        how='left',
        indicator=True
    )
)
strict_merged['match_level'] = np.where(strict_merged['_merge']=='both','strict','left_only')

# Rows that failed the strict match
to_retry = WRB_Curr_Q.loc[strict_merged['_merge'].eq('left_only'), :]

# --- 2) Fallback merge (looser keys)
fallback_merged = (
    to_retry
    .merge(
        mst_trends[fallback_keys + mst_non_fallback],
        on=fallback_keys,
        how='left',
        indicator=True
    )
)
fallback_merged['match_level'] = np.where(fallback_merged['_merge']=='both','fallback','left_only')

# --- 3) Vertically append (strict matches + fallback results)
final_cols = list(WRB_Curr_Q.columns) + list(mst_non_strict)  # expected RHS cols from strict path
# Make both frames line up (missing columns will be added as NaN)
strict_out   = strict_merged[strict_merged['_merge'].eq('both')].drop(columns=['_merge'])
strict_out   = strict_out.reindex(columns=final_cols + ['match_level'])

fallback_out = fallback_merged.drop(columns=['_merge'])
fallback_out = fallback_out.reindex(columns=final_cols + ['match_level'])

WRB_Merged_2pass = pd.concat([strict_out, fallback_out], ignore_index=True)

# --- 4) Quick diagnostics
print("Strict merge:", strict_merged['_merge'].value_counts().to_dict())
print("Fallback merge:", fallback_merged['_merge'].value_counts().to_dict())
print("Final shape:", WRB_Merged_2pass.shape)
print(WRB_Merged_2pass['match_level'].value_counts(dropna=False).to_dict())
