4. DQM INPUT DATA, MODEL METHODOLOGY & MODEL OUTPUT
This section describes the key elements of the input data, including data sources, time periods considered, data proxies, and data transformations. The data has been rigorously assessed to confirm its suitability and relevance for the overlay approach. Where applicable, the use of data proxies has been identified, justified, and thoroughly documented. Data transformation processes have been applied to Year-0 (actuals) BCRS data, and comprehensive data quality checks have been performed to ensure integrity.
4.1 DQM Input Data
The Stranded Asset Analysis relies on a diverse set of both internal and external data sources. The accuracy and reliability of the analysis are fundamentally dependent on the quality and consistency of this input data. While robust data acquisition and cleaning processes are in place, acknowledged data availability and usability challenges across various footprint markets are systematically managed, as detailed in Section 7.1.1. The Python script plays a crucial role in processing and preparing these inputs for the analysis.
Table 10 DQM Inputs
| # | Input Data | Description | Source | Remarks on Data Quality, Data Proxy, Data Transformation and/or Expert Judgement | Time Period & Data Availability | Files |
|---|---|---|---|---|---|---|
| 1 | Internal Data | This category encompasses granular property-level information such as Property Age and Property Type, alongside essential mortgage details including loan amount, Loan-to-Value (LTV) ratios, outstanding balances, and precise geo-coordinates and Account IDs. These data points are foundational for identifying assets within the portfolio and for subsequent financial impact calculations. | Country Teams (for Property Age, Property Type) and WRB Mortgage Portfolio Data (Credit Risk Systems) | Data Quality: Rigorous sanity checks are performed to ensure the data is fit for use. A key challenge lies in the availability and usability of Property Age and Property Type data across specific markets (e.g., Korea, Taiwan, India), often leading to "not sourced" or "not usable" classifications, necessitating expert judgment. <br> Data Transformation: Raw property age and type data are cleaned and standardized using Python scripts. The mortgage portfolio data, initially at a granular facility level, is processed and aggregated as needed for the analysis, involving "joining mortgage data with property details data". <br> Expert Judgment: Significant expert judgment is applied in addressing data limitations, guiding "best-effort" analysis in segments where complete data is unavailable. | Ongoing/As available (Property data); Quarterly/Monthly (Portfolio data) | Sourced Files: consolidated_prop_data.xlsx, property_types.xlsx, [Reference internal file paths for WRB Mortgage Portfolio Data if applicable] |
| 2 | External Climate Risk Data | This dataset provides granular, property-level climate risk assessments from specialized external vendors. It includes critical variables such as Country Code, Account Id, flood_risk_score_desc (e.g., "Extreme", "Low"), storm_risk_score_desc, quantitative sea_level_rise_rcp85y2100_value, flood_defense_sop (a score for flood defense effectiveness), distance_to_coast, and the outstanding_usd balance for each property. These external data points are fundamental to identifying and quantifying the portfolio's exposure to physical climate risks. | Data Strategy Team (External Vendor data) | Data Quality: Data acquired from external vendors undergoes a rigorous pre-processing phase by the dedicated Data Strategy team to ensure consistency and usability. <br> Data Transformation: Relevant numerical columns (e.g., heat stress index, sea level rise values, flood defense scores, distance to coast, outstanding balances) are converted to their appropriate numeric types. Account IDs are standardized and cleaned to facilitate accurate matching. A crucial step involves geo-spatial joining to precisely link property locations with their corresponding climate risk scores and values. | Annually/As updated | Sourced Files: WRBQ424_RCP_SSP_retail_data.xlsx |
| 3 | Climate Scenario Data | This input comprises the widely recognized Representative Concentration Pathways (RCPs) and Shared Socioeconomic Pathways (SSPs), which serve as the foundation for long-term climate projections, specifically up to 2050. These scenarios describe plausible future climate and socioeconomic conditions. | IPCC / IEA | Data Quality: These data sources represent established scientific projections from authoritative bodies. <br> Data Proxy: For the purpose of this stress test, the RCP 8.5 pathway is utilized for chronic risk exposures to 2050. This choice reflects a conservative "worst-case" scenario, aligning with the objectives of a robust stress test. <br> Expert Judgment: A high degree of expert judgment is involved in selecting the most appropriate combination of RCP and SSP scenarios to define the relevant climate pathways for the analysis. | As published by IPCC/IEA | NA |
| 4 | Insurance Data | This category includes information regarding current insurance coverage status and any mandatory insurance requirements applicable to the mortgage portfolio. This data is leveraged for assessing short-term mitigation capabilities against climate risks. | Internal Insurance Policy Data | Data Quality: The completeness and accuracy of internal insurance policy data are verified. <br> Data Transformation: A specific logic is applied to recognize the benefits of insurance only until the year 2030, and exclusively in markets where insurance is explicitly mandatory (Hong Kong, China, UAE). This transformation reflects a prudent approach given long-term uncertainties. <br> Expert Judgment: There is a high level of expert judgment involved in the assumption that no insurance benefits will be applicable beyond 2031. This is driven by significant uncertainties regarding the future evolution of insurance premiums and the overall availability of coverage in the face of increasingly severe climate events, and the potential for a flood insurance market failure. | Annually/As updated | NA |
| 5 | Reference Mapping Files | These files are crucial for various lookup and categorization purposes within the analysis. Examples include mappings from Industry classifications to ISIC codes, and Country codes to broader Regional groupings, facilitating consistent data aggregation and reporting. | Climate Data Strategy (DS) Team; Static files (Internal) | Data Quality: Routine sanity checks are performed on these static reference files to ensure their accuracy and consistency. | NA (Annual for updates / One-time for initial setup) | Sourced Files: ISIC Mapping Clean.msg, ISIC_Industry_limit.csv, Country_Region_Map.csv |
4.2 DQM Methodology
The Stranded Asset analysis is a methodology used for estimating physical risk arising from acute (flood/storm) and chronic (sea level rise, heat stress, etc.) climate hazards that results in a loss or economic obsolescence for the Bank's residential mortgage portfolio for Retail clients. The methodology provides an estimate of the impact of physical climate risk, which translates to a management adjustment to ECL / LI for the Bank's residential mortgage portfolio. The management adjustment is determined by identifying properties that are exposed to physical risk and applying different physical mitigants.
At its core, the methodology of Stranded Asset Analysis involves:
 * Identifying properties that are highly exposed to physical risks (both acute, such as floods and storms, and chronic, such as sea level rise).
 * Applying relevant physical mitigants (e.g., Flood Defense Standard of Protection (SOP), Property Age, Property Type, and Distance to Coast) to refine the identification of truly stranded assets.
 * A critical assumption of this methodology is that the exposure in these identified stranded properties is considered to be a total loss (i.e., Probability of Default (P) = 100% and Loss Given Default (LGD) = 100%).
