You've provided a new screenshot showing a table of contents, specifically Section 4, with subsections like "4.2.1 Processing BCRS File," "4.2.2 CEM PD Overlays for Corporates," etc., and then "4.3 Model Methodology (cont.)" with subsections "4.3.1 Model Specification," "4.3.2 Use of Approximations," etc..
This new screenshot clarifies the intended structure of the documentation's methodology section. My previous response integrated the Python script's explanation into 4.2 DQM Methodology and 4.1 DQM Input Data, and 4.4 DQM Output based on the content of the script and its relevance to the overall "Stranded Asset Analysis."
Now, with this new table of contents, it's clear that there's a more granular breakdown expected, particularly under "4.2 DQM Methodology" for processing data and then "4.3 Model Methodology (cont.)" for model specifics, approximations, and assumptions.
My Recommendation: A Hybrid Approach is Best.
Instead of just commentary or a direct replication of code, we should:
Introduce a new subsection within 4.2 specific to the SAA script's data processing. The current 4.2.1 Methodology for Estimating Stranded Assets is quite high-level. We can introduce a 4.2.1 SAA Script Data Processing and Feature Engineering or similar.
Integrate the core SAA logic (risk identification, mitigant application) into 4.2.2 Stranded Asset Identification Logic or expand 4.2.1 Methodology for Estimating Stranded Assets to include this detail. This is where the specific boolean flags and conditional statements from your script come in.
Use 4.3.1 Model Specification to talk about the overall stranded asset calculation (Loss = Value * Probability of Stranding, etc.) and refer to the script as its implementation.
Leverage 4.3.2 Use of Approximations and 4.3.4 Use of Expert Judgment for the rationales behind certain thresholds, the insurance benefits phase-out, and the property type proxies, explicitly mentioning how the script reflects these judgments.
For 4.2.1 Processing BCRS File (from the new TOC image), if the SAA script specifically processes the BCRS file, we can detail that there. If "BCRS File" is a general banking term not directly used by this specific SAA script, we might need to assume the SAA script receives pre-processed data or add a note. Based on the script, it loads WRBQ424_RCP_SSP_retail_data.xlsx and Consolidated_prop_data.xlsx which are the core inputs. We can describe how the script handles these.
Why a Hybrid Approach?
Clarity and Detail: It provides enough technical detail from the script without simply pasting code. It explains what the script does and why.
Adherence to Structure: It respects the hierarchical structure outlined in your new table of contents.
Readability: A narrative explanation of the code's logic is generally more digestible for a documentation reader than line-by-line code comments. We can highlight key functions, the logic of conditional statements, and how data transformations are applied.
Completeness: It links the practical implementation (the script) to the theoretical methodology.
Let's revise Section 4 again, incorporating the granular structure suggested by the new TOC, and re-distributing the script's explanation accordingly. I will create new subsections under 4.2 DQM Methodology and expand 4.3 Model Methodology (cont.) with relevant details from the script.
4. DQM INPUT DATA, MODEL METHODOLOGY & MODEL OUTPUT
This section describes the key elements of the input data, including data sources, time periods considered, data proxies, and data transformations. The data has been rigorously assessed to confirm its suitability and relevance for the overlay approach. Where applicable, the use of data proxies has been identified, justified, and thoroughly documented. Data transformation processes have been applied to Year-0 (actuals) BCRS data, and comprehensive data quality checks have been performed to ensure integrity.
4.1 DQM Input Data
The Stranded Asset Analysis relies on a diverse set of both internal and external data sources. The accuracy and reliability of the analysis are fundamentally dependent on the quality and consistency of this input data. While robust data acquisition and cleaning processes are in place, acknowledged data availability and usability challenges across various footprint markets are systematically managed, as detailed in Section 7.1.1. The Python script plays a crucial role in processing and preparing these inputs for the analysis.
Table 10 DQM Inputs
#
Input Data
Description
Source
Remarks on Data Quality, Data Proxy, Data Transformation and/or Expert Judgement
Time Period & Data Availability
Files
1
Internal Data
This category encompasses granular property-level information such as Property Age and Property Type, alongside essential mortgage details including loan amount, Loan-to-Value (LTV) ratios, outstanding balances, and precise geo-coordinates and Account IDs. These data points are foundational for identifying assets within the portfolio and for subsequent financial impact calculations.
Country Teams (for Property Age, Property Type) and WRB Mortgage Portfolio Data (Credit Risk Systems)
Data Quality: Rigorous sanity checks are performed to ensure the data is fit for use. A key challenge lies in the availability and usability of Property Age and Property Type data across specific markets (e.g., Korea, Taiwan, India), often leading to "not sourced" or "not usable" classifications, necessitating expert judgment. <br> Data Transformation: Raw property age and type data are cleaned and standardized using Python scripts, leveraging functions like clean_prop_type. The mortgage portfolio data, initially at a granular facility level, is processed and aggregated as needed for the analysis, involving "joining mortgage data with property details data". <br> Expert Judgment: Significant expert judgment is applied in addressing data limitations, guiding "best-effort" analysis in segments where complete data is unavailable.
Ongoing/As available (Property data); Quarterly/Monthly (Portfolio data)
Sourced Files: consolidated_prop_data.xlsx, property_types.xlsx, [Reference internal file paths for WRB Mortgage Portfolio Data if applicable]
2
External Climate Risk Data
This dataset provides granular, property-level climate risk assessments from specialized external vendors. It includes critical variables such as Country Code, Account Id, flood_risk_score_desc (e.g., "Extreme", "Low"), storm_risk_score_desc, quantitative sea_level_rise_rcp85y2100_value, flood_defense_sop (a score for flood defense effectiveness), distance_to_coast, and the outstanding_usd balance for each property. These external data points are fundamental to identifying and quantifying the portfolio's exposure to physical climate risks.
Data Strategy Team (External Vendor data)
Data Quality: Data acquired from external vendors undergoes a rigorous pre-processing phase by the dedicated Data Strategy team to ensure consistency and usability. <br> Data Transformation: Relevant numerical columns (e.g., heat_stress_index, sea_level_rise_rcp85y2100_value, flood_defense_sop, distance_to_coast, outstanding_usd) are converted to their appropriate numeric types using a Python function (convert_to_numeric). Account IDs are standardized and cleaned using a specific Python function (clean_actid) to facilitate accurate matching. A crucial step involves geo-spatial joining to precisely link property locations with their corresponding climate risk scores and values.
Annually/As updated
Sourced Files: WRBQ424_RCP_SSP_retail_data.xlsx
3
Climate Scenario Data
This input comprises the widely recognized Representative Concentration Pathways (RCPs) and Shared Socioeconomic Pathways (SSPs), which serve as the foundation for long-term climate projections, specifically up to 2050. These scenarios describe plausible future climate and socioeconomic conditions.
IPCC / IEA
Data Quality: These data sources represent established scientific projections from authoritative bodies. <br> Data Proxy: For the purpose of this stress test, the RCP 8.5 pathway is utilized for chronic risk exposures to 2050. This choice reflects a conservative "worst-case" scenario, aligning with the objectives of a robust stress test. <br> Expert Judgment: A high degree of expert judgment is involved in selecting the most appropriate combination of RCP and SSP scenarios to define the relevant climate pathways for the analysis.
As published by IPCC/IEA
NA
4
Insurance Data
This category includes information regarding current insurance coverage status and any mandatory insurance requirements applicable to the mortgage portfolio. This data is leveraged for assessing short-term mitigation capabilities against climate risks.
Internal Insurance Policy Data
Data Quality: The completeness and accuracy of internal insurance policy data are verified. <br> Data Transformation: A specific logic is applied to recognize the benefits of insurance only until the year 2030, and exclusively in markets where insurance is explicitly mandatory (Hong Kong, China, UAE). This transformation reflects a prudent approach given long-term uncertainties. <br> Expert Judgment: There is a high level of expert judgment involved in the assumption that no insurance benefits will be applicable beyond 2031. This is driven by significant uncertainties regarding the future evolution of insurance premiums and the overall availability of coverage in the face of increasingly severe climate events, and the potential for a flood insurance market failure.
Annually/As updated
NA
5
Reference Mapping Files
These files are crucial for various lookup and categorization purposes within the analysis. Examples include mappings from Industry classifications to ISIC codes, and Country codes to broader Regional groupings, facilitating consistent data aggregation and reporting.
Climate Data Strategy (DS) Team; Static files (Internal)
Data Quality: Routine sanity checks are performed on these static reference files to ensure their accuracy and consistency.
NA (Annual for updates / One-time for initial setup)
Sourced Files: ISIC Mapping Clean.msg, ISIC_Industry_limit.csv, Country_Region_Map.csv

