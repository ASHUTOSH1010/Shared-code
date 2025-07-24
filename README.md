Thank you for providing the content of "Section 7." This is very helpful as it provides the explicit details on those limitations and assumptions.
I can confirm that the core points from your provided "Section 7" regarding Data Availability and Usability and Scenario Specifications were already largely captured in the table I generated previously. However, your explicit content allows for more precision and completeness, particularly by adding the Mortgage Geo-coordinates limitation and refining the details on the scenario phasing.
Here is the updated and more precise table incorporating all the details from your "Section 7" images:
Table: DQM Assumptions & Limitations: Stranded Asset Analysis (SAA)
Assumptions/Limitation
Description
Materiality/Impact
Mitigation
A/L
Conservative Climate Scenario Selection (RCP 8.5 Phasing)
The analysis utilizes the RCP 8.5 pathway for long-term chronic risks (to 2050). For the "Tail Physical Risk" scenario, acute risk impacts are applied from 2024, while chronic risk impacts are applied from 2041.
Leads to more stressed losses and a conservative estimate of stranded assets, particularly under the Tail Physical Risk scenario due to earlier recognition of acute impacts.
This choice aligns with the objective of a robust stress test, ensuring a prudent assessment of tail risks. A high degree of expert judgment is applied in selecting and combining RCP and SSP scenarios to define relevant climate pathways.
A
Expert-Defined Mitigant Thresholds
Specific thresholds for various mitigants (e.g., Flood Defense SOP \le 20, Property Age pre-1970, Distance to Coast \le 1 \text{km}) are determined based on expert judgment.
Directly influences the number of properties classified as "stranded" and the magnitude of estimated losses.
Thresholds are established through expert consensus and are clearly defined within the model's methodology, reflecting best available knowledge.
A
Complete Phase-out of Insurance Benefits Post-2030
Insurance benefits are assumed to cease entirely from 2031 onwards for all markets, and are only considered for mandatory insurance markets (HK, China, UAE) up to 2030.
Significantly increases projected losses after 2030 as a critical financial mitigant is removed. Impacts potential ECL/LI adjustments by an estimated USD30m benefit up to 2030.
This assumption is driven by regulatory guidance (HKMA CRST), internal discussions, and external research anticipating future insurance market failures, affordability issues, and availability challenges in climate-vulnerable areas. It represents a prudent and conservative stance on long-term insurability.
A
Use of Property Type as Elevation Proxy
Due to the unavailability of direct data on property floor levels, property type (e.g., 'Grounded' vs. 'Non-Grounded' categories like standalone houses vs. apartments) is used as a proxy for a property's susceptibility to ground-level flooding.
May not precisely reflect the actual flood exposure of every individual property, potentially leading to misclassification in some cases.
This is a pragmatic approximation given data limitations. The categorization relies on reasonable assumptions about the typical construction and location of different property types.
A
Simplified Loss Calculation (Full Value Erosion)
The model assumes a complete erosion of value for properties identified as stranded assets, with losses directly equaling the outstanding balance of these assets.
Might overestimate actual losses by not accounting for potential partial damages, residual value, or recovery rates post-event.
This approach simplifies complex damage modeling for stress testing purposes and provides a conservative estimate of potential maximum losses.
A
Limited Data Availability & Usability for Property Attributes
There are significant challenges with the availability and usability of granular Property Age data (not sourced/usable for Korea, Taiwan, India) and Property Type data (not sourced/usable for Korea, Singapore, Taiwan, India) across various markets.
Requires 'best-effort' analysis and default assumptions in affected segments, which could impact the precision of stranded asset identification.
Expert judgment is applied to guide the 'best-effort' analysis in segments with data gaps. The Python script's logic handles missing data by defaulting to a vulnerable classification when necessary. Active engagement with country teams is ongoing for future data capture improvement.
L
Limited Mortgage Geo-coordinates Availability
Mortgage geo-coordinates are not fully available for a few markets.
For affected markets, country-level averages are used for climate risk mapping, which may not accurately reflect property-specific risk.
Applied expert judgment and 'best-effort' analysis by using country-level averages as a proxy where granular data is unavailable. Engagement with country teams is ongoing for future data capture improvement.
L