4.2.1 SAA Methodology Steps
The process for identifying stranded assets and quantifying their impact follows a structured approach:
 * Initial Risk Identification: Properties are first assessed for their exposure to extreme physical climate hazards. This involves evaluating data points related to acute risks (e.g., flood risk scores, storm risk scores) and chronic risks (e.g., sea level rise values). Properties are flagged if they exhibit "Extreme" levels of these hazards.
 * Mitigant Assessment and Application: Once initial exposure is identified, various physical mitigants are considered. These mitigants act as filters to determine if a property, despite being exposed to an extreme hazard, possesses characteristics that reduce its vulnerability. Key mitigants include:
   * Flood Defense Capability: Assessing the effectiveness of existing flood defenses.
   * Distance to Coast: Evaluating proximity to coastal areas, particularly for sea level rise risk.
   * Property Age: Considering the age of the property, as older properties may be less resilient to climate impacts.
   * Property Type: Categorizing properties (e.g., as 'Grounded' or 'Non-Grounded') to infer susceptibility based on typical construction and elevation.
 * Final Stranded Asset Determination: A property is ultimately deemed "stranded" if it is exposed to an extreme physical risk AND its relevant mitigants are deemed insufficient or absent based on predefined criteria. This results in a final classification of properties that are considered to be at total loss.