4.2 DQM Methodology
The methodology for the Stranded Asset Analysis (SAA) is designed to systematically identify and quantify potential losses within the mortgage portfolio resulting from the physical impacts of climate change. This involves assessing exposure to extreme physical risks and accounting for available mitigants, ultimately translating into management adjustments for Expected Credit Losses (ECL) or Loan Impairment (LI). The Python script provided implements the detailed logical steps of this methodology.
4.2.1 SAA Script Data Processing and Feature Engineering The Python script initiates the analytical process by loading and transforming raw input data into a structured format suitable for the Stranded Asset Analysis.
Initial Data Loading and Renaming: The script reads the primary climate risk dataset from 'WRBQ424_RCP_SSP_retail_data.xlsx' into a pandas DataFrame named mort_data. It then immediately renames key columns for consistency and ease of use, such as 'base country' to 'Country Code' and 'address_id' to 'Account Id'. A copy of this data (filter_data) is created for subsequent filtering and analysis.
Data Cleaning Functions:
convert_to_numeric(): This custom function is crucial for data integrity. It iterates through a predefined list of columns (e.g., heat_stress_index_rcp85y2050_value, sea_level_rise_rcp85y2100_value, flood_defense_sop, outstanding_usd) and attempts to convert their values to a numeric (float) type. It includes robust error handling to set values that cannot be converted to np.nan (Not a Number), ensuring that non-numeric entries do not halt calculations. This function also handles stripping whitespace and converting to numerical format.
clean_actid(): This function standardizes Account Id values. It converts the IDs to uppercase, removes a specific prefix ('RTL-'), and eliminates leading zeros. This standardization is vital for accurate data merging and unique identification of properties across various datasets.
clean_prop_type(): This function processes the Property Type column by stripping whitespace and converting text to lowercase. This helps in standardizing property type entries before categorization.
Property Data Integration: Property age and type data are loaded from 'Consolidated_prop_data.xlsx' and, for Hong Kong specifically, from 'HK year_type_final.xlsx'. These datasets are then merged with the main filter_data DataFrame using cleaned 'Account Id' and 'Country Code' as keys, linking property attributes to climate risk data.
Property Type Categorization: A separate lookup file, 'Property_types.xlsx', is loaded and used to categorize cleaned property types into 'Grounded' (e.g., standalone houses, villas which might be more exposed to ground-level flooding) and 'Non-Grounded' (e.g., apartments, condominiums, expected to be on higher floors) categories. This categorization is critical for applying property-type-specific mitigant criteria.
Hazard Value Description Mapping: The script maps numerical climate hazard values (e.g., sea_level_rise_rcp85y2100_value, riverflood_current_defended_value, riverflood_current_undefended_value) to descriptive categories such as 'No Hazard', 'Low', 'Medium', 'High', and 'Extreme'. This facilitates the boolean logic used for identifying "Extreme" risk exposures.
4.2.2 Stranded Asset Identification Logic This section details the core methodology for identifying stranded assets based on extreme climate risks and the presence (or absence) of mitigants, as implemented by the Python script.
Initial Risk Exposure Flags (Without Mitigants):
EXTREME_FLOOD_OR_STORM_wo_MITIGANTS: A boolean flag is created to identify properties exposed to 'Extreme' acute risks (either flood or storm) based on the descriptive hazard values derived in the data processing stage.
STRANDED_FLOOD_STORM_SEA_RISE_wo_MITIGANTS: This flag extends the acute risk identification to include properties exposed to 'Extreme' sea level rise risk (sea_level_rise_rcp85y2100_value_Desc == 'Extreme'), thus identifying all initial potential stranded assets before mitigants are considered.
Mitigant Application Logic: The script then applies specific criteria for various mitigants:
Flood Defense SOP: FLOOD_DEFENSE_SOP_LTE20 flags properties where the flood_defense_sop (Standard of Protection) is less than or equal to 20, indicating insufficient flood defense.
Distance to Coast: Distance to coast zone2 flags properties as 'Stranded' if their distance_to_coast is less than or equal to 1000 meters (1 km), identifying chronic sea level rise vulnerability.
Property Age: PROPERTY_AGE_lt_1970 identifies older properties (YEAR_OF_PROPERTY < 1970) as more vulnerable, or if YEAR_OF_PROPERTY is unavailable for certain countries, it defaults to a vulnerable classification.
Property Type: STRANDED_PROPERTY_TYPE identifies properties with a PROPERTY_TYPE_cl that are categorized as 'Grounded' (more susceptible to ground-level flooding) or if the property type is unidentifiable, flagging them as more exposed.
Combined Stranded Asset Flags (With Mitigants):
STRANDED_SEA_RISE_W_MITIGANTS: Properties are identified as stranded due to sea level rise if they are in an 'Extreme' sea level rise zone AND fall within the 'Stranded' distance to coast zone (i.e., \\le 1 \\text{km}).
STRANDED_FLOOD_STORM_W_MITIGANTS: For acute risks, properties are flagged if they are in an 'Extreme' flood or storm risk category AND (FLOOD_DEFENSE_SOP_LTE20 is True OR PROPERTY_AGE_lt_1970 is True). This means they are exposed to extreme acute risk and have poor flood defense or are older properties.
STRANDED_FLOOD_STORM_W_MITIGANTS_incl_PropType: This refines the acute risk assessment by also incorporating the STRANDED_PROPERTY_TYPE flag. Properties are flagged if they are in an 'Extreme' flood or storm risk category AND (FLOOD_DEFENSE_SOP_LTE20 is True OR PROPERTY_AGE_lt_1970 is True OR STRANDED_PROPERTY_TYPE is True).
STRANDED_FINAL_incl_PropType: This is the ultimate flag, combining all identified stranded assets. A property is considered finally stranded if STRANDED_SEA_RISE_W_MITIGANTS is True OR STRANDED_FLOOD_STORM_W_MITIGANTS_incl_PropType is True.
Table 2: Mitigants Considered for Different Risk Types.
Risk
Mitigant Variable
Mitigant Criteria
Stranded Asset Criteria*
Acute Risk (Flood/Storm)
Flood Defense SOP
High Flood Defense (SOP > 20)
Poor Flood Defense (SOP <= 20)