Thank you for providing the content of "Section 7." This is very helpful as it provides the explicit details on those limitations and assumptions.
I can confirm that the core points from your provided "Section 7" regarding Data Availability and Usability and Scenario Specifications were already largely captured in the table I generated previously. However, your explicit content allows for more precision and completeness, particularly by adding the Mortgage Geo-coordinates limitation and refining the details on the scenario phasing.
Here is the updated and more precise table incorporating all the details from your "Section 7" images:
Table: DQM Assumptions & Limitations: Stranded Asset Analysis (SAA)
Assumptions/Limitation
Description
Materiality/Impact
Mitigation
A/L
Conservative Climate Scenario Selection (RCP 8.5 Phasing)
The analysis utilizes the RCP 8.5 pathway for long-term chronic risks (to 2050). For the "Tail Physical Risk" scenario, acute risk impacts are applied from 2024, while chronic risk impacts are applied from 2041.
Leads to more stressed losses and a conservative estimate of stranded assets, particularly under the Tail Physical Risk scenario due to earlier recognition of acute impacts.
This choice aligns with the objective of a robust stress test, ensuring a prudent assessment of tail risks. A high degree of expert judgment is applied in selecting and combining RCP and SSP scenarios to define relevant climate pathways.
A
Expert-Defined Mitigant Thresholds
Specific thresholds for various mitigants (e.g., Flood Defense SOP \le 20, Property Age pre-1970, Distance to Coast \le 1 \text{km}) are determined based on expert judgment.
Directly influences the number of properties classified as "stranded" and the magnitude of estimated losses.
Thresholds are established through expert consensus and are clearly defined within the model's methodology, reflecting best available knowledge.
A
Complete Phase-out of Insurance Benefits Post-2030
Insurance benefits are assumed to cease entirely from 2031 onwards for all markets, and are only considered for mandatory insurance markets (HK, China, UAE) up to 2030.
Significantly increases projected losses after 2030 as a critical financial mitigant is removed. Impacts potential ECL/LI adjustments by an estimated USD30m benefit up to 2030.
This assumption is driven by regulatory guidance (HKMA CRST), internal discussions, and external research anticipating future insurance market failures, affordability issues, and availability challenges in climate-vulnerable areas. It represents a prudent and conservative stance on long-term insurability.
A
Use of Property Type as Elevation Proxy
Due to the unavailability of direct data on property floor levels, property type (e.g., 'Grounded' vs. 'Non-Grounded' categories like standalone houses vs. apartments) is used as a proxy for a property's susceptibility to ground-level flooding.
May not precisely reflect the actual flood exposure of every individual property, potentially leading to misclassification in some cases.
This is a pragmatic approximation given data limitations. The categorization relies on reasonable assumptions about the typical construction and location of different property types.
A
Simplified Loss Calculation (Full Value Erosion)
The model assumes a complete erosion of value for properties identified as stranded assets, with losses directly equaling the outstanding balance of these assets.
Might overestimate actual losses by not accounting for potential partial damages, residual value, or recovery rates post-event.
This approach simplifies complex damage modeling for stress testing purposes and provides a conservative estimate of potential maximum losses.
A
Limited Data Availability & Usability for Property Attributes
There are significant challenges with the availability and usability of granular Property Age data (not sourced/usable for Korea, Taiwan, India) and Property Type data (not sourced/usable for Korea, Singapore, Taiwan, India) across various markets.
Requires 'best-effort' analysis and default assumptions in affected segments, which could impact the precision of stranded asset identification.
Expert judgment is applied to guide the 'best-effort' analysis in segments with data gaps. The Python script's logic handles missing data by defaulting to a vulnerable classification when necessary. Active engagement with country teams is ongoing for future data capture improvement.
L
Limited Mortgage Geo-coordinates Availability
Mortgage geo-coordinates are not fully available for a few markets.
For affected markets, country-level averages are used for climate risk mapping, which may not accurately reflect property-specific risk.
Applied expert judgment and 'best-effort' analysis by using country-level averages as a proxy where granular data is unavailable. Engagement with country teams is ongoing for future data capture improvement.
L