Table 2: Mitigants Considered for Different Risk Types.
| Risk | Mitigant Variable | Mitigant Criteria | Stranded Asset Criteria* |
|---|---|---|---|
| Acute Risk (Flood/Storm) | Flood Defense SOP | High Flood Defense (SOP > 20) | Poor Flood Defense (SOP <= 20) |
|  | Age of Property | New Properties (Constructed after 1970) | Old Properties (Constructed prior to 1970) |
|  | Type of Property | Properties expected to be on higher floor like Condominiums, Apartments etc. | Properties expected to be on lower floors like Standalone Buildings, Village Type Houses, Villas, Bungalows, Semi Detached properties. |
|  | Insurance Benefits | 100% insurance benefits considered for markets where insurance is mandatory | Until 2030, markets where insurance is mandatory are considered for stranded assets estimation. From 2031, no insurance benefits are considered. |
| Chronic Risk (Sea Level Rise) | Distance to Coast | Far from the coast (distance > 1km) | Far from the coast (distance <= 1km) |
4.2.2 Python Script Implementation
The Python script serves as the direct operationalization of the Stranded Asset Analysis methodology, translating the conceptual steps into executable data processing and logical operations.
 * Data Processing and Feature Engineering: The script begins by loading raw input data, performing essential data cleaning, standardization, and transformation. This includes:
   * Initial Data Loading and Preparation: Reading the primary climate risk dataset and renaming key identifiers for consistent use.
   * Numeric Data Conversion: Robustly converting all critical numerical columns (e.g., climate hazard indices, sea level rise values, flood defense scores, outstanding balances) to a numeric format, with error handling for non-numeric entries.
   * Identifier Standardization: Standardizing account identifiers (e.g., converting to uppercase, removing specific prefixes, eliminating leading zeros) to ensure accurate data merging across datasets.
   * Text Field Cleaning: Processing categorical text fields, such as property types, by stripping whitespace and converting text to lowercase for standardization.
   * Data Integration and Feature Creation: Merging property age and type data from separate sources with the main dataset to link property-specific attributes with climate risk information.
   * Property Type Categorization: Using a lookup file to categorize properties into 'Grounded' and 'Non-Grounded' types, which informs vulnerability assessments.
   * Hazard Value Description Mapping: Converting numerical climate hazard values (e.g., for sea level rise, river flood) into descriptive categories (e.g., 'No Hazard', 'Low', 'Medium', 'High', 'Extreme') to simplify the logical conditions for risk identification.
 * Stranded Asset Identification Logic Implementation: The script then implements the core identification logic through a series of conditional statements and flag creations:
   * Initial Risk Exposure Flags: Boolean flags are created to identify properties exposed to 'Extreme' acute risks (either flood or storm) and 'Extreme' sea level rise risks based on the descriptive hazard values.
   * Mitigant Application: The script applies the specific criteria for each mitigant. For example, it flags properties with a flood defense SOP below a certain threshold, properties within a critical distance to the coast, properties older than a specified year, or properties classified as 'Grounded' types.
   * Combined Stranded Asset Flags: Finally, the script combines the initial risk exposure flags with the mitigant criteria to derive a set of ultimate 'stranded' flags. A property is considered finally stranded if it meets the extreme risk criteria AND one or more relevant mitigants are insufficient (e.g., extreme acute risk AND (poor flood defense OR older property OR vulnerable property type) OR extreme chronic risk AND fails distance to coast criterion).
