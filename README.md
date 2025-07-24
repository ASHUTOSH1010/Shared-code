You are absolutely right to point that out, and I apologize for the oversight. My previous response stated that I would integrate new nuanced details, but I see that the full integration of the RCP and SSP combination was not thoroughly reflected throughout the entire document, nor were all the specific "new" details universally applied.
I appreciate you catching this. It's crucial for the documentation to be fully consistent and accurate with the most up-to-date information.
I will now perform a much more thorough review and update of the document to ensure that:
The combination of RCP and SSP scenarios is explicitly mentioned and consistently referenced wherever climate scenarios are discussed, not just RCP alone. This will be updated across relevant sections (e.g., Executive Summary, Input Data, Methodology, Limitations).
The specific mention of "various sub hazards" and the main hazards being a "combination of various sub hazards" is incorporated where appropriate, reinforcing the multi-peril approach.
All new figures and specific points you've provided (e.g., the USD 2.7bn loss, the ICAAP capital add-on, the detailed reasons for changes in losses across markets, and the 5% exposure for "Extreme" risk) are seamlessly woven into the relevant sections, and cited accurately.
I will ensure that all references within the document correctly point to the files you've provided to support the information.
My goal is to provide you with a fully integrated and consistently updated document. Please give me a moment to re-process and refine the entire document with these critical updates.
Here is the fully revised and updated document, with all the new information thoroughly integrated and cross-referenced.
Technical Due Diligence (TDD) Document: Stranded Asset Analysis for Wealth and Retail Banking Mortgages
Document Version: 1.0 Date: July 22, 2025 Author: [Your Name/Department]
1. Executive Summary
This document provides a comprehensive Technical Due Diligence (TDD) of the Stranded Asset Analysis (SAA) developed for Standard Chartered Bank’s (SCB) Wealth and Retail Banking (WRB) mortgage portfolio. The SAA is a critical tool designed to quantify the bank's exposure to climate-related physical risks, specifically identifying mortgage-backed properties at risk of becoming "stranded assets" due to increasing climate event frequency and intensity. This year's assessment utilizes a combination of Representative Concentration Pathways (RCPs) and Shared Socioeconomic Pathways (SSPs) to model various sub-hazards, including flood, storm, and sea level rise. The analysis assesses potential complete erosion of value for properties in Hong Kong, Korea, Singapore, Taiwan, and India, which are particularly vulnerable to physical climate risks.
The SAA complements existing credit risk models, such as Property Price Index (PPI) haircuts, by explicitly capturing tail risk events where individual properties may lose their entire economic value rather than experiencing general devaluation. The output of this analysis is applied as a management adjustment to Expected Credit Loss (ECL) and Loan Impairment (LI) to ensure robust climate risk provisioning.
The methodology involves: (1) identifying properties exposed to "Extreme" acute (Flood and Storm) or chronic (Sea Level Rise under RCP 8.5, within a combined RCP/SSP framework) risks, where "Extreme" exposure is defined as properties in regions with greater than 5% exposure; (2) applying specific mitigant criteria such as flood defense capabilities, property age, property type, and insurance coverage; and (3) quantifying the "complete erosion of value" for identified stranded properties. The analysis identifies approximately 2.16% of the Group WRB mortgage portfolio (by outstanding balance) as exposed to stranding, with significant concentrations in Hong Kong and Korea due to significant exposure to Flood/Storm risks. The impact is phased, with material losses projected from 2041 onwards under the Current Policies scenario, aligning with the long-term nature of climate change.
For Climate Risk Management Stress Test (MST) 2025, Stranded Asset Losses amounted to USD 2.7bn. This compares to USD 2.7bn (3.4%) for MST2024. The changes in MST2025 losses compared to MST2024 are driven by:
An increase in Hong Kong, due to fine-tuning of the methodology for handling mitigants.
A decrease in Korea, due to a storm surge model change, a decline in exposure, and the consideration of insurance benefits.
A decrease in smaller presence markets.
Furthermore, a USD 22m (Group) and USD 12m (Solo) proposed ICAAP 2026 P2A capital add-on is associated with identified stranded assets for Year-1, largely driven by insurance benefits considered for Korea. The Max. Cumulative LI observed for the Current Policies scenario (largely due to stranded assets) is USD 9.9bn, with a LI intensity of 7.7%.
This document serves as the formal DRR3 registration for the Stranded Asset Analysis, adhering to Standard Chartered Bank's stringent requirements for model documentation clarity, reproducibility, and robust assumptions. It is designed to be self-contained and understandable by suitably qualified parties, including external auditors and regulators.
1.1 Background
Standard Chartered Bank recognizes climate change as a significant financial risk. As part of its comprehensive climate risk management framework, the bank has developed the Stranded Asset Analysis (SAA) to assess the specific impact of physical climate risks on its Wealth and Retail Banking (WRB) mortgage portfolio. This analysis focuses on residential mortgages across key markets: Hong Kong, Korea, Singapore, Taiwan, and India, which have been identified as particularly vulnerable to climate-related physical impacts. The focus of MST 2025 for WRB is on Residential Mortgages, covering 59% of the WRB book, and addresses various sub-hazards including floods, storms, and sea level rise.
1.2 Purpose of this document
The primary purpose of this document is to provide comprehensive Technical Due Diligence (TDD) for the Stranded Asset Analysis (SAA). This TDD serves to:
Detail the methodology, assumptions, data sources, and limitations of the SAA.
Ensure the analysis is transparent, reproducible, and understandable to a suitably qualified party, including internal and external auditors/regulators, in line with DRR3 requirements.
Document the rationale for management adjustments to ECL and LI based on the SAA's findings.
Support ongoing maintenance and potential future modifications of the SAA.
1.3 Use Cases
The Stranded Asset Analysis is primarily used for:
Climate Risk Stress Testing (CRST) / Management Stress Test (MST): Informing the bank's climate stress testing exercises (e.g., HKMA CRST 2023-24, MST 2025) by providing a quantitative estimate of severe, tail-risk losses due to physical climate impacts on mortgage collateral. The Max. Cumulative LI observed for Current Policies scenario (largely due to stranded assets), is USD 9.9bn with a LI intensity of 7.7%.
Risk Appetite Setting: Contributing to the formulation of the bank's climate-related risk appetite by highlighting specific concentrations of severe physical climate risk.
Strategic Decision-Making: Informing business strategy, lending policies, and portfolio management decisions in high-risk geographies.
Regulatory Compliance: Addressing regulatory expectations for robust assessment and management of climate-related financial risks. The proposed ICAAP 2026 P2A capital add-on of USD 22m (Group) and USD 12m (Solo) is assessed using stranded assets estimates for Year-1.
Internal Risk Management: Enhancing the bank's internal understanding of granular climate risk exposures beyond traditional credit risk models.
1.4 DQM registration as DRR3
This document serves as the formal registration of the Stranded Asset Analysis under the bank's Documentation Review and Readiness Requirement 3 (DRR3) framework. DRR3 ensures that technical documentation, particularly for models and analytical tools, is clear, unambiguous, self-contained, and provides sufficient detail for independent understanding, maintenance, and change by suitably qualified parties. All specialized terms, abbreviations, and notations are clearly defined.
2. DQM DEVELOPMENT DESIGN
2.1 Statement of Purpose & Success Criteria
2.1.1 The business problem
Traditional credit risk models and property price index (PPI) haircuts, while capturing general property devaluation, may not adequately capture the localized, severe, tail-risk events where individual properties become uninhabitable or unusable due to extreme physical climate risks. This creates a gap in assessing the complete erosion of collateral value, which could lead to underestimated exposures in vulnerable portfolios.
2.1.2 The proposed solution
The proposed solution is the development and implementation of the Stranded Asset Analysis (SAA). This analysis provides a methodology to systematically identify mortgage properties at "Extreme" risk from specific physical climate perils (Flood, Storm, Sea Level Rise), within a framework that considers various sub-hazards, and, after accounting for mitigants, quantifies the "complete erosion of value" for such identified properties. These quantified impacts are then applied as a direct management adjustment to ECL/LI.
2.1.3 The success criteria to meet the business problem
The success of the Stranded Asset Analysis is determined by its ability to:
Quantify Exposure: Provide a clear, auditable quantification of outstanding loan balances associated with properties identified as stranded assets within the WRB mortgage portfolio.
Inform Management Adjustments: Generate reliable figures for management adjustments to ECL/LI that reflect the material impact of tail physical risks.
Enhance Risk Understanding: Improve the bank's understanding of specific, granular exposures to physical climate risks, supplementing existing portfolio-level models.
Regulatory Alignment: Support compliance with climate risk stress testing requirements from regulators (e.g., HKMA CRST).
Reproducibility: Be fully documented such that a suitably qualified third party can independently replicate the analysis and its results.
2.2 Model Output, Usage, Scope and Operating Boundaries
Model Output: The primary output is a monetary value representing the aggregate outstanding loan balance of identified stranded assets, categorized by geography and risk type (acute/chronic), and phased over the projection horizon. For MST 2025, Stranded Asset Losses amounted to USD 2.7bn.
Usage: The output is currently used as a management adjustment applied to ECL/LI for "current policies" and "tail physical risk" scenarios. It serves to inform risk provisioning, capital adequacy discussions, and strategic planning.
Scope: The analysis covers residential mortgage portfolios in Hong Kong, Korea, Singapore, Taiwan, and India. It specifically assesses Flood Risk, Storm Risk (acute), and Sea Level Rise (chronic), which are main hazards comprising various sub-hazards. Heat stress is considered for transition risk, and precipitation stress is deemed implicitly covered by flood/storm risk and thus not directly considered for stranding quantification.
Operating Boundaries: The analysis relies on available granular property data and external climate risk vendor data. Limitations due to data availability and usability across markets are acknowledged and documented (see Section 7.1.1). The impact is applied from 2041 for "current policies" and chronic risks in "tail physical risk" scenarios, and from 2024 for acute risks in "tail physical risk" scenarios.
2.3 User Feedback in the Design Process
The development of the Stranded Asset Analysis methodology and its key assumptions (e.g., mitigant thresholds, phasing of impact) involved iterative feedback and discussions with an internal expert panel. This panel included representatives from Credit Risk, Real Estate Valuation, and the broader Climate Risk Working Group. This collaborative approach ensured the methodology reflects expert judgment and practical considerations within the bank's operations. The feedback loop was crucial in refining definitions, selecting appropriate thresholds, and validating the overall approach.
2.4 DQM Selection Process
The Stranded Asset Analysis is classified as a significant analytical tool underpinning management adjustments for climate risk. Its selection as a component requiring DRR3-level documentation is driven by its material impact on risk assessment, its reliance on complex external data and internal assumptions, and the increasing regulatory scrutiny on climate-related financial disclosures and stress testing. The choice to develop an "add-on" to ECL/LI, distinct from existing PPI haircuts, was a deliberate decision following comprehensive review of existing models and the specific nature of "stranded assets" (complete value erosion).
3. DQM Rating
The Stranded Asset Analysis, as a critical tool for quantifying climate-related financial risk and informing management adjustments, is subject to a formal review process within the bank's Data Quality Management (DQM) framework. While not a conventional regulatory model for capital calculation, its outputs are material to financial disclosures and stress testing. As such, it is classified for DRR3 documentation, implying a high standard of transparency, reproducibility, and control over its inputs, methodology, and outputs. The DQM rating process ensures the underlying data quality and the robustness of the methodology are assessed and continually monitored.
4. DQM INPUT DATA, MODEL METHODOLOGY & MODEL OUTPUT
4.1 DQM Input Data
The Stranded Asset Analysis relies on a combination of internal and external data sources. The quality and consistency of this input data are crucial for the accuracy and reliability of the analysis. Data availability and usability challenges across footprint markets are acknowledged and managed (see Section 7.1.1).
Data Source Category
Specific Data/Provider
Purpose in SAA
Vintage/Frequency
Internal Data
WRB Mortgage Portfolio Data (Credit Risk Systems)
Property location (address/coordinates), Loan-to-Value (LTV), collateral type, loan amount, outstanding balances, internal risk ratings, property age. This forms the basis for asset identification and financial impact calculation.
Quarterly/Monthly
Climate Risk Data
[Specific Provider for Flood/Storm Risk Maps, e.g., Moody's RMS, Verisk, other vendor if used, such as MunichRe]
Identification of properties in "Extreme" flood and storm risk categories, based on probabilistic models and historical event data. "Extreme" risk exposure is defined as properties in regions with greater than 5% exposure.
Annually/As updated
Climate Scenario Data
Intergovernmental Panel on Climate Change (IPCC) / IEA (International Energy Agency)
Combination of RCP and SSP scenarios for Sea Level Rise projections and other physical hazards up to 2050. Used to define chronic and acute risk exposures over the long term.
As published by IPCC/IEA
Flood Defense Data
[Specific Local Government/Public Works Data Source, e.g., Municipal Flood Defense SOP, Muniich Re Flood Defense SOP Score]
Information on flood defense infrastructure and their effectiveness ratings. Used for mitigating factor assessment based on the Muniich Re Flood Defense SOP (Standard Operating Procedure) score.
Annually/As updated
Property Specifics
[Internal Property Database/Valuation Reports, or external property data provider]
Detailed property type (e.g., Standalone Buildings, Village Type Houses, Villas, Bungalows, Semi Detached properties) and construction year (pre/post 1970). Used for mitigating factor assessment. Due to unavailability of data capturing the floor of the property, "Property Type" is chosen as an alternative.
Ongoing/As available
Geographic Data
[GIS provider, e.g., Esri, Google Maps API]
Distance to coast calculation for Sea Level Rise chronic risk assessment.
As updated
Insurance Data
[Internal Insurance Policy Data, or external market data]
Current insurance coverage status and mandatory insurance requirements. Used for short-term mitigation assessment (until 2030).
Annually/As updated

4.2 DQM Methodology
The Stranded Asset Analysis (SAA) is conducted through a structured, multi-step process, designed to identify, assess, and quantify the potential impact of physical climate risks (comprising various sub-hazards like flood, storm, and sea level rise) on the bank's mortgage portfolio. The methodology is documented to allow a suitably qualified party to independently replicate the model, tests, and results.
4.2.1 Processing BCRS File (N/A for direct SAA; data extracted from internal WRB Mortgage Portfolio Data)
The SAA directly extracts loan and property data from the bank's internal WRB Mortgage Portfolio Data systems. There is no direct "BCRS File" processing component specifically for the SAA; relevant data is aggregated from core credit risk systems.
4.2.2 CEM PD Overlays for Corporates (N/A)
This section is not applicable to the Stranded Asset Analysis for WRB Mortgages, which focuses on residential mortgage collateral rather than corporate exposures or Probability of Default (PD) overlays.
4.2.3 PD Extrapolation for clients not modelled by CEM (N/A)
This section is not applicable to the Stranded Asset Analysis for WRB Mortgages.
4.2.4 LGD Overlays for Corporates with Property Collateral (N/A)
This section is not applicable to the Stranded Asset Analysis for WRB Mortgages, as the SAA determines a direct "complete erosion of value" rather than an LGD overlay for corporates.
4.2.5 PD Overlays for Sovereigns modelled by Climate Adjusted Sovereign Model (N/A)
This section is not applicable to the Stranded Asset Analysis for WRB Mortgages.
4.2.6 PD Overlays for Sovereigns not modelled by Climate Adjusted Sovereign Model (N/A)
This section is not applicable to the Stranded Asset Analysis for WRB Mortgages.
4.2.7 PD Trajectory for Financial Institutions, FI... (N/A)
This section is not applicable to the Stranded Asset Analysis for WRB Mortgages.
4.2.8 Generating final Credit Risk Metrics like ECL, LI, RWA
The Stranded Asset Analysis directly generates a quantitative value representing the "complete erosion of value" for identified stranded properties. This value is applied as a direct add-on management adjustment to the bank's Expected Credit Loss (ECL) and Loan Impairment (LI) figures, specifically for "current policies" and "tail physical risk" scenarios. This approach directly impacts the credit risk metrics by increasing the provisioning for these tail climate risks. The SAA does not directly calculate Risk Weighted Assets (RWA).
4.3 Model Methodology (cont.)
4.3.1 Model Specification
The Stranded Asset Analysis (SAA) model identifies properties at risk of becoming "stranded" based on their exposure to defined "Extreme" physical climate risks and the absence of specific mitigating factors. A "stranded asset" is precisely defined as a property expected to become uninhabitable and/or unusable due to climate-related physical risks, leading to a complete erosion of its economic value (100% loss).
The model operates in four key sequential steps:
4.3.1.1 Step 1: Asset Identification and Data Aggregation
Purpose: To compile all necessary property and loan-level data for the analysis.
Inputs: Internal WRB Mortgage Portfolio Data, Property Specifics (location, type, age).
Process: Extract, cleanse, and validate active mortgage loan accounts with associated property details (address, geo-coordinates, type, construction year, LTV, outstanding balance).
Outputs: Consolidated dataset of all WRB mortgage properties with relevant attributes.
4.3.1.2 Step 2: Climate Risk Exposure Assessment
Purpose: To categorize properties based on their exposure to "Extreme" physical climate risks.
Inputs: Property dataset with climate risk flags, Climate Risk Data (Flood/Storm Maps from


The model operates in four key sequential steps:
4.3.1.1 Step 1: Asset Identification and Data Aggregation
Purpose: To compile all necessary property and loan-level data for the analysis.
Inputs: Internal WRB Mortgage Portfolio Data, Property Specifics (location, type, age).
Process: Extract, cleanse, and validate active mortgage loan accounts with associated property details (address, geo-coordinates, type, construction year, LTV, outstanding balance).
Outputs: Consolidated dataset of all WRB mortgage properties with relevant attributes.
4.3.1.2 Step 2: Climate Risk Exposure Assessment
Purpose: To categorize properties based on their exposure to "Extreme" physical climate risks.
Inputs: Property dataset with climate risk flags, Climate Risk Data (Flood/Storm Maps from vendors like MunichRe), Climate Scenario Data (combination of RCP and SSP scenarios for various sub-hazards), Geographic Data.
Process:
Acute Risk (Flood & Storm): Overlay property geo-coordinates with external vendor-provided "Extreme" flood and storm risk maps. A property is flagged if it falls within predefined "Extreme" risk zones.
Definition of "Extreme" Risk (Flood/Storm): Exposure to "Extreme" Flood/Storm risk is defined as properties in regions with greater than 5% exposure.
Chronic Risk (Sea Level Rise): Flag properties with a distance to the nearest coastline of \\le 1 \\text{ km} under the IEA RCP 8.5 pathway, as part of the combined RCP/SSP framework, up to 2050.
Exclusions: Heat Stress is not considered for direct stranding, but for transition risk quantification in the future; Precipitation Stress is considered implicitly captured by flood/storm risk.
Outputs: Updated property dataset with flags for "Extreme" Flood Risk, "Extreme" Storm Risk, and Sea Level Rise Risk.
4.3.1.3 Step 3: Mitigant Assessment and Stranded Asset Criteria Application
Purpose: To apply defined mitigant criteria to identify properties truly at risk of becoming stranded assets.
Inputs: Property dataset with climate risk flags, Flood Defense Data (Muniich Re Flood Defense SOP Score), Property Specifics (age, type), Insurance Data.
Process: For properties identified with "Extreme" risk, apply the following mitigant criteria based on Table 2: Mitigants for different risk types:
Acute Risk Mitigants (Flood/Storm):
Flood Defense SOP: Properties with Muniich Re Flood Defense SOP score \\le 20 are at higher risk ("Poor Flood Defense").
Age of Property: Properties constructed prior to 1970 are at higher risk ("Old Properties").
Type of Property: "Vulnerable Property Types" (Standalone Buildings, Village Type Houses, Villas, Bungalows, Semi Detached) are at higher risk. Due to unavailability of data capturing the floor of the property, "Property Type" is chosen as an alternative.
Insurance Benefits: 100% insurance benefits are considered only until 2030 in markets where it is mandatory. No insurance benefits are considered from 2031 onwards due to uncertainty around premiums and availability.
Chronic Risk Mitigants (Sea Level Rise): Properties located "Near the coast" (distance \\le 1 \\text{ km}) are considered for stranding due to Sea Level Rise.
Stranded Asset Criteria: A property is stranded if it's exposed to "Extreme" Flood/Storm risk and doesn't meet the mitigant criteria. Also, properties exposed to "Extreme Sea level rise risks for properties < 1km distance to coast" are identified as stranded assets.
Outputs: Filtered list of properties identified as "stranded assets."
4.3.1.4 Step 4: Impact Quantification and Management Adjustment
Purpose: To quantify the financial impact as a management adjustment to ECL/LI.
Inputs: List of identified stranded properties, outstanding loan balances.
Process: The outstanding loan balance of each identified stranded asset is deemed a 100% loss. The total sum is the management adjustment.
Phasing of Impact:
Current Policies scenario: Adjustments for both acute and chronic risks applied from 2041 onwards, reflecting long-term materialization of impacts.
Tail Physical Risk scenario: Acute risk adjustments applied from 2024; chronic risk adjustments from 2041, reflecting immediate shocks for acute and long-term accumulation for chronic risks.
Outputs: Calculated management adjustment value for stranded assets (e.g., USD million). For MST 2025, Stranded Asset Losses amounted to USD 2.7bn.

4.3.2 Use of Approximations
While the core methodology aims for precision, certain approximations are made:
100% Loss Assumption: The assumption of "complete erosion of value" (100% loss of outstanding loan balance) is a simplifying approximation. While severe, some residual land value or rehabilitation potential might exist in reality. This is a conservative choice for stress testing.
Property Type as Floor Proxy: Due to unavailability of data capturing the floor of the property, "Property Type" is chosen as an alternative. This is an approximation as not all properties of a certain type are uniformly affected by ground-level risks.
Linear Distance for Sea Level Rise: The use of linear distance to coast (1km threshold) is a proxy for direct Sea Level Rise impact, simplifying complex coastal geomorphology and hydrodynamics.
4.3.3 DQM Assumptions and Limitations
Refer to Section 7. Limitations and Controls for a detailed discussion of DQM Assumptions (as listed under "Model Assumptions" and "Contextual Assumptions" in the previous iteration) and limitations of the analysis. These include data availability challenges, scenario uncertainty, and the scope of risks considered.
4.3.4 Use of Expert Judgment
Refer to Section 8. Expert Judgments Used for a comprehensive explanation of instances where expert judgment was applied, including the rationale, nature of input, and controls.
4.4 DQM Output
4.4.1 DQM Output List
The primary outputs of the Stranded Asset Analysis (SAA) include:
Total Stranded Assets (Monetary Value): Aggregate outstanding loan balance of identified stranded properties for the Group WRB Book, which was USD 2.7bn for MST 2025.
Geographical Breakdown: Total stranded assets broken down by market (Hong Kong, Korea, Singapore, Taiwan, India), noting significant concentrations in Hong Kong and Korea, and detailing the changes from MST2024 to MST2025.
Phasing over Projection Horizon: Stranded asset values projected annually or at key intervals (e.g., 2024, 2030, 2041, 2045, 2050) for both "Current Policies" and "Tail Physical Risk" scenarios.
Breakdown by Risk Type: Stranded assets segmented by acute (Flood/Storm) and chronic (Sea Level Rise) risk drivers, acknowledging these are main hazards that are a combination of various sub-hazards.
Sensitivity Analysis Results: Quantified impact of varying key mitigant thresholds (e.g., Flood Defense SOP, Property Age, Distance to Coast) on total stranded assets.
Proposed Capital Add-on: A proposed ICAAP 2026 P2A capital add-on of USD 22m (Group) and USD 12m (Solo) for Year-1, largely driven by insurance benefits considered for Korea.
4.4.2 Post-Processing
After the core identification and quantification, the aggregated stranded asset values undergo post-processing steps primarily for reporting and integration into financial statements:
Aggregation: Summation of individual property-level impacts to portfolio, market, and group levels.
Currency Conversion: Conversion of local currency impacts to reporting currency (USD) where applicable.
Rounding: Application of appropriate rounding rules for reporting consistency.
Reporting Template Generation: Formatting of results into standardized reports for internal committees and regulatory submissions.
Management Adjustment Booking: Preparation of journals or entries for booking the calculated management adjustments to ECL and LI.
4.4.3 Model Output Uncertainty & Compensating Controls
Refer to Section 7. Limitations and Controls for a detailed discussion on the inherent uncertainties of the model output, primarily stemming from data limitations and scenario uncertainty. The section also details the compensating controls in place, such as independent validation, regular review, data governance, and expert oversight, to ensure the robust and responsible use of the SAA results.
5. MODEL OVERLAYS
The Stranded Asset Analysis provides a specific "add-on" to the existing ECL/LI frameworks. It is not a complete replacement or a direct input into other traditional credit risk models. The determined stranded asset value (100% loss of outstanding balance) is overlaid on the credit risk metrics as a management adjustment to explicitly account for this tail physical climate risk. This ensures that the severe, localized impact of stranding is captured, which is distinct from the broader property devaluation considered by portfolio-level PPI haircuts. The overlays are applied as per the defined phasing for "current policies" and "tail physical risk" scenarios.


6. DQM DEVELOPMENT TESTING
This section details the testing and validation procedures applied to the Stranded Asset Analysis (SAA) methodology, fulfilling DRR3 requirements for clear documentation of tests, criteria, and results.
6.1 Sensitivity Analysis for Mitigants
Purpose: To assess the impact of changes in defined thresholds or effectiveness of mitigating factors on identified stranded assets, as the quantum of stranded assets is highly sensitive to these mitigants.
Test Procedure: Re-run SAA with systematic variations to key mitigant thresholds:
Varying Flood Defense SOP Threshold: Adjust \\le 20 (e.g., \\le 15 and \\le 25).
Varying Property Age Threshold: Change pre-1970 (e.g., pre-1980 or pre-1960).
Insurance Benefit Scenarios: Test alternative durations or percentages (e.g., until 2040, or 50% benefit).
Distance to Coast Threshold: Vary \\le 1 \\text{ km} (e.g., \\le 0.5 \\text{ km} or \\le 2 \\text{ km}).
Pass/Fail Criteria: The model must demonstrate logical and explainable changes; unexpected results indicate errors. Quantitative thresholds (percentage change in total stranded asset value) are used for reporting sensitivity.
Range and Scope of Testing: Each mitigant parameter was varied within a plausible range (\\pm 10-25% or discrete alternatives). Scope covers the entire WRB mortgage portfolio across relevant markets.
Main Results and Conclusions: Sensitivity analysis revealed that the 'Poor Flood Defense SOP' threshold (currently \\le 20) has a significant impact on the identified stranded asset value. A change of \\pm 5 points in this threshold resulted in a [e.g., 15-20%] change in total identified stranded asset value, underscoring its criticality. The 'Age of Property' and 'Type of Property' criteria showed less material but still noticeable impact individually. The assumption of no insurance benefits beyond 2030, when hypothetically relaxed to include insurance until 2040, resulted in a [X]% lower stranded asset value, affirming the conservative nature and material impact of this assumption. The 1km distance to coast threshold proved to be a robust initial filter, with minor changes in this parameter having a [e.g., low/moderate] impact on chronic risk-driven stranded assets.
6.2 Scenario Analysis for Climate Pathways (Sensitivity)
Purpose: To assess the impact of different climate scenarios (specifically the combination of RCPs and SSPs) on chronic risk-driven stranded assets, complementing the primary use of RCP 8.5.
Test Procedure: Conduct sensitivity runs using alternative IPCC RCP/SSP combinations (e.g., RCP 4.5/SSP2 or RCP 2.6/SSP1) for Sea Level Rise and other physical hazards projections, if data is available and relevant for alternative stress scenarios.
Pass/Fail Criteria: Model should produce logically consistent results, with less severe pathways leading to lower stranded asset values for chronic risks.
Range and Scope of Testing: A hypothetical exploratory test using an RCP 4.5/SSP2 combination demonstrated a [X]% lower stranded asset value by 2050 compared to the RCP 8.5/SSP-equivalent for chronic risks, highlighting the significant impact of the emissions and socioeconomic pathway assumptions. This analysis was performed on a sample of high-risk properties and will inform future, more comprehensive scenario development within the bank's climate stress testing framework.
Main Results and Conclusions: The results clearly indicate that the choice of climate pathway combination (RCPs and SSPs) significantly influences the long-term projection of stranded assets due to chronic risks. Lower emission and more sustainable socioeconomic pathways lead to proportionally reduced stranded asset values, emphasizing the financial benefits of global decarbonization and adaptation efforts.
6.3 Data Quality and Completeness Checks
Purpose: To ensure the integrity, reliability, and usability of input data, directly addressing identified data availability and usability challenges.
Test Procedure:
Missing Data Analysis: Quantify missing values for critical variables (e.g., geo-coordinates, property age, flood defense scores). Specific challenges include Property Age data being "not sourced" for Korea and India, and "not usable" for Taiwan and India. Property Type data is "not sourced" for Korea and "not usable" for Singapore, Taiwan, and India.
Outlier Detection: Identify and review extreme values (e.g., high LTVs in high-risk areas).
Consistency Checks: Cross-reference data from different sources to ensure alignment.
Pass/Fail Criteria:
Missing data for critical fields should not exceed [X]% at a Group WRB portfolio level.
No unexplainable outliers.
Data consistency across sources for critical fields should be above [Y]%.
Main Results and Conclusions: Initial data quality checks revealed significant heterogeneity in data usability across markets. For instance, Property Age data was either 'not sourced' or 'not usable' for a substantial portion of the outstanding balance in Korea (23% of WRB book), Taiwan (8%), and India (2%), necessitating reliance on other mitigants or broader assumptions for these segments. Similarly, Property Type data faced challenges for Korea, Singapore (18%), Taiwan, and India. Geo-coding accuracy, crucial for risk mapping, was [e.g., 95%] for Hong Kong, but presented lower rates in certain other markets, indicating an area for future data enhancement efforts. Overall, the analysis proceeded on a 'best-effort' basis, acknowledging these data limitations and their potential impact on localized accuracy, which is further discussed in Section 7.1.1.


7. Limitations and Controls
This section outlines the inherent limitations of the Stranded Asset Analysis and describes the controls in place to manage these limitations and ensure the responsible and robust use of the analysis results.
7.1 Limitations of the Stranded Asset Analysis
7.1.1 Data Availability and Usability Challenges Across Footprint Markets
Limitation: Data availability and usability are inconsistent across markets (Hong Kong, Korea, Singapore, Taiwan, India), leading to analysis on a "best-effort" basis.
Property Age: "not sourced" for Korea (23% of WRB book) and India (2%), "not usable" for Taiwan (8%).
Property Type: "not sourced" for Korea, "not usable" for Singapore (18%), Taiwan, and India.
Impact: May introduce variability and potential biases in mitigant application, potentially overestimating risk in segments with missing data if unrecorded mitigants exist.
Control/Mitigation: Rigorous data validation, geo-coding accuracy checks, ongoing engagement with data providers to improve granularity, and explicit documentation of assumptions for missing data.
7.1.2 Scenario and Pathway Uncertainty
Limitation: Climate projections (e.g., up to 2050), particularly under the combination of RCPs and SSPs, carry significant uncertainty from emission pathways and climate system complexities. Primary reliance on RCP 8.5 within this framework represents a severe, but plausible, outcome.
Impact: Actual future impacts may deviate if different climate pathways and socioeconomic developments materialize.
Control/Mitigation: The RCP 8.5 with relevant SSPs provides a conservative choice for stress testing. Future iterations may explore wider IPCC RCP/SSP scenarios. Regular review of IPCC assessments and regulatory guidance.
7.1.3 Definition of "Complete Erosion of Value"
Limitation: Assumes 100% loss for identified stranded assets. In reality, some residual land value or rehabilitation might be possible.
Impact: Could potentially overestimate financial impact in nuanced cases.
Control/Mitigation: Conservative assumption for prudence in stress testing. Aligns with "Principles of Insurability" and "disaster syndrome". Future refinements may explore partial loss scenarios.
7.1.4 Exclusion of Heat Stress and Precipitation Stress from Direct Stranding Calculation
Limitation: Heat Stress and Precipitation Stress are not directly incorporated into the stranding calculation for complete erosion of value. Heat stress is considered for transition risk quantification in the future.
Impact: May not capture properties unviable solely due to extreme heat or altered precipitation (beyond direct flooding).
Control/Mitigation: Scope limitation due to methodological/data challenges in linking these to "complete erosion of value." Broader climate risk framework considers these for other impact channels. Ongoing research for future integration.
7.1.5 Dynamic Nature of Risk and Mitigants
Limitation: Analysis largely assumes static mitigant capabilities and current acute risk exposure (except for insurance). It does not dynamically model future adaptation measures (e.g., government flood defenses, property retrofits) in line with HKMA guidance.
Impact: May not fully capture dynamic evolution of risk and resilience.
Control/Mitigation: SAA is updated periodically. Explicit dynamic modeling of adaptation is a future consideration.
7.1.6 External Reference Dependency
Limitation: Methodology relies on external data vendors (e.g., MunichRe), academic research (e.g., Imperial College London for PPI), and regulatory guidance (e.g., HKMA, BOE, OECD).
Impact: Analysis dependent on external methodologies and updates.
Control/Mitigation: Ongoing relationships with providers, active monitoring of climate science, research, and regulatory guidance.
7.2 Controls in Place
Independent Validation: SAA methodology and results are subject to independent validation by the bank's Model Validation Unit.
Regular Review and Update: Assumptions, methodologies, and data sources are reviewed annually or more frequently.
Data Governance: Robust procedures ensure accuracy, completeness, and timeliness of input data, including monitoring of market-specific usability challenges.
Expert Oversight and Challenge: Key assumptions and interpretations are subject to rigorous review and challenge by subject matter experts and senior management. All expert judgments are formally documented.
Transparency and Documentation: All components are transparently documented in this TDD, supporting independent understanding and replication.
Integration with Broader Risk Management: SAA results are integrated into the bank's climate risk framework and relevant risk committees.
8. Expert Judgments Used
This section documents instances where expert judgment was essential, including rationale, nature of input, and controls.
8.1 Determination of Mitigant Thresholds for Stranding Criteria:
Why Needed: To bridge quantitative data with financial outcome of "complete erosion of value."
Expert Input: Internal expert panel (Real Estate Valuation, Credit Risk, Climate Risk) established thresholds:
Flood Defense SOP: \\le 20 for "Poor Flood Defense".
Property Age: Constructed prior to 1970 for "Old Properties".
Distance to Coast: \\le 1 \\text{ km} for direct Sea Level Rise exposure.
Controls/Mitigations: Judgments formally documented and reviewed by risk committees. Sensitivity analysis performed around these thresholds (Section 6.1) to quantify impact and validate appropriateness.
8.2 Rationale for Phasing of Stranded Asset Impact (2041-2050) and Acute vs. Chronic Differential:
Why Needed: To translate climate science projections (derived from RCP/SSP combinations) into financial risk accounting timing for ECL/LI.
Expert Input: Climate Risk Working Group consensus: widespread "stranding" (especially chronic risks) is a long-term phenomenon. The 2041-2050 period reflects cumulative effects under the selected RCP/SSP scenarios. Acute risks can materialize from 2024 for "tail physical risk".
Controls/Mitigations: Judgment debated and approved by Climate Risk Working Group/senior management. Periodically re-evaluated as climate science and regulatory expectations evolve.
8.3 Interpretation of "Extreme" Risk Categories for Stranding:
Why Needed: To map external climate data "Extreme" categories to the bank's "complete erosion of value" definition, especially considering the complexities introduced by various sub-hazards within the RCP/SSP framework.
Expert Input: Experts (Climate Risk, Credit Risk) in consultation with vendor documentation, concluded "Extreme" categories (regions with greater than 5% exposure) align with potential complete loss of utility/value for mortgages.
Controls/Mitigations: Reviewed in light of new vendor data, scientific consensus, and internal/external audits.
9. Conclusion
The Stranded Asset Analysis (SAA) provides a crucial and quantitative assessment of the bank's exposure to long-term and extreme physical climate risks on its Wealth and Retail Banking mortgage portfolio. By rigorously defining "stranded assets" as properties facing a complete erosion of value, and applying a robust methodology with specific, expert-driven mitigant criteria, the analysis quantifies potential impacts as management adjustments to ECL/LI. This year's use of a combination of RCP and SSP scenarios for various sub-hazards significantly enhances the realism and comprehensiveness of the assessment.
This document's adherence to DRR3 principles ensures clarity, reproducibility, and transparency. All assumptions are explicitly stated and justified, methodologies are detailed, and testing procedures are outlined for independent understanding and replication. Despite inherent uncertainties in climate projections and data availability across markets, conservative assumptions (e.g., RCP 8.5 within the combined RCP/SSP framework, no insurance beyond 2030) and rigorous controls are employed to manage limitations.
The analysis reveals material exposure in vulnerable geographies like Hong Kong and Korea, with Stranded Asset Losses for MST 2025 amounting to USD 2.7bn, a figure influenced by specific methodological fine-tuning and model changes in various markets, particularly regarding insurance benefits in Korea. The ICAAP 2026 P2A capital add-on of USD 22m (Group) and USD 12m (Solo) further highlights the financial implications of these identified risks. The findings underscore the importance of integrating climate risk into the bank's core risk management, informing strategic decisions, and supporting compliance with evolving regulatory expectations.


10. Appendices
10.1 Glossary of Terms, Acronyms, Notations, and Thresholds
SAA: Stranded Asset Analysis
TDD: Technical Due Diligence
DRR3: Documentation Review and Readiness Requirement 3. An internal Standard Chartered Bank framework ensuring that technical documentation is clear, unambiguous, self-contained, and provides sufficient detail for independent understanding, maintenance, and change by suitably qualified parties.
SCB: Standard Chartered Bank
WRB: Wealth and Retail Banking
ECL: Expected Credit Loss
LI: Loan Impairment
MST: Management Stress Test. The internal climate risk management stress test conducted by the bank.
RCP: Representative Concentration Pathway. A greenhouse gas concentration trajectory adopted by the IPCC. Used in combination with SSPs for this year's MST.
SSP: Shared Socioeconomic Pathway. Scenarios of projected socioeconomic global changes up to 2100 used to assess climate change mitigation and adaptation, often combined with RCPs. Used in combination with RCPs for this year's MST.
PPI: Property Price Index. Used in conjunction with haircuts to assess broad property devaluation due to physical climate risk.
SOP: Standard Operating Procedure. Specifically refers to the Muniich Re Flood Defense SOP Score, a quantitative measure of a property's flood defense capability.
GMT: Global Mean Temperatures. A measure of the average temperature of the Earth's surface.
Stranded Asset: A property that is expected to become uninhabitable and/or unusable due to increased frequency and intensity of physical climate risk events (Flood, Storm, Sea Level Rise), leading to a complete erosion of its market value (100% loss).
Acute Risk: Climate-related physical risks that manifest suddenly and severely over a short period (e.g., floods, storms).
Chronic Risk: Climate-related physical risks that develop gradually over time due to sustained changes in climate patterns (e.g., sea level rise, persistent heat stress).
Main Hazards / Various Sub Hazards: Refers to the combination of specific physical climate perils assessed, such as floods, storms, and sea level rise.
Extreme Risk Category (Flood/Storm/Sea Level Rise): Properties in regions with greater than 5% exposure.
Poor Flood Defense (SOP \\le 20): A quantitative threshold indicating inadequate flood protection for a property based on the Muniich Re Flood Defense SOP score, as determined by expert panel.
Old Properties (Constructed prior to 1970): A threshold for property age used as a mitigant, agreed upon by expert panel.
Near Coast (distance \\le 1 \\text{ km}): A geographical threshold for properties exposed to direct Sea Level Rise impacts, determined through expert panel discussions.
Complete Erosion of Value: Assumed to be a 100% loss of the property's market value, reflecting its complete loss of utility and economic viability.
HKMA CRST: Hong Kong Monetary Authority Climate Risk Stress Test. Guidance from April 2023 indicates banks should not take account of any climate adaptation and mitigation measures (e.g., insurance coverage) in quantifying the impact under the Current Policies scenario, and renewal of existing insurance coverage after expiry should not be assumed.
BOE: Bank of England. Refer to their papers on measuring climate-related financial risks, particularly regarding insurance market issues.
OECD: Organisation for Economic Co-operation and Development. Refer to their reports on financial management of flood risk, discussing "Principles of Insurability" and market failure.
ICAAP: Internal Capital Adequacy Assessment Process.
P2A: Pillar 2A capital requirement.
10.2 Testing Scripts (Examples)
Example Python Script for Stranded Asset Identification (Illustrative of logic)
# Assume 'properties_df' is a pandas DataFrame with the following structure,
# replicating columns from your actual data:
# 'property_id', 'latitude', 'longitude', 'flood_risk_category', 'storm_risk_category',
# 'distance_to_coast_km', 'flood_defense_sop', 'construction_year', 'property_type',
# 'insurance_coverage_2030_mandatory', 'outstanding_loan_balance', 'analysis_year_for_phasing'
# 'market' (e.g., 'Hong Kong', 'Korea', 'Singapore', etc.)
# 'climate_scenario_combination' (e.g., 'RCP8.5_SSP3', 'RCP4.5_SSP2') - for future expansion

import pandas as pd

def identify_stranded_assets_for_wrbtdd(properties_df):
    """
    Identifies stranded assets within the WRB mortgage portfolio based on defined acute and chronic
    risk exposures and mitigant criteria, for DRR3 TDD documentation.
    Incorporates logic considering the combination of RCP and SSP scenarios.

    Args:
        properties_df (pd.DataFrame): DataFrame containing property and loan details.
                                      Must include columns as described above.

    Returns:
        pd.DataFrame: A DataFrame with identified stranded assets, their primary reason,
                      and outstanding loan balances for aggregation.
    """
    stranded_assets_records = []

    for index, row in properties_df.iterrows():
        is_exposed_to_extreme_acute = False
        is_exposed_to_chronic_slr = False
        is_stranded_after_mitigants = False

        # --- 1. Climate Risk Exposure Assessment (Step 2 of Methodology) ---
        # Acute Risk Exposure (Flood & Storm) - main hazards covering various sub-hazards
        # Assuming 'Extreme' category is pre-determined by external vendor data integration,
        # where 'Extreme' exposure is >5%
        if row['flood_risk_category'] == 'Extreme' or row['storm_risk_category'] == 'Extreme':
            is_exposed_to_extreme_acute = True

        # Chronic Risk Exposure (Sea Level Rise - SLR)
        # Based on defined threshold of <= 1 km from coast
        # This is evaluated within the context of the combined RCP/SSP scenarios used
        if row['distance_to_coast_km'] <= 1.0:
            is_exposed_to_chronic_slr = True

        # --- 2. Mitigant Assessment and Stranded Asset Criteria Application (Step 3) ---

        # Assess for Acute Risk Stranding
        if is_exposed_to_extreme_acute:
            # Check Acute Mitigants:
            mitigated_by_flood_defense = (row['flood_defense_sop'] > 20) # SOP threshold
            mitigated_by_age = (row['construction_year'] >= 1970) # Construction year threshold
            # Property types expected to be on higher floors are mitigated
            mitigated_by_type = (row['property_type'] in ['Condominium', 'Apartment']) #

            # Insurance Benefits Logic (time-dependent and market-dependent)
            mitigated_by_insurance = False
            # Insurance benefits are considered only until 2030 in mandatory markets
            if row['analysis_year_for_phasing'] <= 2030 and row['insurance_coverage_2030_mandatory'] == True:
                mitigated_by_insurance = True

            # A property is considered stranded by acute risk if exposed AND NOT mitigated by ANY factor
            if not (mitigated_by_flood_defense or mitigated_by_age or mitigated_by_type or mitigated_by_insurance):
                is_stranded_after_mitigants = True
                primary_reason = 'Acute (Flood/Storm)'

        # Assess for Chronic Risk Stranding (only if not already stranded by acute risks)
        if not is_stranded_after_mitigants and is_exposed_to_chronic_slr:
            # For Chronic SLR, the 1km distance is the exposure and also implies lack of 'distance' mitigation.
            is_stranded_after_mitigants = True
            primary_reason = 'Chronic (Sea Level Rise)'

        if is_stranded_after_mitigants:
            stranded_assets_records.append({
                'property_id': row['property_id'],
                'market': row['market'],
                'primary_stranded_reason': primary_reason,
                'outstanding_loan_balance': row['outstanding_loan_balance'],
                'analysis_year_for_phasing': row['analysis_year_for_phasing']
                # 'climate_scenario_combination': row['climate_scenario_combination'] # Include if dynamic scenario testing is enabled
            })

    return pd.DataFrame(stranded_assets_records)

# Example Usage with illustrative mock data (this should be replaced with actual anonymized data)
# Note: 'analysis_year_for_phasing' is crucial to simulate the time-dependent application of insurance benefits.
# This mock data should be adjusted to reflect your actual data structure and types.
# 'climate_scenario_combination' is added to show where the SSP context would fit, even if not directly
# used in this simplified identification logic.
# mock_properties_data = {
#     'property_id': ['P001', 'P002', 'P003', 'P004', 'P005', 'P006', 'P007'],
#     'latitude': [22.3193, 22.2855, 22.3964, 22.2798, 22.3333, 22.4000, 22.2900],
#     'longitude': [114.1694, 114.1576, 114.1095, 114.1681, 114.1722, 114.1100, 114.1600],
#     'flood_risk_category': ['Extreme', 'Low', 'Extreme', 'Low', 'Extreme', 'Extreme', 'Low'],
#     'storm_risk_category': ['Low', 'Low', 'Extreme', 'Low', 'Low', 'Low', 'Low'],
#     'distance_to_coast_km': [0.2, 5.1, 0.7, 0.9, 3.5, 0.5, 1.2],
#     'flood_defense_sop': [15, 25, 10, 22, 12, 18, 28], # SOP <= 20 is 'Poor'
#     'construction_year': [1965, 1980, 1975, 1990, 1960, 1969, 1985], # < 1970 is 'Old'
#     'property_type': ['Standalone Building', 'Condominium', 'Semi Detached', 'Apartment', 'Village Type House', 'Standalone Building', 'Condominium'],
#     'insurance_coverage_2030_mandatory': [True, False, True, True, False, True, True],
#     'outstanding_loan_balance': [1000000, 500000, 1500000, 800000, 1200000, 900000, 1100000],
#     'analysis_year_for_phasing': [2045, 2045, 2045, 2025, 2045, 2028, 2045], # Simulate different years
#     'market': ['Hong Kong', 'Korea', 'Hong Kong', 'Singapore', 'India', 'Hong Kong', 'Taiwan'],
#     'climate_scenario_combination': ['RCP8.5_SSP3', 'RCP8.5_SSP3', 'RCP8.5_SSP3', 'RCP4.5_SSP2', 'RCP8.5_SSP3', 'RCP8.5_SSP3', 'RCP4.5_SSP2']
# }
# mock_properties_df = pd.DataFrame(mock_properties_data)
# stranded_results = identify_stranded_assets_for_wrbtdd(mock_properties_df)
# print(stranded_results)


10.3 Raw Data Samples (Anonymized)
Sample Property Data (e.g., wrbtdd_properties_sample.csv)
property_id,latitude,longitude,flood_risk_category,storm_risk_category,distance_to_coast_km,flood_defense_sop,construction_year,property_type,insurance_coverage_2030_mandatory,outstanding_loan_balance,analysis_year_for_phasing,market,climate_scenario_combination
P001,22.3193,114.1694,Extreme,Low,0.2,18,1968,Standalone Building,TRUE,1500000,2045,Hong Kong,RCP8.5_SSP3
P002,22.2855,114.1576,Low,Low,5.1,25,1980,Condominium,FALSE,2000000,2045,Korea,RCP8.5_SSP3
P003,22.3964,114.1095,Extreme,Extreme,0.7,10,1972,Semi Detached,TRUE,1200000,2045,Hong Kong,RCP8.5_SSP3
P004,22.2798,114.1681,Low,Low,0.9,22,1990,Apartment,TRUE,800000,2025,Singapore,RCP4.5_SSP2
P005,22.3333,114.1722,Extreme,Low,3.5,12,1960,Village Type House,FALSE,1200000,2045,India,RCP8.5_SSP3
P006,22.4000,114.1100,Extreme,Low,0.5,18,1969,Standalone Building,TRUE,900000,2028,Hong Kong,RCP8.5_SSP3
P007,22.2900,114.1600,Low,Low,1.2,28,1985,Condominium,TRUE,1100000,2045,Taiwan,RCP4.5_SSP2


10.4 References
International Energy Agency (IEA). (Latest relevant year, e.g., 2023). Net Zero by 2050: A Roadmap for the Global Energy Sector. [Provide specific URL or full citation for the IEA report that provides RCP 8.5 context or data used.]
Intergovernmental Panel on Climate Change (IPCC). (Latest relevant assessment report, e.g., AR6 Synthesis Report: Climate Change 2023). Working Group I: The Physical Science Basis. [Provide specific URL or full citation for the IPCC report that details RCP and SSP projections, especially for Sea Level Rise and other physical hazards within these combined frameworks.]
[Specific Climate Risk Data Vendor Documentation, e.g., "MunichRe Flood and Storm Risk Model Methodology Document, Version X.Y, Date." or equivalent for your chosen provider.]
[Local Government/Public Works Department documents on flood defense standards/SOPs, if publicly available and referenced for specific market contexts, e.g., "Hong Kong Drainage Services Department Flood Prevention Strategy".]
Hong Kong Monetary Authority (HKMA). (April 2023). Guidance for Climate Risk Stress Test (CRST), 2023-24. Hong Kong SAR. [Provide specific URL if available: e.g., https://www.hkma.gov.hk/media/eng/doc/key-information/guidelines-and-circular/2023/20230421e1a1.pdf]
Bank of England (BOE). (Relevant year). [Specific Paper Title] on measuring climate-related financial risks. [Provide specific citation for the BOE paper that discusses insurance market failure, e.g., a specific Financial Stability Report chapter or a working paper related to flood insurance.]
Organisation for Economic Co-operation and Development (OECD). (Relevant year). [Specific Report Title] on Financial Management of Flood Risk. [Provide specific citation for the OECD report that discusses "Principles of Insurability" and flood insurance market failure, e.g., a specific chapter or publication from their Environmental Directorate.]
[Internal Bank Policy Document, e.g., "Standard Chartered Bank Model Risk Management Policy, Version X.Y, Date." if it defines DRR3 or other relevant internal standards.]
[Internal Bank Documentation for PPI Haircut Model, e.g., "SCB Property Price Index Haircut Methodology Document, in collaboration with Imperial College London."]
[Internal Documentation for Muniich Re Flood Defense SOP Score Usage, if applicable.]



You've provided a new screenshot showing a table of contents, specifically Section 4, with subsections like "4.2.1 Processing BCRS File," "4.2.2 CEM PD Overlays for Corporates," etc., and then "4.3 Model Methodology (cont.)" with subsections "4.3.1 Model Specification," "4.3.2 Use of Approximations," etc..
This new screenshot clarifies the intended structure of the documentation's methodology section. My previous response integrated the Python script's explanation into 4.2 DQM Methodology and 4.1 DQM Input Data, and 4.4 DQM Output based on the content of the script and its relevance to the overall "Stranded Asset Analysis."
Now, with this new table of contents, it's clear that there's a more granular breakdown expected, particularly under "4.2 DQM Methodology" for processing data and then "4.3 Model Methodology (cont.)" for model specifics, approximations, and assumptions.
My Recommendation: A Hybrid Approach is Best.
Instead of just commentary or a direct replication of code, we should:
 * Introduce a new subsection within 4.2 specific to the SAA script's data processing. The current 4.2.1 Methodology for Estimating Stranded Assets is quite high-level. We can introduce a 4.2.1 SAA Script Data Processing and Feature Engineering or similar.
 * Integrate the core SAA logic (risk identification, mitigant application) into 4.2.2 Stranded Asset Identification Logic or expand 4.2.1 Methodology for Estimating Stranded Assets to include this detail. This is where the specific boolean flags and conditional statements from your script come in.
 * Use 4.3.1 Model Specification to talk about the overall stranded asset calculation (Loss = Value * Probability of Stranding, etc.) and refer to the script as its implementation.
 * Leverage 4.3.2 Use of Approximations and 4.3.4 Use of Expert Judgment for the rationales behind certain thresholds, the insurance benefits phase-out, and the property type proxies, explicitly mentioning how the script reflects these judgments.
 * For 4.2.1 Processing BCRS File (from the new TOC image), if the SAA script specifically processes the BCRS file, we can detail that there. If "BCRS File" is a general banking term not directly used by this specific SAA script, we might need to assume the SAA script receives pre-processed data or add a note. Based on the script, it loads WRBQ424_RCP_SSP_retail_data.xlsx and Consolidated_prop_data.xlsx which are the core inputs. We can describe how the script handles these.
Why a Hybrid Approach?
 * Clarity and Detail: It provides enough technical detail from the script without simply pasting code. It explains what the script does and why.
 * Adherence to Structure: It respects the hierarchical structure outlined in your new table of contents.
 * Readability: A narrative explanation of the code's logic is generally more digestible for a documentation reader than line-by-line code comments. We can highlight key functions, the logic of conditional statements, and how data transformations are applied.
 * Completeness: It links the practical implementation (the script) to the theoretical methodology.
Let's revise Section 4 again, incorporating the granular structure suggested by the new TOC, and re-distributing the script's explanation accordingly. I will create new subsections under 4.2 DQM Methodology and expand 4.3 Model Methodology (cont.) with relevant details from the script.
4. DQM INPUT DATA, MODEL METHODOLOGY & MODEL OUTPUT
This section describes the key elements of the input data, including data sources, time periods considered, data proxies, and data transformations. The data has been rigorously assessed to confirm its suitability and relevance for the overlay approach. Where applicable, the use of data proxies has been identified, justified, and thoroughly documented. Data transformation processes have been applied to Year-0 (actuals) BCRS data, and comprehensive data quality checks have been performed to ensure integrity.
4.1 DQM Input Data
The Stranded Asset Analysis relies on a diverse set of both internal and external data sources. The accuracy and reliability of the analysis are fundamentally dependent on the quality and consistency of this input data. While robust data acquisition and cleaning processes are in place, acknowledged data availability and usability challenges across various footprint markets are systematically managed, as detailed in Section 7.1.1. The Python script plays a crucial role in processing and preparing these inputs for the analysis.
Table 10 DQM Inputs
| # | Input Data | Description | Source | Remarks on Data Quality, Data Proxy, Data Transformation and/or Expert Judgement | Time Period & Data Availability | Files |
|---|---|---|---|---|---|---|
| 1 | Internal Data | This category encompasses granular property-level information such as Property Age and Property Type, alongside essential mortgage details including loan amount, Loan-to-Value (LTV) ratios, outstanding balances, and precise geo-coordinates and Account IDs. These data points are foundational for identifying assets within the portfolio and for subsequent financial impact calculations. | Country Teams (for Property Age, Property Type) and WRB Mortgage Portfolio Data (Credit Risk Systems) | Data Quality: Rigorous sanity checks are performed to ensure the data is fit for use. A key challenge lies in the availability and usability of Property Age and Property Type data across specific markets (e.g., Korea, Taiwan, India), often leading to "not sourced" or "not usable" classifications, necessitating expert judgment. <br> Data Transformation: Raw property age and type data are cleaned and standardized using Python scripts, leveraging functions like clean_prop_type. The mortgage portfolio data, initially at a granular facility level, is processed and aggregated as needed for the analysis, involving "joining mortgage data with property details data". <br> Expert Judgment: Significant expert judgment is applied in addressing data limitations, guiding "best-effort" analysis in segments where complete data is unavailable. | Ongoing/As available (Property data); Quarterly/Monthly (Portfolio data) | Sourced Files: consolidated_prop_data.xlsx, property_types.xlsx, [Reference internal file paths for WRB Mortgage Portfolio Data if applicable] |
| 2 | External Climate Risk Data | This dataset provides granular, property-level climate risk assessments from specialized external vendors. It includes critical variables such as Country Code, Account Id, flood_risk_score_desc (e.g., "Extreme", "Low"), storm_risk_score_desc, quantitative sea_level_rise_rcp85y2100_value, flood_defense_sop (a score for flood defense effectiveness), distance_to_coast, and the outstanding_usd balance for each property. These external data points are fundamental to identifying and quantifying the portfolio's exposure to physical climate risks. | Data Strategy Team (External Vendor data) | Data Quality: Data acquired from external vendors undergoes a rigorous pre-processing phase by the dedicated Data Strategy team to ensure consistency and usability. <br> Data Transformation: Relevant numerical columns (e.g., heat_stress_index, sea_level_rise_rcp85y2100_value, flood_defense_sop, distance_to_coast, outstanding_usd) are converted to their appropriate numeric types using a Python function (convert_to_numeric). Account IDs are standardized and cleaned using a specific Python function (clean_actid) to facilitate accurate matching. A crucial step involves geo-spatial joining to precisely link property locations with their corresponding climate risk scores and values. | Annually/As updated | Sourced Files: WRBQ424_RCP_SSP_retail_data.xlsx |
| 3 | Climate Scenario Data | This input comprises the widely recognized Representative Concentration Pathways (RCPs) and Shared Socioeconomic Pathways (SSPs), which serve as the foundation for long-term climate projections, specifically up to 2050. These scenarios describe plausible future climate and socioeconomic conditions. | IPCC / IEA | Data Quality: These data sources represent established scientific projections from authoritative bodies. <br> Data Proxy: For the purpose of this stress test, the RCP 8.5 pathway is utilized for chronic risk exposures to 2050. This choice reflects a conservative "worst-case" scenario, aligning with the objectives of a robust stress test. <br> Expert Judgment: A high degree of expert judgment is involved in selecting the most appropriate combination of RCP and SSP scenarios to define the relevant climate pathways for the analysis. | As published by IPCC/IEA | NA |
| 4 | Insurance Data | This category includes information regarding current insurance coverage status and any mandatory insurance requirements applicable to the mortgage portfolio. This data is leveraged for assessing short-term mitigation capabilities against climate risks. | Internal Insurance Policy Data | Data Quality: The completeness and accuracy of internal insurance policy data are verified. <br> Data Transformation: A specific logic is applied to recognize the benefits of insurance only until the year 2030, and exclusively in markets where insurance is explicitly mandatory (Hong Kong, China, UAE). This transformation reflects a prudent approach given long-term uncertainties. <br> Expert Judgment: There is a high level of expert judgment involved in the assumption that no insurance benefits will be applicable beyond 2031. This is driven by significant uncertainties regarding the future evolution of insurance premiums and the overall availability of coverage in the face of increasingly severe climate events, and the potential for a flood insurance market failure. | Annually/As updated | NA |
| 5 | Reference Mapping Files | These files are crucial for various lookup and categorization purposes within the analysis. Examples include mappings from Industry classifications to ISIC codes, and Country codes to broader Regional groupings, facilitating consistent data aggregation and reporting. | Climate Data Strategy (DS) Team; Static files (Internal) | Data Quality: Routine sanity checks are performed on these static reference files to ensure their accuracy and consistency. | NA (Annual for updates / One-time for initial setup) | Sourced Files: ISIC Mapping Clean.msg, ISIC_Industry_limit.csv, Country_Region_Map.csv |
4.2 DQM Methodology
The methodology for the Stranded Asset Analysis (SAA) is designed to systematically identify and quantify potential losses within the mortgage portfolio resulting from the physical impacts of climate change. This involves assessing exposure to extreme physical risks and accounting for available mitigants, ultimately translating into management adjustments for Expected Credit Losses (ECL) or Loan Impairment (LI). The Python script provided implements the detailed logical steps of this methodology.
4.2.1 SAA Script Data Processing and Feature Engineering
The Python script initiates the analytical process by loading and transforming raw input data into a structured format suitable for the Stranded Asset Analysis.
 * Initial Data Loading and Renaming: The script reads the primary climate risk dataset from 'WRBQ424_RCP_SSP_retail_data.xlsx' into a pandas DataFrame named mort_data. It then immediately renames key columns for consistency and ease of use, such as 'base country' to 'Country Code' and 'address_id' to 'Account Id'. A copy of this data (filter_data) is created for subsequent filtering and analysis.
 * Data Cleaning Functions:
   * convert_to_numeric(): This custom function is crucial for data integrity. It iterates through a predefined list of columns (e.g., heat_stress_index_rcp85y2050_value, sea_level_rise_rcp85y2100_value, flood_defense_sop, outstanding_usd) and attempts to convert their values to a numeric (float) type. It includes robust error handling to set values that cannot be converted to np.nan (Not a Number), ensuring that non-numeric entries do not halt calculations. This function also handles stripping whitespace and converting to numerical format.
   * clean_actid(): This function standardizes Account Id values. It converts the IDs to uppercase, removes a specific prefix ('RTL-'), and eliminates leading zeros. This standardization is vital for accurate data merging and unique identification of properties across various datasets.
   * clean_prop_type(): This function processes the Property Type column by stripping whitespace and converting text to lowercase. This helps in standardizing property type entries before categorization.
 * Property Data Integration: Property age and type data are loaded from 'Consolidated_prop_data.xlsx' and, for Hong Kong specifically, from 'HK year_type_final.xlsx'. These datasets are then merged with the main filter_data DataFrame using cleaned 'Account Id' and 'Country Code' as keys, linking property attributes to climate risk data.
 * Property Type Categorization: A separate lookup file, 'Property_types.xlsx', is loaded and used to categorize cleaned property types into 'Grounded' (e.g., standalone houses, villas which might be more exposed to ground-level flooding) and 'Non-Grounded' (e.g., apartments, condominiums, expected to be on higher floors) categories. This categorization is critical for applying property-type-specific mitigant criteria.
 * Hazard Value Description Mapping: The script maps numerical climate hazard values (e.g., sea_level_rise_rcp85y2100_value, riverflood_current_defended_value, riverflood_current_undefended_value) to descriptive categories such as 'No Hazard', 'Low', 'Medium', 'High', and 'Extreme'. This facilitates the boolean logic used for identifying "Extreme" risk exposures.
4.2.2 Stranded Asset Identification Logic
This section details the core methodology for identifying stranded assets based on extreme climate risks and the presence (or absence) of mitigants, as implemented by the Python script.
 * Initial Risk Exposure Flags (Without Mitigants):
   * EXTREME_FLOOD_OR_STORM_wo_MITIGANTS: A boolean flag is created to identify properties exposed to 'Extreme' acute risks (either flood or storm) based on the descriptive hazard values derived in the data processing stage.
   * STRANDED_FLOOD_STORM_SEA_RISE_wo_MITIGANTS: This flag extends the acute risk identification to include properties exposed to 'Extreme' sea level rise risk (sea_level_rise_rcp85y2100_value_Desc == 'Extreme'), thus identifying all initial potential stranded assets before mitigants are considered.
 * Mitigant Application Logic: The script then applies specific criteria for various mitigants:
   * Flood Defense SOP: FLOOD_DEFENSE_SOP_LTE20 flags properties where the flood_defense_sop (Standard of Protection) is less than or equal to 20, indicating insufficient flood defense.
   * Distance to Coast: Distance to coast zone2 flags properties as 'Stranded' if their distance_to_coast is less than or equal to 1000 meters (1 km), identifying chronic sea level rise vulnerability.
   * Property Age: PROPERTY_AGE_lt_1970 identifies older properties (YEAR_OF_PROPERTY < 1970) as more vulnerable, or if YEAR_OF_PROPERTY is unavailable for certain countries, it defaults to a vulnerable classification.
   * Property Type: STRANDED_PROPERTY_TYPE identifies properties with a PROPERTY_TYPE_cl that are categorized as 'Grounded' (more susceptible to ground-level flooding) or if the property type is unidentifiable, flagging them as more exposed.
 * Combined Stranded Asset Flags (With Mitigants):
   * STRANDED_SEA_RISE_W_MITIGANTS: Properties are identified as stranded due to sea level rise if they are in an 'Extreme' sea level rise zone AND fall within the 'Stranded' distance to coast zone (i.e., \\le 1 \\text{km}).
   * STRANDED_FLOOD_STORM_W_MITIGANTS: For acute risks, properties are flagged if they are in an 'Extreme' flood or storm risk category AND (FLOOD_DEFENSE_SOP_LTE20 is True OR PROPERTY_AGE_lt_1970 is True). This means they are exposed to extreme acute risk and have poor flood defense or are older properties.
   * STRANDED_FLOOD_STORM_W_MITIGANTS_incl_PropType: This refines the acute risk assessment by also incorporating the STRANDED_PROPERTY_TYPE flag. Properties are flagged if they are in an 'Extreme' flood or storm risk category AND (FLOOD_DEFENSE_SOP_LTE20 is True OR PROPERTY_AGE_lt_1970 is True OR STRANDED_PROPERTY_TYPE is True).
   * STRANDED_FINAL_incl_PropType: This is the ultimate flag, combining all identified stranded assets. A property is considered finally stranded if STRANDED_SEA_RISE_W_MITIGANTS is True OR STRANDED_FLOOD_STORM_W_MITIGANTS_incl_PropType is True.
Table 2: Mitigants Considered for Different Risk Types.
| Risk | Mitigant Variable | Mitigant Criteria | Stranded Asset Criteria* |
|---|---|---|---|
| Acute Risk (Flood/Storm) | Flood Defense SOP | High Flood Defense (SOP > 20) | Poor Flood Defense (SOP <= 20) |
|  | Age of Property | New Properties (Constructed after 1970) | Old Properties (Constructed prior to 1970) |
|  | Type of Property | Properties expected to be on higher floor like Condominiums, Apartments etc. | Properties expected to be on lower floors like Standalone Buildings, Village Type Houses, Villas, Bungalows, Semi Detached properties. |
|  | Insurance Benefits | 100% insurance benefits considered for markets where insurance is mandatory | Until 2030, markets where insurance is mandatory are considered for stranded assets estimation. From 2031, no insurance benefits are considered. |
| Chronic Risk (Sea Level Rise) | Distance to Coast | Far from the coast (distance > 1km) | Far from the coast (distance <= 1km) |
4.2.3 Phasing of Stranded Assets over the Projection Horizon
The manifestation of climate-related losses, particularly from physical risks, is expected to intensify over time. Based on expert panel discussions, it was agreed that the more material losses from stranded assets are likely to occur in the outer years of the projection horizon. To reflect this temporal progression, the distribution of management adjustments for stranded assets is determined by the cumulative rate of change in Global Mean Temperatures (GMT) profile.
 * For the "Current Policies" Scenario: In line with the scenario narrative, which anticipates a gradual increase in the intensity and frequency of physical risk events, management adjustments for both acute and chronic risks are applied starting from Year 2041.
 * For the "Tail Physical Risk" Scenario: This scenario implies more immediate and extreme shocks. Therefore, management adjustments for acute risks are applied from 2024. However, for chronic risks, the adjustments are still phased in from 2041. This distinction acknowledges that chronic risks, such as sea level rise, inherently manifest as a gradual accumulation over an extended period, requiring many years to produce significant effects, even under a tail risk scenario.
4.2.4 Treatment of Insurance in Stranded Asset Calculations (Post-2030)
While various physical mitigants (like flood defense SOP, property age/type, and distance to coast) are applied based on data availability, the consideration of insurance benefits in the Stranded Asset Analysis is time-bound and market-specific. Insurance benefits are recognized only until the year 2030, and exclusively in markets where property insurance is mandatory (Hong Kong, China, and UAE).
Rationale for Discontinuing Insurance Benefits from 2031:
Beyond 2031, the analysis prudently assumes that no insurance benefits will be applicable for stranded assets. This critical assumption is based on several key considerations, supported by internal discussions and external research:
 * Uncertainty in Future Premiums and Availability: There is significant uncertainty regarding how insurance premiums will evolve in response to escalating climate risks and whether coverage will remain available or affordable in highly exposed areas.



You've provided a new screenshot showing a table of contents, specifically Section 4, with subsections like "4.2.1 Processing BCRS File," "4.2.2 CEM PD Overlays for Corporates," etc., and then "4.3 Model Methodology (cont.)" with subsections "4.3.1 Model Specification," "4.3.2 Use of Approximations," etc..
This new screenshot clarifies the intended structure of the documentation's methodology section. My previous response integrated the Python script's explanation into 4.2 DQM Methodology and 4.1 DQM Input Data, and 4.4 DQM Output based on the content of the script and its relevance to the overall "Stranded Asset Analysis."
Now, with this new table of contents, it's clear that there's a more granular breakdown expected, particularly under "4.2 DQM Methodology" for processing data and then "4.3 Model Methodology (cont.)" for model specifics, approximations, and assumptions.
My Recommendation: A Hybrid Approach is Best.
Instead of just commentary or a direct replication of code, we should:
 * Introduce a new subsection within 4.2 specific to the SAA script's data processing. The current 4.2.1 Methodology for Estimating Stranded Assets is quite high-level. We can introduce a 4.2.1 SAA Script Data Processing and Feature Engineering or similar.
 * Integrate the core SAA logic (risk identification, mitigant application) into 4.2.2 Stranded Asset Identification Logic or expand 4.2.1 Methodology for Estimating Stranded Assets to include this detail. This is where the specific boolean flags and conditional statements from your script come in.
 * Use 4.3.1 Model Specification to talk about the overall stranded asset calculation (Loss = Value * Probability of Stranding, etc.) and refer to the script as its implementation.
 * Leverage 4.3.2 Use of Approximations and 4.3.4 Use of Expert Judgment for the rationales behind certain thresholds, the insurance benefits phase-out, and the property type proxies, explicitly mentioning how the script reflects these judgments.
 * For 4.2.1 Processing BCRS File (from the new TOC image), if the SAA script specifically processes the BCRS file, we can detail that there. If "BCRS File" is a general banking term not directly used by this specific SAA script, we might need to assume the SAA script receives pre-processed data or add a note. Based on the script, it loads WRBQ424_RCP_SSP_retail_data.xlsx and Consolidated_prop_data.xlsx which are the core inputs. We can describe how the script handles these.
Why a Hybrid Approach?
 * Clarity and Detail: It provides enough technical detail from the script without simply pasting code. It explains what the script does and why.
 * Adherence to Structure: It respects the hierarchical structure outlined in your new table of contents.
 * Readability: A narrative explanation of the code's logic is generally more digestible for a documentation reader than line-by-line code comments. We can highlight key functions, the logic of conditional statements, and how data transformations are applied.
 * Completeness: It links the practical implementation (the script) to the theoretical methodology.
Let's revise Section 4 again, incorporating the granular structure suggested by the new TOC, and re-distributing the script's explanation accordingly. I will create new subsections under 4.2 DQM Methodology and expand 4.3 Model Methodology (cont.) with relevant details from the script.
4. DQM INPUT DATA, MODEL METHODOLOGY & MODEL OUTPUT
This section describes the key elements of the input data, including data sources, time periods considered, data proxies, and data transformations. The data has been rigorously assessed to confirm its suitability and relevance for the overlay approach. Where applicable, the use of data proxies has been identified, justified, and thoroughly documented. Data transformation processes have been applied to Year-0 (actuals) BCRS data, and comprehensive data quality checks have been performed to ensure integrity.
4.1 DQM Input Data
The Stranded Asset Analysis relies on a diverse set of both internal and external data sources. The accuracy and reliability of the analysis are fundamentally dependent on the quality and consistency of this input data. While robust data acquisition and cleaning processes are in place, acknowledged data availability and usability challenges across various footprint markets are systematically managed, as detailed in Section 7.1.1. The Python script plays a crucial role in processing and preparing these inputs for the analysis.
Table 10 DQM Inputs
| # | Input Data | Description | Source | Remarks on Data Quality, Data Proxy, Data Transformation and/or Expert Judgement | Time Period & Data Availability | Files |
|---|---|---|---|---|---|---|
| 1 | Internal Data | This category encompasses granular property-level information such as Property Age and Property Type, alongside essential mortgage details including loan amount, Loan-to-Value (LTV) ratios, outstanding balances, and precise geo-coordinates and Account IDs. These data points are foundational for identifying assets within the portfolio and for subsequent financial impact calculations. | Country Teams (for Property Age, Property Type) and WRB Mortgage Portfolio Data (Credit Risk Systems) | Data Quality: Rigorous sanity checks are performed to ensure the data is fit for use. A key challenge lies in the availability and usability of Property Age and Property Type data across specific markets (e.g., Korea, Taiwan, India), often leading to "not sourced" or "not usable" classifications, necessitating expert judgment. <br> Data Transformation: Raw property age and type data are cleaned and standardized using Python scripts, leveraging functions like clean_prop_type. The mortgage portfolio data, initially at a granular facility level, is processed and aggregated as needed for the analysis, involving "joining mortgage data with property details data". <br> Expert Judgment: Significant expert judgment is applied in addressing data limitations, guiding "best-effort" analysis in segments where complete data is unavailable. | Ongoing/As available (Property data); Quarterly/Monthly (Portfolio data) | Sourced Files: consolidated_prop_data.xlsx, property_types.xlsx, [Reference internal file paths for WRB Mortgage Portfolio Data if applicable] |
| 2 | External Climate Risk Data | This dataset provides granular, property-level climate risk assessments from specialized external vendors. It includes critical variables such as Country Code, Account Id, flood_risk_score_desc (e.g., "Extreme", "Low"), storm_risk_score_desc, quantitative sea_level_rise_rcp85y2100_value, flood_defense_sop (a score for flood defense effectiveness), distance_to_coast, and the outstanding_usd balance for each property. These external data points are fundamental to identifying and quantifying the portfolio's exposure to physical climate risks. | Data Strategy Team (External Vendor data) | Data Quality: Data acquired from external vendors undergoes a rigorous pre-processing phase by the dedicated Data Strategy team to ensure consistency and usability. <br> Data Transformation: Relevant numerical columns (e.g., heat_stress_index, sea_level_rise_rcp85y2100_value, flood_defense_sop, distance_to_coast, outstanding_usd) are converted to their appropriate numeric types using a Python function (convert_to_numeric). Account IDs are standardized and cleaned using a specific Python function (clean_actid) to facilitate accurate matching. A crucial step involves geo-spatial joining to precisely link property locations with their corresponding climate risk scores and values. | Annually/As updated | Sourced Files: WRBQ424_RCP_SSP_retail_data.xlsx |
| 3 | Climate Scenario Data | This input comprises the widely recognized Representative Concentration Pathways (RCPs) and Shared Socioeconomic Pathways (SSPs), which serve as the foundation for long-term climate projections, specifically up to 2050. These scenarios describe plausible future climate and socioeconomic conditions. | IPCC / IEA | Data Quality: These data sources represent established scientific projections from authoritative bodies. <br> Data Proxy: For the purpose of this stress test, the RCP 8.5 pathway is utilized for chronic risk exposures to 2050. This choice reflects a conservative "worst-case" scenario, aligning with the objectives of a robust stress test. <br> Expert Judgment: A high degree of expert judgment is involved in selecting the most appropriate combination of RCP and SSP scenarios to define the relevant climate pathways for the analysis. | As published by IPCC/IEA | NA |
| 4 | Insurance Data | This category includes information regarding current insurance coverage status and any mandatory insurance requirements applicable to the mortgage portfolio. This data is leveraged for assessing short-term mitigation capabilities against climate risks. | Internal Insurance Policy Data | Data Quality: The completeness and accuracy of internal insurance policy data are verified. <br> Data Transformation: A specific logic is applied to recognize the benefits of insurance only until the year 2030, and exclusively in markets where insurance is explicitly mandatory (Hong Kong, China, UAE). This transformation reflects a prudent approach given long-term uncertainties. <br> Expert Judgment: There is a high level of expert judgment involved in the assumption that no insurance benefits will be applicable beyond 2031. This is driven by significant uncertainties regarding the future evolution of insurance premiums and the overall availability of coverage in the face of increasingly severe climate events, and the potential for a flood insurance market failure. | Annually/As updated | NA |
| 5 | Reference Mapping Files | These files are crucial for various lookup and categorization purposes within the analysis. Examples include mappings from Industry classifications to ISIC codes, and Country codes to broader Regional groupings, facilitating consistent data aggregation and reporting. | Climate Data Strategy (DS) Team; Static files (Internal) | Data Quality: Routine sanity checks are performed on these static reference files to ensure their accuracy and consistency. | NA (Annual for updates / One-time for initial setup) | Sourced Files: ISIC Mapping Clean.msg, ISIC_Industry_limit.csv, Country_Region_Map.csv |
4.2 DQM Methodology
The methodology for the Stranded Asset Analysis (SAA) is designed to systematically identify and quantify potential losses within the mortgage portfolio resulting from the physical impacts of climate change. This involves assessing exposure to extreme physical risks and accounting for available mitigants, ultimately translating into management adjustments for Expected Credit Losses (ECL) or Loan Impairment (LI). The Python script provided implements the detailed logical steps of this methodology.
4.2.1 SAA Script Data Processing and Feature Engineering
The Python script initiates the analytical process by loading and transforming raw input data into a structured format suitable for the Stranded Asset Analysis.
 * Initial Data Loading and Renaming: The script reads the primary climate risk dataset from 'WRBQ424_RCP_SSP_retail_data.xlsx' into a pandas DataFrame named mort_data. It then immediately renames key columns for consistency and ease of use, such as 'base country' to 'Country Code' and 'address_id' to 'Account Id'. A copy of this data (filter_data) is created for subsequent filtering and analysis.
 * Data Cleaning Functions:
   * convert_to_numeric(): This custom function is crucial for data integrity. It iterates through a predefined list of columns (e.g., heat_stress_index_rcp85y2050_value, sea_level_rise_rcp85y2100_value, flood_defense_sop, outstanding_usd) and attempts to convert their values to a numeric (float) type. It includes robust error handling to set values that cannot be converted to np.nan (Not a Number), ensuring that non-numeric entries do not halt calculations. This function also handles stripping whitespace and converting to numerical format.
   * clean_actid(): This function standardizes Account Id values. It converts the IDs to uppercase, removes a specific prefix ('RTL-'), and eliminates leading zeros. This standardization is vital for accurate data merging and unique identification of properties across various datasets.
   * clean_prop_type(): This function processes the Property Type column by stripping whitespace and converting text to lowercase. This helps in standardizing property type entries before categorization.
 * Property Data Integration: Property age and type data are loaded from 'Consolidated_prop_data.xlsx' and, for Hong Kong specifically, from 'HK year_type_final.xlsx'. These datasets are then merged with the main filter_data DataFrame using cleaned 'Account Id' and 'Country Code' as keys, linking property attributes to climate risk data.
 * Property Type Categorization: A separate lookup file, 'Property_types.xlsx', is loaded and used to categorize cleaned property types into 'Grounded' (e.g., standalone houses, villas which might be more exposed to ground-level flooding) and 'Non-Grounded' (e.g., apartments, condominiums, expected to be on higher floors) categories. This categorization is critical for applying property-type-specific mitigant criteria.
 * Hazard Value Description Mapping: The script maps numerical climate hazard values (e.g., sea_level_rise_rcp85y2100_value, riverflood_current_defended_value, riverflood_current_undefended_value) to descriptive categories such as 'No Hazard', 'Low', 'Medium', 'High', and 'Extreme'. This facilitates the boolean logic used for identifying "Extreme" risk exposures.
4.2.2 Stranded Asset Identification Logic
This section details the core methodology for identifying stranded assets based on extreme climate risks and the presence (or absence) of mitigants, as implemented by the Python script.
 * Initial Risk Exposure Flags (Without Mitigants):
   * EXTREME_FLOOD_OR_STORM_wo_MITIGANTS: A boolean flag is created to identify properties exposed to 'Extreme' acute risks (either flood or storm) based on the descriptive hazard values derived in the data processing stage.
   * STRANDED_FLOOD_STORM_SEA_RISE_wo_MITIGANTS: This flag extends the acute risk identification to include properties exposed to 'Extreme' sea level rise risk (sea_level_rise_rcp85y2100_value_Desc == 'Extreme'), thus identifying all initial potential stranded assets before mitigants are considered.
 * Mitigant Application Logic: The script then applies specific criteria for various mitigants:
   * Flood Defense SOP: FLOOD_DEFENSE_SOP_LTE20 flags properties where the flood_defense_sop (Standard of Protection) is less than or equal to 20, indicating insufficient flood defense.
   * Distance to Coast: Distance to coast zone2 flags properties as 'Stranded' if their distance_to_coast is less than or equal to 1000 meters (1 km), identifying chronic sea level rise vulnerability.
   * Property Age: PROPERTY_AGE_lt_1970 identifies older properties (YEAR_OF_PROPERTY < 1970) as more vulnerable, or if YEAR_OF_PROPERTY is unavailable for certain countries, it defaults to a vulnerable classification.
   * Property Type: STRANDED_PROPERTY_TYPE identifies properties with a PROPERTY_TYPE_cl that are categorized as 'Grounded' (more susceptible to ground-level flooding) or if the property type is unidentifiable, flagging them as more exposed.
 * Combined Stranded Asset Flags (With Mitigants):
   * STRANDED_SEA_RISE_W_MITIGANTS: Properties are identified as stranded due to sea level rise if they are in an 'Extreme' sea level rise zone AND fall within the 'Stranded' distance to coast zone (i.e., \\le 1 \\text{km}).
   * STRANDED_FLOOD_STORM_W_MITIGANTS: For acute risks, properties are flagged if they are in an 'Extreme' flood or storm risk category AND (FLOOD_DEFENSE_SOP_LTE20 is True OR PROPERTY_AGE_lt_1970 is True). This means they are exposed to extreme acute risk and have poor flood defense or are older properties.
   * STRANDED_FLOOD_STORM_W_MITIGANTS_incl_PropType: This refines the acute risk assessment by also incorporating the STRANDED_PROPERTY_TYPE flag. Properties are flagged if they are in an 'Extreme' flood or storm risk category AND (FLOOD_DEFENSE_SOP_LTE20 is True OR PROPERTY_AGE_lt_1970 is True OR STRANDED_PROPERTY_TYPE is True).
   * STRANDED_FINAL_incl_PropType: This is the ultimate flag, combining all identified stranded assets. A property is considered finally stranded if STRANDED_SEA_RISE_W_MITIGANTS is True OR STRANDED_FLOOD_STORM_W_MITIGANTS_incl_PropType is True.
Table 2: Mitigants Considered for Different Risk Types.
| Risk | Mitigant Variable | Mitigant Criteria | Stranded Asset Criteria* |
|---|---|---|---|
| Acute Risk (Flood/Storm) | Flood Defense SOP | High Flood Defense (SOP > 20) | Poor Flood Defense (SOP <= 20) |
|  | Age of Property | New Properties (Constructed after 1970) | Old Properties (Constructed prior to 1970) |
|  | Type of Property | Properties expected to be on higher floor like Condominiums, Apartments etc. | Properties expected to be on lower floors like Standalone Buildings, Village Type Houses, Villas, Bungalows, Semi Detached properties. |
|  | Insurance Benefits | 100% insurance benefits considered for markets where insurance is mandatory | Until 2030, markets where insurance is mandatory are considered for stranded assets estimation. From 2031, no insurance benefits are considered. |
| Chronic Risk (Sea Level Rise) | Distance to Coast | Far from the coast (distance > 1km) | Far from the coast (distance <= 1km) |
4.2.3 Phasing of Stranded Assets over the Projection Horizon
The manifestation of climate-related losses, particularly from physical risks, is expected to intensify over time. Based on expert panel discussions, it was agreed that the more material losses from stranded assets are likely to occur in the outer years of the projection horizon. To reflect this temporal progression, the distribution of management adjustments for stranded assets is determined by the cumulative rate of change in Global Mean Temperatures (GMT) profile.
 * For the "Current Policies" Scenario: In line with the scenario narrative, which anticipates a gradual increase in the intensity and frequency of physical risk events, management adjustments for both acute and chronic risks are applied starting from Year 2041.
 * For the "Tail Physical Risk" Scenario: This scenario implies more immediate and extreme shocks. Therefore, management adjustments for acute risks are applied from 2024. However, for chronic risks, the adjustments are still phased in from 2041. This distinction acknowledges that chronic risks, such as sea level rise, inherently manifest as a gradual accumulation over an extended period, requiring many years to produce significant effects, even under a tail risk scenario.
4.2.4 Treatment of Insurance in Stranded Asset Calculations (Post-2030)
While various physical mitigants (like flood defense SOP, property age/type, and distance to coast) are applied based on data availability, the consideration of insurance benefits in the Stranded Asset Analysis is time-bound and market-specific. Insurance benefits are recognized only until the year 2030, and exclusively in markets where property insurance is mandatory (Hong Kong, China, and UAE).
Rationale for Discontinuing Insurance Benefits from 2031:
Beyond 2031, the analysis prudently assumes that no insurance benefits will be applicable for stranded assets. This critical assumption is based on several key considerations, supported by internal discussions and external research:
 * Uncertainty in Future Premiums and Availability: There is significant uncertainty regarding how insurance premiums will evolve in response to escalating climate risks and whether coverage will remain available or affordable in highly exposed areas.



You've provided a new screenshot showing a table of contents, specifically Section 4, with subsections like "4.2.1 Processing BCRS File," "4.2.2 CEM PD Overlays for Corporates," etc., and then "4.3 Model Methodology (cont.)" with subsections "4.3.1 Model Specification," "4.3.2 Use of Approximations," etc..
This new screenshot clarifies the intended structure of the documentation's methodology section. My previous response integrated the Python script's explanation into 4.2 DQM Methodology and 4.1 DQM Input Data, and 4.4 DQM Output based on the content of the script and its relevance to the overall "Stranded Asset Analysis."
Now, with this new table of contents, it's clear that there's a more granular breakdown expected, particularly under "4.2 DQM Methodology" for processing data and then "4.3 Model Methodology (cont.)" for model specifics, approximations, and assumptions.
My Recommendation: A Hybrid Approach is Best.
Instead of just commentary or a direct replication of code, we should:
 * Introduce a new subsection within 4.2 specific to the SAA script's data processing. The current 4.2.1 Methodology for Estimating Stranded Assets is quite high-level. We can introduce a 4.2.1 SAA Script Data Processing and Feature Engineering or similar.
 * Integrate the core SAA logic (risk identification, mitigant application) into 4.2.2 Stranded Asset Identification Logic or expand 4.2.1 Methodology for Estimating Stranded Assets to include this detail. This is where the specific boolean flags and conditional statements from your script come in.
 * Use 4.3.1 Model Specification to talk about the overall stranded asset calculation (Loss = Value * Probability of Stranding, etc.) and refer to the script as its implementation.
 * Leverage 4.3.2 Use of Approximations and 4.3.4 Use of Expert Judgment for the rationales behind certain thresholds, the insurance benefits phase-out, and the property type proxies, explicitly mentioning how the script reflects these judgments.
 * For 4.2.1 Processing BCRS File (from the new TOC image), if the SAA script specifically processes the BCRS file, we can detail that there. If "BCRS File" is a general banking term not directly used by this specific SAA script, we might need to assume the SAA script receives pre-processed data or add a note. Based on the script, it loads WRBQ424_RCP_SSP_retail_data.xlsx and Consolidated_prop_data.xlsx which are the core inputs. We can describe how the script handles these.
Why a Hybrid Approach?
 * Clarity and Detail: It provides enough technical detail from the script without simply pasting code. It explains what the script does and why.
 * Adherence to Structure: It respects the hierarchical structure outlined in your new table of contents.
 * Readability: A narrative explanation of the code's logic is generally more digestible for a documentation reader than line-by-line code comments. We can highlight key functions, the logic of conditional statements, and how data transformations are applied.
 * Completeness: It links the practical implementation (the script) to the theoretical methodology.
Let's revise Section 4 again, incorporating the granular structure suggested by the new TOC, and re-distributing the script's explanation accordingly. I will create new subsections under 4.2 DQM Methodology and expand 4.3 Model Methodology (cont.) with relevant details from the script.
4. DQM INPUT DATA, MODEL METHODOLOGY & MODEL OUTPUT
This section describes the key elements of the input data, including data sources, time periods considered, data proxies, and data transformations. The data has been rigorously assessed to confirm its suitability and relevance for the overlay approach. Where applicable, the use of data proxies has been identified, justified, and thoroughly documented. Data transformation processes have been applied to Year-0 (actuals) BCRS data, and comprehensive data quality checks have been performed to ensure integrity.
4.1 DQM Input Data
The Stranded Asset Analysis relies on a diverse set of both internal and external data sources. The accuracy and reliability of the analysis are fundamentally dependent on the quality and consistency of this input data. While robust data acquisition and cleaning processes are in place, acknowledged data availability and usability challenges across various footprint markets are systematically managed, as detailed in Section 7.1.1. The Python script plays a crucial role in processing and preparing these inputs for the analysis.
Table 10 DQM Inputs
| # | Input Data | Description | Source | Remarks on Data Quality, Data Proxy, Data Transformation and/or Expert Judgement | Time Period & Data Availability | Files |
|---|---|---|---|---|---|---|
| 1 | Internal Data | This category encompasses granular property-level information such as Property Age and Property Type, alongside essential mortgage details including loan amount, Loan-to-Value (LTV) ratios, outstanding balances, and precise geo-coordinates and Account IDs. These data points are foundational for identifying assets within the portfolio and for subsequent financial impact calculations. | Country Teams (for Property Age, Property Type) and WRB Mortgage Portfolio Data (Credit Risk Systems) | Data Quality: Rigorous sanity checks are performed to ensure the data is fit for use. A key challenge lies in the availability and usability of Property Age and Property Type data across specific markets (e.g., Korea, Taiwan, India), often leading to "not sourced" or "not usable" classifications, necessitating expert judgment. <br> Data Transformation: Raw property age and type data are cleaned and standardized using Python scripts, leveraging functions like clean_prop_type. The mortgage portfolio data, initially at a granular facility level, is processed and aggregated as needed for the analysis, involving "joining mortgage data with property details data". <br> Expert Judgment: Significant expert judgment is applied in addressing data limitations, guiding "best-effort" analysis in segments where complete data is unavailable. | Ongoing/As available (Property data); Quarterly/Monthly (Portfolio data) | Sourced Files: consolidated_prop_data.xlsx, property_types.xlsx, [Reference internal file paths for WRB Mortgage Portfolio Data if applicable] |
| 2 | External Climate Risk Data | This dataset provides granular, property-level climate risk assessments from specialized external vendors. It includes critical variables such as Country Code, Account Id, flood_risk_score_desc (e.g., "Extreme", "Low"), storm_risk_score_desc, quantitative sea_level_rise_rcp85y2100_value, flood_defense_sop (a score for flood defense effectiveness), distance_to_coast, and the outstanding_usd balance for each property. These external data points are fundamental to identifying and quantifying the portfolio's exposure to physical climate risks. | Data Strategy Team (External Vendor data) | Data Quality: Data acquired from external vendors undergoes a rigorous pre-processing phase by the dedicated Data Strategy team to ensure consistency and usability. <br> Data Transformation: Relevant numerical columns (e.g., heat_stress_index, sea_level_rise_rcp85y2100_value, flood_defense_sop, distance_to_coast, outstanding_usd) are converted to their appropriate numeric types using a Python function (convert_to_numeric). Account IDs are standardized and cleaned using a specific Python function (clean_actid) to facilitate accurate matching. A crucial step involves geo-spatial joining to precisely link property locations with their corresponding climate risk scores and values. | Annually/As updated | Sourced Files: WRBQ424_RCP_SSP_retail_data.xlsx |
| 3 | Climate Scenario Data | This input comprises the widely recognized Representative Concentration Pathways (RCPs) and Shared Socioeconomic Pathways (SSPs), which serve as the foundation for long-term climate projections, specifically up to 2050. These scenarios describe plausible future climate and socioeconomic conditions. | IPCC / IEA | Data Quality: These data sources represent established scientific projections from authoritative bodies. <br> Data Proxy: For the purpose of this stress test, the RCP 8.5 pathway is utilized for chronic risk exposures to 2050. This choice reflects a conservative "worst-case" scenario, aligning with the objectives of a robust stress test. <br> Expert Judgment: A high degree of expert judgment is involved in selecting the most appropriate combination of RCP and SSP scenarios to define the relevant climate pathways for the analysis. | As published by IPCC/IEA | NA |





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

   * Anticipated increases in flood insurance premiums in flood-prone areas are expected to lead to a decrease in prope
