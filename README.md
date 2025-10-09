import pandas as pd
import re

# --- 1️⃣ Read and clean column names ---
df = pd.read_excel("stress_data.xlsx", sheet_name="Sheet1")
df.columns = df.columns.str.strip()  # remove extra spaces

dimension_cols = [
    "Scenario", "APPROACH", "ENTITY", "COUNTRY", "PRODUCT", "FIN_BUSINESS_UNIT"
]

# --- 2️⃣ Extract all projection years dynamically ---
years = sorted(set(re.findall(r"Y\d+", " ".join(df.columns))))

# --- 3️⃣ Define a helper function to melt each metric safely ---
def melt_metric(df, prefix, new_col):
    cols = [c for c in df.columns if c.startswith(prefix)]
    melted = df.melt(id_vars=dimension_cols, value_vars=cols,
                     var_name="Metric", value_name=new_col)
    melted["YEAR"] = melted["Metric"].str.extract(r"(Y\d+)")
    melted.drop(columns="Metric", inplace=True)
    return melted

# --- 4️⃣ Melt each measure ---
ead_ifrs = melt_metric(df, "EAD IFRS DF", "EAD_IFRS_DF")
ecl_ndf = melt_metric(df, "ECL NDF", "ECL_NDF")
ecl_df = melt_metric(df, "ECL DF", "ECL_DF")
ecl_total = melt_metric(df, "ECL ", "ECL_TOTAL")  # note space to avoid ECL DF/NDF confusion

# --- 5️⃣ Merge safely using inner joins ---
merged = (
    ead_ifrs
    .merge(ecl_ndf, on=dimension_cols + ["YEAR"], how="inner")
    .merge(ecl_df, on=dimension_cols + ["YEAR"], how="inner")
    .merge(ecl_total, on=dimension_cols + ["YEAR"], how="inner")
)

# --- 6️⃣ Drop duplicates just in case ---
merged = merged.drop_duplicates(subset=dimension_cols + ["YEAR"])

# --- 7️⃣ Sort and export ---
final_cols = dimension_cols + ["YEAR", "EAD_IFRS_DF", "ECL_NDF", "ECL_DF", "ECL_TOTAL"]
final_df = merged[final_cols].sort_values(by=dimension_cols + ["YEAR"])

final_df.to_excel("reshaped_stress_data_clean.xlsx", index=False)
print("✅ Clean reshaping done — duplicates removed, saved as 'reshaped_stress_data_clean.xlsx'")