4.2.3 Phasing of Stranded Assets over the Projection Horizon
The manifestation of climate-related losses, particularly from physical risks, is expected to intensify over time. Based on expert panel discussions, it was agreed that the more material losses from stranded assets are likely to occur in the outer years of the projection horizon. To reflect this temporal progression, the distribution of management adjustments for stranded assets is determined by the cumulative rate of change in Global Mean Temperatures (GMT) profile.
 * For the "Current Policies" Scenario: In line with the scenario narrative, which anticipates a gradual increase in the intensity and frequency of physical risk events, management adjustments for both acute and chronic risks are applied starting from Year 2041.
 * For the "Tail Physical Risk" Scenario: This scenario implies more immediate and extreme shocks. Therefore, management adjustments for acute risks are applied from 2024. However, for chronic risks, the adjustments are still phased in from 2041. This distinction acknowledges that chronic risks, such as sea level rise, inherently manifest as a gradual accumulation over an long period, requiring many years to produce significant effects, even under a tail risk scenario.
4.2.4 Treatment of Insurance in Stranded Asset Calculations (Post-2030)
While various physical mitigants (like flood defense SOP, property age/type, and distance to coast) are applied based on data availability, the consideration of insurance benefits in the Stranded Asset Analysis is time-bound and market-specific. Insurance benefits are recognized only until the year 2030, and exclusively in markets where property insurance is mandatory (Hong Kong, China, and UAE).
Rationale for Discontinuing Insurance Benefits from 2031:
Beyond 2031, the analysis prudently assumes that no insurance benefits will be applicable for stranded assets. This critical assumption is based on several key considerations, supported by internal discussions and external research:
 * Uncertainty in Future Premiums and Availability: There is significant uncertainty regarding how insurance premiums will evolve in response to escalating climate risks and whether coverage will remain available or affordable in highly exposed areas.
   * Anticipated increases in flood insurance premiums in flood-prone areas are expected to lead to a decrease in property values.
 * Disruption of "Principles of Insurability": For areas highly prone to recurrent severe events (e.g., floods), the fundamental principles of insurability—which rely on quantifiable, diversified, and randomly occurring risks—may be disrupted. Catastrophe risks, particularly flood risks, often do not meet these criteria. This can lead to insurers charging premiums beyond the willingness-to-pay of homeowners, ultimately resulting in a "flood insurance market failure" in the private market.
   * The OECD report on Financial Management of Flood Risk specifically discusses the erosion of "Principles of Insurability" and the likelihood of flood insurance market failure.
   * Low demand for flood insurance can further reduce the size and diversity of the insurance pool, leading to higher prices.
   * Low levels of insurance coverage can pressure governments to provide compensation, potentially creating a "disaster syndrome" where government aid further reduces demand for insurance.
 * Property Becoming "Unmortgageable": A foreseen decrease in the availability of flood insurance in most flood-prone areas could lead to properties becoming difficult to mortgage or even "unmortgageable".
 * Regulatory Guidance (HKMA CRST 2023-24): For conservative purposes, banks are advised not to account for climate adaptation and mitigation measures (including insurance coverage) in quantifying impact under the Current Policies scenario. Renewal of existing insurance coverage after expiry should not be assumed.
   * Internal discussions during the HKMA CRST exercise reinforced the view that property insurance benefit will only be available for Year 1, as the policy will not be available at renewal, and physical risk impact is expected to exacerbate over time.
   * Furthermore, even for claims lodged in Year 1, it is conservative to assume that numerous insurance claims linked to an extreme physical risk event will take a few years to settle.
   * It is noted that Mortgage Indemnity Policy (MIP) may not cover loss linked to stranded properties, or damages may need to be repairable and costs coverable from property insurance proceeds.
Application in Scenarios:
Due to these considerations, insurance benefits are applied only in the Tail Physical Risk scenario up to 2030, where losses appear earlier. They are not applied in the "Current Policies" scenario, as stranded assets are projected to emerge only after 2041 under that less severe pathway, coinciding with the period of assumed insurance unavailability. This approach aligns with recommendations from Stress Test Forum (STF) members, who advocated for recognizing existing insurance benefits in the initial years. It is assumed that 100% of stranded asset losses are covered by insurance until 2030, with an estimated benefit of approximately USD30m.


