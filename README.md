Great. Here's an updated version tailored for Technical Development Document (TDD) or DRR3-level documentation standards. It includes:

Clean narrative structure

Traceable references to the data source

Connection to how the phasing logic impacts your modelling (e.g. LGD, stage transitions)

Ready-to-submit formatting



---

4.2.3 Phasing of Stranded Asset Impacts over the Projection Horizon

The manifestation of climate-related losses, particularly from physical risks, is expected to escalate over time. This aligns with the broader scientific understanding that rising global temperatures will drive more frequent and severe climate hazards—such as extreme heat, inland flooding, and cyclones—which in turn increase the vulnerability and impairment risk of exposed assets.

Based on expert panel discussions, it was agreed that the more material losses from stranded assets—especially those driven by physical climate risks—are likely to occur in the latter years of the projection horizon. This assumption was incorporated into the loss modeling approach to better reflect the expected timing of climate-related stress events.

To phase these losses over time, we use a temperature-linked progression that mirrors the trajectory of global warming under a high-emissions pathway. Specifically, the distribution of losses is aligned with the cumulative rate of change in Global Mean Temperature (GMT).

The reference scenario used is from the Network for Greening the Financial System (NGFS) climate scenario database:

Model: REMIND-MAgPIE 3.2-4.6

Scenario: Current Policies

Climate Model Emulator: MAGICC7.5.3

Percentile: 50th (Median)

Region: World


This scenario broadly reflects the assumptions of a business-as-usual pathway comparable to RCP 8.5, where limited policy intervention results in steadily increasing warming throughout the century.

The projected GMT increases over the modelling horizon are as follows:

Year	2020	2025	2030	2035	2040	2045	2050

GMT (K)	1.23	1.35	1.38	1.48	1.61	1.73	1.96
Cumulative Change Share	2%	7%	14%	20%	26%	32%	
Cumulative Fraction of Total	2%	9%	22%	42%	68%	100%	


This temperature-linked phasing curve is used to allocate stranded asset losses across the projection years. In particular:

Valuation adjustments for vulnerable or impaired exposures (e.g. LGD or stage 2/3 transitions) are scaled using the cumulative GMT share.

The assumption is that climate-related credit impairments will not be linear but instead back-loaded, with increasing concentrations of loss appearing in later years, consistent with physical climate risk progression.


> Footnote: The NGFS climate scenario data used for this exercise was sourced from the NGFS IIASA Scenario Explorer (downloaded prior to July 2025). The full scenario path is based on AR6 climate diagnostics using MAGICC7.5.3 median global temperature outputs.




---

Let me know if you also want to:

Integrate this logic into a LGD calculation or staging threshold

Add a chart or visual of the temperature path + phasing weights

Customize for submission in a governance pack or review memo


Ready when you are.

