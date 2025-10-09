import pandas as pd

# --- 1️⃣ Load your data ---
# (Assuming your Excel file is named 'stress_data.xlsx' and sheet is 'Sheet1')
df = pd.read_excel("stress_data.xlsx", sheet_name="Sheet1")

# --- 2️⃣ Define your dimension columns ---
dimension_cols = [
    "Scenario", "APPROACH", "ENTITY", "COUNTRY", "PRODUCT", "FIN_BUSINESS_UNIT"
]

# --- 3️⃣ Identify projection years ---
years = ["Y0", "Y1", "Y6", "Y11", "Y16", "Y21", "Y26"]

# --- 4️⃣ Prepare long-format frames for each measure type ---
# Melt (unpivot) the data so that projection years become a single "YEAR" column.

ead_ifrs = df.melt(
    id_vars=dimension_cols,
    value_vars=[f"EAD IFRS DF {y}" for y in years],
    var_name="Metric",
    value_name="EAD_IFRS_DF"
)
ead_ifrs["YEAR"] = ead_ifrs["Metric"].str.extract(r"Y(\d+)")
ead_ifrs.drop(columns="Metric", inplace=True)

ecl_ndf = df.melt(
    id_vars=dimension_cols,
    value_vars=[f"ECL NDF Y{y[1:]}" for y in years],
    var_name="Metric",
    value_name="ECL_NDF"
)
ecl_ndf["YEAR"] = ecl_ndf["Metric"].str.extract(r"Y(\d+)")
ecl_ndf.drop(columns="Metric", inplace=True)

ecl_df = df.melt(
    id_vars=dimension_cols,
    value_vars=[f"ECL DF Y{y[1:]}" for y in years],
    var_name="Metric",
    value_name="ECL_DF"
)
ecl_df["YEAR"] = ecl_df["Metric"].str.extract(r"Y(\d+)")
ecl_df.drop(columns="Metric", inplace=True)

# --- 5️⃣ Merge all measures together ---
# Merging on dimensions + YEAR gives one row per scenario & year
merged = (
    ead_ifrs
    .merge(ecl_ndf, on=dimension_cols + ["YEAR"], how="outer")
    .merge(ecl_df, on=dimension_cols + ["YEAR"], how="outer")
)

# --- 6️⃣ Compute total ECL (ECL_NDF + ECL_DF) ---
merged["ECL_TOTAL"] = merged["ECL_NDF"].fillna(0) + merged["ECL_DF"].fillna(0)

# --- 7️⃣ Clean up and reorder columns ---
final_cols = (
    dimension_cols
    + ["YEAR", "EAD_IFRS_DF", "ECL_NDF", "ECL_DF", "ECL_TOTAL"]
)
final_df = merged[final_cols].sort_values(by=dimension_cols + ["YEAR"])

# --- 8️⃣ Save reshaped data to Excel or CSV ---
final_df.to_excel("reshaped_stress_data.xlsx", index=False)
# or
# final_df.to_csv("reshaped_stress_data.csv", index=False)

print("✅ Reshaping complete! Output saved as 'reshaped_stress_data.xlsx'")
