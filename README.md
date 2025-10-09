import pandas as pd

# --- 1️⃣ Load your data ---
df = pd.read_excel("stress_data.xlsx", sheet_name="Sheet1")

# --- 2️⃣ Define dimension columns ---
dimension_cols = [
    "Scenario", "APPROACH", "ENTITY", "COUNTRY", "PRODUCT", "FIN_BUSINESS_UNIT"
]

# --- 3️⃣ Projection periods ---
years = ["Y0", "Y1", "Y6", "Y11", "Y16", "Y21", "Y26"]

# --- 4️⃣ Melt each measure into long format ---

# EAD IFRS DF
ead_ifrs = df.melt(
    id_vars=dimension_cols,
    value_vars=[f"EAD IFRS DF {y}" for y in years],
    var_name="Metric",
    value_name="EAD_IFRS_DF"
)
ead_ifrs["YEAR"] = ead_ifrs["Metric"].str.extract(r"Y(\d+)")
ead_ifrs.drop(columns="Metric", inplace=True)

# ECL NDF
ecl_ndf = df.melt(
    id_vars=dimension_cols,
    value_vars=[f"ECL NDF Y{y[1:]}" for y in years],
    var_name="Metric",
    value_name="ECL_NDF"
)
ecl_ndf["YEAR"] = ecl_ndf["Metric"].str.extract(r"Y(\d+)")
ecl_ndf.drop(columns="Metric", inplace=True)

# ECL DF
ecl_df = df.melt(
    id_vars=dimension_cols,
    value_vars=[f"ECL DF Y{y[1:]}" for y in years],
    var_name="Metric",
    value_name="ECL_DF"
)
ecl_df["YEAR"] = ecl_df["Metric"].str.extract(r"Y(\d+)")
ecl_df.drop(columns="Metric", inplace=True)

# ECL TOTAL (already present)
ecl_total = df.melt(
    id_vars=dimension_cols,
    value_vars=[f"ECL {y}" for y in years],
    var_name="Metric",
    value_name="ECL_TOTAL"
)
ecl_total["YEAR"] = ecl_total["Metric"].str.extract(r"Y(\d+)")
ecl_total.drop(columns="Metric", inplace=True)

# --- 5️⃣ Merge all measures together ---
merged = (
    ead_ifrs
    .merge(ecl_ndf, on=dimension_cols + ["YEAR"], how="outer")
    .merge(ecl_df, on=dimension_cols + ["YEAR"], how="outer")
    .merge(ecl_total, on=dimension_cols + ["YEAR"], how="outer")
)

# --- 6️⃣ Final clean-up ---
final_cols = (
    dimension_cols
    + ["YEAR", "EAD_IFRS_DF", "ECL_NDF", "ECL_DF", "ECL_TOTAL"]
)
final_df = merged[final_cols].sort_values(by=dimension_cols + ["YEAR"])

# --- 7️⃣ Save reshaped output ---
final_df.to_excel("reshaped_stress_data.xlsx", index=False)
print("✅ Reshaping complete — saved as 'reshaped_stress_data.xlsx'")
