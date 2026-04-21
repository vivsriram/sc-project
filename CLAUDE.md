# Project Context: Lock Maintenance Prioritization — U.S. Inland Waterway System

**Team A02:** Arend Colle, Sourav Dhar, Vivek Sriram  
**Course:** Operations and Supply Chain Analytics

## 1. Project Context & Background
The U.S. inland waterway system (specifically the Mississippi and Illinois rivers) is critical for transporting commodities, such as agricultural goods, at scale. However, aging lock infrastructure leads to unscheduled closures (stoppages). When locks unexpectedly stop traffic, grain transportation is disrupted, leading to increased spot barge freight rates. These system constraints were particularly stressed during the 2022 low-water crisis.

## 2. Main Goal
The primary objective of this project is to prioritize lock maintenance investments to maximize the **Dollar ROI** (Return on Investment). This means determining which locks require infrastructure repairs to avoid the most financial impact on freight costs caused by unscheduled stoppages. 

To achieve this, the project moves through three analytical stages:
- **Descriptive Analysis:** Understanding historic trends in lock stoppages (2021–2023) and observing seasonal rate premiums (e.g., harvest surges).
- **Predictive Analysis:** Isolating the causal impact of stoppage hours on freight rates controlling for broader macroeconomic or environmental factors (such as the 2022 drought) using linear regression (with year fixed effects).
- **Prescriptive Analysis:** Translating the percentage tariff rate hike per stoppage hour into a tangible monetary freight cost impact. The analysis evaluates what lock maintenance gets the highest return on investment under different budget scenarios (e.g., $50M, $100M, $200M).

## 3. Connecting the Dots (News / Events / Quantified Estimates)
One of the core evaluation criteria is the ability to tie the analysis to real-world events.
- **The 2022 Drought:** In late 2022, extreme low-water conditions severely constrained barge traffic. By controlling for year-fixed effects (the drought signal), this analysis successfully parses out how much of the rate shock was due globally to the drought vs. locally to *unscheduled infrastructure failures*.
- **Quantified Estimates:** Instead of generic severity scores, every hour of unscheduled stoppage is connected directly to "Estimated Freight Cost Avoided ($K)" based on weekly lock volumes and USDA Grain Transportation Report (GTR) base rates. 

## 4. Final Presentation & Visualizations Strategy
The slide deck must have a logical flow moving from the problem (closures & rate spikes), to the analysis (regression), to the solution (budget allocation), keeping within time limits and optimizing for the rubric.
- **Visuals:** The project currently leverages 9 pastel-colored charts. Time series graphs show the 2022 crisis overlap, tiered bar charts show priority ranking, and a scatter plot visualizes the Severity vs. Cost matrix. 
- **Flow:** 
  1. *Motivation*: The rising cost of freight during peak harvest and external conditions.
  2. *Descriptive*: The scale of the problem (hours lost to infrastructure vs. external causes).
  3. *Predictive / Rigor*: How we proved that stoppages *cause* higher rates, controlling for the 2022 low-water event. 
  4. *Prescriptive*: The budget ROI analysis and final lock maintenance recommendations.

## 5. Project Deliverables Checklist
- [ ] **Slide Deck:** Visual, focused presentation of the findings.
- [ ] **Recorded Presentation:** Clearly explaining the problem, models, and recommendations. Time limit tracking.
- [ ] **Data:** Final `lock_priority_ranking.csv`, `merged_weekly_data.csv`, and all generated Jupyter Notebook data pipelines.
- [ ] **GenAI Chat Histories:** Independent history sets recorded from each team member (Arend, Sourav, Vivek).
- [ ] **Peer Reviews:** Review records for two other groups' projects.

## 6. Grading Rubric Alignment (5-Point Scale)
When constructing the deck and recorded presentation, ensure these elements are front-and-center to score a `5`:
1. **Depth/Breadth of Content:** Show end-to-end data pipeline construction (USACE API + USDA GTR data matching).
2. **Quantitative Analysis (Rigor):** Emphasize the linear regression model with year fixed effects and volume-weighted ROI metrics.
3. **Visualization & Flow:** Point out the clear color-coding (e.g., Pastel Red for crisis/priority) and the intuitive progression from descriptive to prescriptive.
4. **Connecting the Dots:** Highlight the explicit calculation that separates drought-driven freight costs vs. lock infrastructure-driven freight costs. 
5. **Overall Presentation:** Pacing, clear motivation slides, and professional delivery.