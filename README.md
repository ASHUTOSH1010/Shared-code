You are absolutely right to catch that! My apologies for the inconsistency. The sub-heading "2.1 Methodology for estimating Stranded Assets" and its subsequent "2.1.4 Mitigants" and "2.4 Phasing of Stranded Assets over the projection horizon" were directly copied from the internal headings within the images you provided.
While these headings are internal to the document snippets, they do not align with the overall section numbering (Section 4, subsection 4.2).
I will correct this to ensure the numbering is consistent with Section 4, specifically under 4.2 DQM Methodology.
Here is the revised Section 4 again, with the correct numbering for the methodology sub-sections:
4. DQM INPUT DATA, MODEL METHODOLOGY & MODEL OUTPUT
This section describes the key elements of the input data including the data sources, time-period considered for the data, data proxy, and data transformation among others. The data has been assessed to be suitable and relevant for use in the overlay approach. The use of data proxies has been identified, justified, and documented. Data Transformation has been done on Year-0 (actuals) BCRS data. Where applicable, data quality checks have been performed.
4.1 DQM Input Data
The Stranded Asset Analysis relies on a combination of internal and external data sources. The quality and consistency of this input data are crucial for the accuracy and reliability of the analysis. Data availability and usability challenges across footprint markets are acknowledged and managed (see Section 7.1.1).
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
Contains information about Property Age and Property Type, along with core mortgage details (e.g., loan amount, LTV, outstanding balances, geo-coordinates, Account ID).
Country Teams (for Property Age, Property Type) and WRB Mortgage Portfolio Data (Credit Risk Systems)
Data Quality: Sanity checks have been performed to ensure the data is usable before it is consumed. Data availability and usability challenges exist for Property Age and Property Type across certain markets (e.g., Korea, Taiwan, India), leading to "not sourced" or "not usable" classifications. Data Transformation: Property Age and Type are cleaned and mapped using Python scripts (e.g., clean_prop_type function). Mortgage portfolio data is processed and aggregated to the required level for analysis (e.g., "joining mortgage data with property details data"). Expert Judgment is high for handling data limitations and determining "best-effort" analysis in segments with data gaps.
Ongoing/As available (Property data); Quarterly/Monthly (Portfolio data)
Sourced Files: consolidated_prop_data.xlsx, property_types.xlsx, [Reference internal file paths for WRB Mortgage Portfolio Data if applicable]
2
External Climate Risk Data
Contains granular property-level climate risk scores and values from external vendors. These include: Country Code, Account Id, flood_risk_score_desc, storm_risk_score_desc, sea_level_rise_rcp85y2100_value, flood_defense_sop, distance_to_coast, and outstanding_usd. This forms the basis for climate risk exposure assessment.
Data Strategy Team (External Vendor data)
Data Quality: Data received from external vendors undergoes pre-processing by the Data Strategy team. Data Transformation: Numeric conversion is applied to relevant columns (e.g., heat_stress_index, sea_level_rise_rcp85y2100_value, flood_defense_sop, distance_to_coast, outstanding_usd) using a Python function (convert_to_numeric). Account IDs are cleaned using a Python function (clean_actid). Geo-spatial joining is performed to link property locations to risk scores and values.
Annually/As updated
Sourced Files: WRBQ424_RCP_SSP_retail_data.xlsx
3
Climate Scenario Data
Provides Representative Concentration Pathways (RCPs) and Shared Socioeconomic Pathways (SSPs) for long-term climate projections up to 2050.
IPCC / IEA
Data Quality: These are internationally recognized scientific projections. Data Proxy: RCP 8.5 pathway is used for exposures to 2050 for chronic risks, due to its conservative nature. Expert Judgment: High in selecting the appropriate scenario combination for the analysis.
As published by IPCC/IEA
NA
4
Insurance Data
Information on current insurance coverage status and mandatory requirements. Used for short-term mitigation assessment.
Internal Insurance Policy Data
Data Quality: Verified for completeness. Data Transformation: Logic applied to recognize insurance benefits only until 2030 in markets where insurance is mandatory (HK, CN, AE). Expert Judgment: High for the assumption of no insurance benefits beyond 2030 due to uncertainty around premiums and availability in extreme events.
Annually/As updated
NA
5
Reference Mapping Files
Used for various lookups and categorizations, such as Industry to ISIC code mapping and Country to Region mapping.
Climate Data Strategy (DS) Team; Static files (Internal)
Data Quality: Sanity checks are performed.
NA (Annual for updates / One-time for initial setup)
Sourced Files: ISIC Mapping Clean.msg, ISIC_Industry_limit.csv, Country_Region_Map.csv

