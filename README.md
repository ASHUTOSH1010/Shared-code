# Suppose df is your earlier dataframe with Yi_0 … Yi_26 columns

import re

# Define base year
base_year = 2024

# Create a rename mapping
rename_dict = {}
for col in df.columns:
    match = re.search(r'_Yi_(\d+)', col)
    if match:
        year = base_year + int(match.group(1))
        new_col = re.sub(r'_Yi_\d+', f'_{year}', col)
        rename_dict[col] = new_col

# Apply renaming
df = df.rename(columns=rename_dict)

# Now select only the final columns you want (based on your new image)
keep_cols = [
    'Scenario', 'approach', 'entity', 'country', 'product', 'fin_business_unit',
    # Example sets
    *[c for c in df.columns if 'EAD_IFRS' in c],
    *[c for c in df.columns if 'EAD_IFRS_NDF' in c],
    *[c for c in df.columns if 'EAD_IFRS_DF' in c],
    *[c for c in df.columns if 'ECL' in c],
    *[c for c in df.columns if 'Cumm_LI' in c],
    'fr_unit', 'Entity_Product'
]

df = df[[col for col in keep_cols if col in df.columns]]