Based on the content from both images, here is a well-written “Methodology – Stranded Assets Assessment” section for your Technical Development Document (TDD) in alignment with DRR3 expectations and your MST 2024 context:


---

Section 4 – Methodology: Stranded Assets Assessment

This section outlines the methodology used to estimate management adjustments related to stranded assets under physical climate risk scenarios. The focus is on properties exposed to “Extreme” risk levels under the RCP 8.5 climate pathway (2050 horizon) across flood, storm, and sea level rise hazards.


---

Definition of Stranded Assets

Stranded assets are defined as properties expected to become uninhabitable or unusable due to climate-induced physical risks. These assets are assumed to experience a complete erosion in property value, necessitating full credit loss recognition for associated mortgage exposures.


---

Rationale for Adjustments

Existing credit models, including PPI haircuts (e.g., from Munich Re), are applied at the portfolio level and may not capture tail-risk events such as total stranding of certain high-risk assets.

The stranded assets methodology introduces additional management overlays to explicitly account for climate tail scenarios that go beyond average portfolio impacts.

The adjustments are scoped strictly for current lending policies and tail physical climate scenarios.



---

Hazard Types Considered

Only the most material physical hazards are included in the stranded asset assessment:

Flood Risk: Includes flash flood, coastal flood, and storm surge.

Storm Risk: Includes tropical cyclone, extratropical cyclone, hail, tornado, and lightning.

Sea Level Rise: Chronic hazard with long-term uninhabitability potential.


Exclusions:

Heat stress is excluded as it is more relevant for transition risk rather than acute or chronic stranding.

Precipitation stress is not separately modeled, as it is already embedded in flood and storm projections.



---

Stranded Asset Criteria

Properties are classified as stranded if they meet any of the following physical or structural vulnerability criteria:

1. “Extreme” Risk Classification under RCP 8.5 scenario by 2050 (as per Munich Re risk scoring).


2. Property Age: Built before 1970 (older structures assumed to have lower resilience).


3. Building Type: Standalone bungalows, villas, semi-detached and village-type houses are included due to higher exposure and repair costs.


4. Flood Defense SOP < 20: Properties in areas with poor protection are included.


5. Distance to Coast < 1km: Used for chronic sea-level rise exposures.


6. No Insurance Coverage Post-2030: Insurance mitigants are only assumed to exist until 2030. Beyond this, full loss is assumed due to uncertainty around availability and affordability.




---

Scenario Inputs and Risk Mapping

Risk outputs are sourced from Munich Re’s models based on combined RCP 8.5 and SSP5-85 scenarios.

The models account for multiple hazard layers and apply geospatial overlays to determine “Extreme” risk classification.

Properties are tagged based on their geographic overlap with “Extreme” zones across applicable hazard layers.



---

Regional Exposure Insights (Key Results)

Exposure to “Extreme” Flood/Storm Risk:

TW (100%), HK (68%), CN (48%), IN (22%), KR (11%)


Exposure to “Extreme” Sea-Level Rise:

UAE (35%), CN (9%), HK (4%), IN (1%)

Other markets contribute <1% each




---

Let me know if you'd like this section as audio or if you want me to incorporate it into the full TDD document structure.
Thanks for the clarification! Based on that, I’ll revise the relevant sentence in the Methodology section to clearly reflect this year's change in scenario input.

🔄 Updated Line:

> “Risk outputs are sourced from Munich Re’s models, which in last year’s assessment used RCP 8.5 scenarios. For this year’s assessment, a combined RCP 8.5 and SSP5-8.5 scenario is used to generate climate risk scores, representing both physical hazard severity and socio-economic amplification.”



🧩 Full revised paragraph (from the Methodology section):