4.2 DQM Methodology
4.2.1 Methodology for estimating Stranded Assets [based on 1000082310.jpg] Stranded assets are identified based on exposures under "Extreme" risk category of different risk types (as per RCP 8.5 pathway as of 2050 for Chronic Risks, and current acute risks). The analysis is based on the concentration of exposures in "Extreme" Flood Risk, Storm Risk, and Sea level rise. Heat Stress and Precipitation Stress are considered most critical for the group; however, only Flood Risk, Storm Risk, and Sea Level Rise risk are considered to determine stranded assets. Given its nature, heat stress can be used for transition risk quantification in the future, rather than for stranded assets. Precipitation stress is not considered for estimating stranded assets, as its impact is indirectly captured by flood and storm risks already.
Only those mortgage assets that are exposed to "Extreme" Acute Risks (Flood or Storm) or Chronic Risks (sea level rise) and don't meet the mitigants criteria are identified as stranded assets.
4.2.2 Mitigants [based on 1000082313.jpg] Different Mitigants are considered for different risk types. For properties exposed to extreme acute risks (flood or storm), three mitigants are considered – flood defence capability, age of property, and type of property. Similarly, for properties exposed to extreme chronic risks (sea level rise), distance to coast is considered as a mitigant.
The idea was to use floor of the property to identify stranded assets. However, due to unavailability of the data capturing the floor of the property, "Property Type" is chosen as an alternative.
Table 2: Mitigants considered for different risk types.
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

4.2.3 Phasing of Stranded Assets over the projection horizon: [based on 1000082314.jpg] Based on the feedback received during expert panel discussions, it was agreed that more material losses may materialize in the outer years. Accordingly, an approach based on cumulative rate of change in Global Mean Temperatures ('GMT') profile is adopted for distributing the management adjustments over the overlays horizon.
For current policies scenario, the management adjustments for stranded assets due to both acute risks and chronic risks are applied from Year 2041, in line with the scenario narrative, where we expect the intensity and frequency of the physical risk events to materialize in the outer years. For Tail Physical Risk scenario, management adjustments for stranded assets due to acute risks are applied from 2024, while those due to chronic risks are applied from 2041. While the tail risk narrative poses extreme shocks in the immediate short term, chronic risks typically manifest as a gradual accumulation over an extended period, often requiring years to produce any significant effects. Consequently, these chronic risks are projected to be applicable only from the year 2041.
4.2.4 Why Insurance is not considered for Stranded Assets from 2031: [based on 1000082317.jpg] While acute risk related mitigants like flood defense SOP, property age, property type and chronic risk related mitigants like distance to coast are applied based on availability and usability of data, Insurance benefits are recognized only until the year 2030 in the markets where insurance is mandatory (HK, CN, AE). Beyond 2031, it is assumed that no insurance benefits will be applicable. Consequently, the consideration of insurance benefits is limited to the Tail Physical Risk scenario only, and does not apply to the Current Policies scenario, as stranded assets are projected to emerge only after 2041 in Current Policies scenario. This approach is adopted following the recommendations from the STF members, who sought to take the benefits of insurance during the initial years based on the existing insurance coverage. It is assumed that 100% of the losses attributable to stranded assets will be covered by insurance until 2030. The insurance benefit of this consideration is estimated to be approximately USD30m. Current coverage varies across markets, with some markets covering Flood, Storm Risks under mandatory insurance cover, while others cover as an add-on. From 2031, Insurance benefits are not considered for Stranded Assets because of the uncertainty around how the premiums and availability of insurance will evolve. Uncertainty around the availability of insurance in most flood-prone areas, with flood risk potentially disrupting the "Principles of Insurability" and the likely flood insurance market failure are among the reasons for not considering Insurance impact. Based on research papers, articles and guidance from varied sources it was noted that availability of the flood insurance is going to be a major concern, especially in the context of likely flood insurance market failure. Even when available, the premium of such insurance policies is expected to be so high that it impacts the willingness to pay of the homeowners and dissuade them from opting for the cover.
4.3 Model Methodology (cont.)
(This subsection would typically include further details on model specification, use of approximations, assumptions, limitations, and use of expert judgment. Some of this information is implicitly covered in the DQM Assessment reasoning and the methodology description above, but if there are dedicated sub-sections for these in your full documentation, they should be placed here.)
4.4 DQM Output
The primary output of the Stranded Asset Analysis is the quantification of potential losses due to physical climate risks, which translates into a management adjustment to Expected Credit Losses (ECL) / Loan Impairment (LI). This output is crucial for informing climate risk provisioning and capital adequacy discussions, such as the ICAAP capital add-on.
The analysis provides a breakdown of stranded assets by country and risk type (Acute/Chronic), demonstrating the financial impact (e.g., USD 2.7bn for MST 2025).
4.5 DQM Assessment
The Stranded Asset Analysis (SAA) is a critical tool for quantifying climate-related financial risk and informing management adjustments. Its assessment under the DQM framework reflects its materiality, purpose, and the complexity of its underlying data and methodology.
Table: Detailed Reasoning for the DQM Assessment - Stranded Asset Analysis
L1 Parameter
L1 Assessment
L2 Parameter
L2 Assessment
Reasoning
Materiality
High
Reliance
High
High reliance as its output (management adjustment to ECL/LI) is used to inform key business decisions, climate risk provisioning, capital adequacy discussions (e.g., ICAAP capital add-on), and regulatory stress testing exercises (e.g., HKMA CRST). The identified losses are material (USD 2.7bn for MST 2025).