Age of Property
New Properties (Constructed after 1970)
Old Properties (Constructed prior to 1970)


Type of Property
Properties expected to be on higher floor like Condominiums, Apartments etc.
Properties expected to be on lower floors like Standalone Buildings, Village Type Houses, Villas, Bungalows, Semi Detached properties.


Insurance Benefits
100% insurance benefits considered for markets where insurance is mandatory
Until 2030, markets where insurance is mandatory are considered for stranded assets estimation. From 2031, no insurance benefits are considered.
Chronic Risk (Sea Level Rise)
Distance to Coast
Far from the coast (distance > 1km)
Far from the coast (distance <= 1km)

4.2.3 Phasing of Stranded Assets over the Projection Horizon The manifestation of climate-related losses, particularly from physical risks, is expected to intensify over time. Based on expert panel discussions, it was agreed that the more material losses from stranded assets are likely to occur in the outer years of the projection horizon. To reflect this temporal progression, the distribution of management adjustments for stranded assets is determined by the cumulative rate of change in Global Mean Temperatures (GMT) profile.
For the "Current Policies" Scenario: In line with the scenario narrative, which anticipates a gradual increase in the intensity and frequency of physical risk events, management adjustments for both acute and chronic risks are applied starting from Year 2041.
For the "Tail Physical Risk" Scenario: This scenario implies more immediate and extreme shocks. Therefore, management adjustments for acute risks are applied from 2024. However, for chronic risks, the adjustments are still phased in from 2041. This distinction acknowledges that chronic risks, such as sea level rise, inherently manifest as a gradual accumulation over an extended period, requiring many years to produce significant effects, even under a tail risk scenario.
4.2.4 Treatment of Insurance in Stranded Asset Calculations (Post-2030) While various physical mitigants (like flood defense SOP, property age/type, and distance to coast) are applied based on data availability, the consideration of insurance benefits in the Stranded Asset Analysis is time-bound and market-specific. Insurance benefits are recognized only until the year 2030, and exclusively in markets where property insurance is mandatory (Hong Kong, China, and UAE).
Rationale for Discontinuing Insurance Benefits from 2031: Beyond 2031, the analysis prudently assumes that no insurance benefits will be applicable for stranded assets. This critical assumption is based on several key considerations, supported by internal discussions and external research:
Uncertainty in Future Premiums and Availability: There is significant uncertainty regarding how insurance premiums will evolve in response to escalating climate risks and whether coverage will remain available or affordable in highly exposed areas.
Anticipated increases in flood insurance premiums in flood-prone areas are expected to lead to a decrease in property values.
Disruption of "Principles of Insurability": For areas highly prone to recurrent severe events (e.g., floods), the fundamental principles of insurability—which rely on quantifiable, diversified, and randomly occurring risks—may be disrupted. Catastrophe risks, particularly flood risks, often do not meet these criteri
