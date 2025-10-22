def fn_pivot_results(df, actuals_year):
    """
    Final Pivoting Function for WRB Scenario Analysis Output
    --------------------------------------------------------
    Converts long-format projection data into wide format (year-wise columns)
    for dashboard or Tableau consumption.
    """

    df1 = df.copy()

    # Keep only relevant projection years based on current actuals year
    if actuals_year == 2024:
        df1 = df1[df1['projection_period'] <= 26]
    elif actuals_year == 2025:
        df1 = df1[df1['projection_period'] <= 25]

    # Pivot table by scenario, portfolio dimensions, and projection year
    dim_cols = ['Scenario', 'approach', 'entity', 'country', 'product', 'fin_business_unit']
    value_cols = ['EAD_IFRS', 'EAD_IFRS_NDF', 'EAD_IFRS_DF', 'ECL', 'ECL_NDF', 'ECL_DF', 'Cumm_LI']

    pivoted = (
        df1
        .pivot_table(index=dim_cols, columns='projection_period', values=value_cols)
        .reset_index()
    )

    # Flatten MultiIndex columns
    pivoted.columns = ['_'.join([str(c) for c in col if c]).strip('_') for col in pivoted.columns.values]

    # Create projection year mapping (projection period → calendar year)
    proj_year_map = {i: actuals_year + i for i in range(df1['projection_period'].max() + 1)}

    # Rename columns: e.g., EAD_IFRS_1 → EAD_IFRS_2025
    new_cols = {}
    for col in pivoted.columns:
        for period, year in proj_year_map.items():
            if col.endswith(f"_{period}"):
                new_cols[col] = col.replace(f"_{period}", f"_{year}")
    pivoted.rename(columns=new_cols, inplace=True)

    # Ensure column order
    fixed_cols = ['Scenario', 'approach', 'entity', 'country', 'product', 'fin_business_unit']
    year_cols = sorted([c for c in pivoted.columns if any(str(y) in c for y in proj_year_map.values())])
    pivoted = pivoted[fixed_cols + year_cols]

    print(f"Pivoting complete for actuals_year = {actuals_year}")
    print(f"Output shape: {pivoted.shape}")

    return pivoted
