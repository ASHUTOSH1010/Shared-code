import re

base_year = 2024
rename_dict = {}

# Define the sequence of actual projection years (custom mapping)
projection_years = list(range(2024, 2031)) + [2035, 2040, 2045, 2050]

# Create a dictionary mapping from Yi_0, Yi_1 ... to actual projection years
yi_to_year = {f"Yi_{i}": year for i, year in enumerate(projection_years)}

# Build rename map
for col in df.columns:
    match = re.search(r'Yi_\d+', col)
    if match:
        yi_label = match.group(0)
        if yi_label in yi_to_year:
            new_col = col.replace(yi_label, str(yi_to_year[yi_label]))
            rename_dict[col] = new_col

# Apply renaming
df = df.rename(columns=rename_dict)


keep_cols = [
    'Scenario', 'approach', 'entity', 'country', 'product', 'fin_business_unit',
    *[c for c in df.columns if any(x in c for x in ['EAD_IFRS', 'EAD_IFRS_NDF', 'EAD_IFRS_DF', 'ECL', 'Cumm_LI'])],
    'fr_unit', 'Entity_Product'
]

df = df[[col for col in keep_cols if col in df.columns]]
