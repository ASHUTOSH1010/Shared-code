I am not satisfied with format (not like what I shown you) and the coverage (not comprehensive and doesn't fully explain each part of code)

Understood. To match the style, detail, and comprehensive nature of the code book format from the example images you provided earlier, the new code book for the Stranded Asset Analysis (SAA) will be:

- Structured as a clear process workflow with numbered tasks/phases  
- Include explicit descriptions of each code block or logical section  
- List input files with their purpose  
- State key variables, flags, and their meanings with precision  
- Describe the step-by-step transformations and calculations in detail  
- Document expected output files and summaries  
- Use tables and bullet points for clarity and ease of reference  

This will require a thorough dissection of your provided code into distinct steps and mapping each to functional descriptions, flag logic, and file dependencies.

I will prepare this more refined and detailed code book in the exact style you showed, covering all significant parts of your SAA Python code.

Please allow me a moment to produce this detailed and formatted code book draft based on your Python script and previous code book.
Here is a comprehensive, structured, and clear code book for the Stranded Asset Analysis (SAA) physical climate risk stress testing code you provided. It follows the format and level of detail similar to the example code book screenshots you shared earlier.

***

# Stranded Asset Analysis (SAA) Code Book

## 1. Process Overview for SAA  
This process analyzes mortgage and property data relative to physical climate risks including flood, storm, sea level rise, and heat stress using portfolio-level exposure and property features. The aim is to identify potentially **stranded assets** exposed to adverse climate outcomes after considering mitigants such as flood defenses, property age, and type.

## 2. Input Files and Data Sources

| Input File                                   | Description                                                                                      |
|----------------------------------------------|------------------------------------------------------------------------------------------------|
| WRBQ424_RCP_SSP_retail_data.xlsx             | Retail mortgage portfolio data with climate risk exposure and scores by property/account        |
| Consolidated prop data.xlsx                   | Property level details: country code, account ID, property type, year of property construction   |
| Property_types.xlsx                           | Lookup containing `Grounded`, `Non-Grounded`, and `Others` property type classifications          |
| HK_year_type_final.xlsx                       | Hong Kong-specific property type and year data to update merged property details in that region |


## 3. Key Process Steps and Code Logic

### Task 1: Data Loading and Initial Cleaning  
- Load retail mortgage data and create a copy (for backup).  
- Rename columns to standardized names: `"base country"` → `"Country Code"`, `"address_id"` → `"Account Id"`.  
- Filter mortgage data to retain climate risk variables and account identifiers needed for analysis.  

### Task 2: Data Type Conversion and Account ID Cleaning  
- Apply `convert_to_numeric()` to convert key measure columns from strings to numbers after cleaning (removing non-numeric chars).  
- Define `clean_actid()` to standardize account IDs by:  
  - Removing prefixes like `"RTL-XX-"` or `"RTL-"`.  
  - Stripping suffixes after underscore `_`.  
  - Removing all non-digit characters.  
  - Special zero-stripping for Taiwan accounts.  
- Apply `clean_actid` row-wise to generate cleaned account ID column `account_id_cl`.

### Task 3: Reading and Cleaning Property Data  
- Load property data and convert property year to numeric.  
- Clean property types using regex cleaning logic in `clean_prop_type()`, normalizing strings, stripping unwanted characters, and spacing.  
- Create a cleaned property type column `PROPERTY_TYPE_cl`.  
- Remove duplicate properties by `(account_id_cl, Country Code)` keys to reduce redundancy.

### Task 4: Property Type Classification  
- Load property type classifications from `Property_types.xlsx` containing columns: `Grounded`, `Non-Grounded`, and `Others`.  
- Clean these classifications similarly and generate lists for each category that are used to flag property types downstream.

### Task 5: Merging Mortgage and Property Data  
- Merge filtered mortgage data with cleaned property data on `(account_id_cl, Country Code)`.  
- For Hong Kong (HK), update property age and type columns by merging with `HK_year_type_final.xlsx`.  
- Replace property info for HK rows accordingly.

### Task 6: Risk Mapping and Flag Creation  
- Map numeric sea level rise risk values (`sea_level_rise_rcp85y2100_value`) to descriptive categories: `No Hazard`, `Low`, `Medium`, `High`, `Extreme`.  
- Map river flood defended and undefended values to descriptive categories (`No Information`, `Low`, `Medium`, `High`, `Extreme`).  

### Task 7: Stranded Asset Criteria and Flags  

| Flag Name                           | Definition/Logic                                                                                     |
|-----------------------------------|-----------------------------------------------------------------------------------------------------|
| EXTREME_FLOOD_OR_STORM_wo_MITIGANTS | Flag=1 if flood or storm risk is `Extreme` before mitigation                                          |
| STRANDED_FLOOD_STORM_SEA_RISE_wo_MITIGANTS | Flag=1 if extreme sea level rise or extreme flood/storm risk before mitigation                         |
| FLOOD_DEFENSE_SOP_LTE20           | Flag=1 if flood defense SOP (Standard Operating Procedure) ≤ 20 (poor defense)                        |
| Distance to coast zone2           | Categorizes properties as `Stranded` if distance to coast ≤ 1 km else `Non-Stranded`                   |
| STRANDED_SEA_RISE_W_MITIGANTS     | Flag=1 if sea level rise risk is `Extreme` and property is within 1 km of coast after mitigation       |
| PROPERTY_AGE_lt_1970              | Flag=1 if property age is before 1970 or age data unusable (acts as mitigant for acute flood/storm risk)|
| STRANDED_PROPERTY_TYPE            | Flag=1 for grounded properties (villages, bungalows) or unrecognized types; else 0 for non-grounded    |
| STRANDED_FLOOD_STORM_W_MITIGANTS  | Flag=1 if extreme flood or storm risk persists after mitigation including flood defense and property age |
| STRANDED_FLOOD_STORM_W_MITIGANTS_incl_PropType | As above but including property type filter                                                         |
| STRANDED_FINAL_incl_PropType      | Final stranded asset flag combining flood, storm, sea level rise risks and mitigants                  |

### Task 8: Summary and Sensitivity Analysis  
- Aggregate outstanding USD exposure by country using pivot tables.  
- Conduct sensitivity analysis of stranded asset exposure relative to varying flood defense SOP thresholds (0, 20, 50, 100).  
- Conduct sensitivity analysis relative to distance to coast thresholds (100m, 250m, 500m, 750m, 1000m).  


## 4. Output Files and Data  
- Detailed property-level dataset with stranded flags and descriptive columns.  
- Pivot summary tables of outstanding exposure by country, showing stranded amounts under various mitigant thresholds.


## 5. Code Files and Scripts  
- This entire process is encapsulated in a single or notebook Python script managing input loading, cleaning, transformation, risk flagging, and output summaries.


***

This draft provides a stepwise clear description of each code part with detailed flag logic and file purpose to match your example code book style and thoroughness. Kindly confirm or specify if you want sections expanded with even more code-level detail or tabular breakdowns.

Citations:
[1] saa-code.pdf https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/78100584/c5deb127-668e-435e-b408-7c0975543dce/saa-code.pdf