Purpose
High
The SAA serves a high-purpose function by explicitly quantifying tail physical climate risks (complete erosion of value) that are not fully captured by traditional credit risk models or PPI haircuts. This directly impacts financial provisioning and capital requirements for climate risk.




Coverage
High
Covers a significant portion of the Wealth and Retail Banking (WRB) portfolio, specifically residential mortgages, across key vulnerable markets including Hong Kong, Korea, Singapore, Taiwan, and India. This covers 59% of the WRB book.
Complexity
Low (Simple)
Network
Medium
The SAA is a standalone analytical tool that feeds directly into management adjustments for ECL/LI. It uses inputs from internal credit risk systems and external climate risk vendors (Data Strategy Team - e.g., flood_risk_score_desc, storm_risk_score_desc, sea_level_rise_rcp85y2100_value, flood_defense_sop, distance_to_coast, outstanding_usd from the uploaded file). While its output impacts financial metrics, it does not directly interact with complex internal capital or risk management models in a highly interconnected network (e.g., no iterative feedback loops to other core models).




Calculation Specification
High
The algorithm for identifying stranded assets is relatively simple and deterministic, based on clear "if-then" trigger criteria. It applies specific thresholds for mitigants (e.g., Flood Defense SOP \le 20, Property Age pre-1970, Distance to Coast \le 1 \text{km}). Expert judgment is high in the selection of these thresholds and the interpretation of climate scenarios (combination of RCPs and SSPs). The logic for insurance benefits and phasing of impact is clearly defined.




Data
Medium
Good level of certainty in data values where available (e.g., outstanding balances, geo-coordinates). Input data is sourced from both external vendors (Data Strategy Team providing risk scores, sea level rise values, flood defense SOP, distance to coast) and internal country teams (providing Property Type and Property Age data). However, there are acknowledged data availability and usability challenges across footprint markets for critical mitigant variables like Property Age (not sourced/usable for Korea, Taiwan, India) and Property Type (not sourced/usable for Korea, Singapore, Taiwan, India). Strong controls are in place for input data quality and integrity. Expert judgment is high in handling these data limitations, leading to 'best-effort' analysis in certain segments.