> Scenario Inputs and Risk Mapping
Risk outputs are sourced from Munich Re’s models. In the 2023 exercise, risk scores were based solely on the RCP 8.5 climate pathway. In the 2024 MST, climate scores are derived using a combination of RCP 8.5 and SSP5-8.5 scenarios. This enhanced approach captures both hazard severity and amplified socio-economic exposure, improving the accuracy of physical risk classification.
The models integrate multiple hazard layers and apply geospatial overlays to determine “Extreme” risk classifications for mortgage properties.



Let me know if you’d like a formal update of the full document, or a side note on where else this clarification might be needed.








Here is the refined and updated “Methodology – Stranded Assets Assessment” section, now incorporating:

The clarification about Munich Re hazard scores using RCP 8.5 last year, and RCP 8.5 + SSP5-8.5 this year

An expanded explanation of flood and storm sub-hazards



---

Section 4 – Methodology: Stranded Assets Assessment

This section outlines the methodology used to estimate management adjustments related to stranded assets under physical climate risk scenarios. The focus is on properties exposed to “Extreme” risk levels under the RCP 8.5 climate pathway (2050 horizon) across flood, storm, and sea level rise hazards.


---

Definition of Stranded Assets

Stranded assets are defined as properties expected to become uninhabitable or unusable due to climate-induced physical risks. These assets are assumed to experience a complete erosion in property value, necessitating full credit loss recognition for associated mortgage exposures.


---

Rationale for Adjustments

Existing credit models, including PPI haircuts (e.g., from Munich Re), are applied at the portfolio level and may not capture tail-risk events such as total stranding of certain high-risk assets.

The stranded assets methodology introduces additional management overlays to explicitly account for climate tail scenarios that go beyond average portfolio impacts.

The adjustments are scoped strictly for current lending policies and tail physical climate scenarios.



---

Hazard Types Considered

Only the most material physical hazards are included in the stranded asset assessment:

Flood Risk, including:

Pluvial flood (surface water flooding)

Fluvial flood (river flooding)

Coastal flood (including storm surge)

Flash flood (from intense rainfall)


Storm Risk, including:

Tropical cyclones

Extratropical cyclones

Hailstorms

Tornadoes

Lightning


Sea Level Rise (chronic hazard):
This represents long-term inundation risk due to permanent sea encroachment.


Exclusions:

Heat stress is excluded as it is more relevant for transition risk rather than asset stranding.

Precipitation stress is not separately modeled, as its effects are embedded within the flood and storm layers above.



---

Stranded Asset Criteria

Properties are classified as stranded if they meet any of the following physical or structural vulnerability criteria:

1. “Extreme” Risk Classification under climate stress scenarios by 2050


2. Property Age: Built before 1970 (assumed to be less resilient to damage)


3. Building Type: Bungalows, villas, semi-detached homes, or village-type structures (which face higher exposure and are costlier to reinstate)


4. Flood Defense SOP < 20: Indicates lack of adequate protection


5. Distance to Coast < 1km: Used as proxy for chronic sea-level risk


6. Insurance Cover Ceases Post-2030: No insurance assumed beyond 2030 due to expected unavailability and affordability




---

Scenario Inputs and Risk Mapping

Physical risk scores are sourced from Munich Re’s risk models, which classify geographic areas across multiple climate hazards.

In the 2023 MST, hazard classifications were based solely on the RCP 8.5 pathway.

For the 2024 MST, a combination of RCP 8.5 and SSP5-8.5 is used. This integrates not only physical hazard severity (RCP 8.5) but also socioeconomic vulnerability and exposure intensification (from SSP5-8.5), providing a more realistic representation of climate impact on properties.

Geospatial overlays of these “Extreme” risk zones are used to tag affected properties.



---

Regional Exposure Insights (Key Results)

Exposure to “Extreme” Flood/Storm Risk:

TW (100%), HK (68%), CN (48%), IN (22%), KR (11%)


Exposure to “Extreme” Sea-Level Rise:

UAE (35%), CN (9%), HK (4%), IN (1%)

All other markets <1%




---

Let me know if you'd like this section converted to audio or merged into the full TDD structure. I can also help format it for Word or PowerPoint depending on your reporting needs.

