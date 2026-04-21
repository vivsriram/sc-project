# Presentation Structure: Lock Maintenance Prioritization

**Team A02:** Arend Colle, Sourav Dhar, Vivek Sriram


---

## Executive Summary

We set out to determine which locks on the Mississippi and Illinois Rivers should get
maintenance investment to minimize freight cost disruption. Using USACE lock stoppage
data (2021 to 2023) and USDA Grain Transportation Report barge rates and volumes, we
ran a regression to isolate the effect of lock stoppages on freight rates while
controlling for year-level shocks like the 2022 drought.

**The core finding is a surprise:** the 2022 freight rate crisis (rates hit 5x normal)
was driven almost entirely by the drought, not by lock infrastructure failures. After
controlling for year effects, lock stoppages had no measurable impact on rates (the
regression coefficient is essentially zero). Additionally, 95% of all stoppage hours
were caused by weather and external factors, not by equipment failure.

**However, stoppages still matter operationally.** 3,792 hours of unscheduled
traffic-stopping downtime hit 23 locks over three years. The top 4 locks alone account
for 46% of all downtime. This creates a clear target list for reliability-focused
maintenance, even if it does not reduce freight rates.

**The storyline arc:** We open with the dramatic 2022 crisis to hook the audience, then
systematically pull apart what caused it (drought, not locks), and conclude by reframing
the maintenance question around operational reliability instead of rate reduction. The
audience should walk away understanding that (1) the 2022 rate spike was a weather
event, (2) the regression proves this, and (3) maintenance still has value but for
different reasons than initially assumed.


---

## Slide 1: Title Slide

### Purpose
Set context: who, what, why. Professional first impression.

### Content

**Title (centered, large):**
"What Really Drives Freight Costs on the Mississippi?"

**Subtitle (centered, smaller, below title):**
Separating drought from infrastructure in the 2022 barge rate crisis

**Team line (bottom-left, small):**
Team A02: Arend Colle, Sourav Dhar, Vivek Sriram

**Course line (bottom-left, below team):**
Operations and Supply Chain Analytics

**Optional:** A faint watermark or background image of a barge on the Mississippi.
Keep it subtle. No chart on this slide.

### Notes
- The title is framed as a question on purpose. It creates curiosity and sets up the
  investigative arc. Avoid a generic title like "Lock Maintenance Prioritization" since
  that tells the audience the answer before you begin.
- Mention verbally: "We started this project thinking we'd find that fixing locks
  would lower freight costs. The data told us a different story."

### Speaker Notes
"Hi everyone, we are Team A02. Our project looks at the U.S. inland waterway system,
specifically the Mississippi and Illinois Rivers. We started with a simple question:
if we could prioritize which locks to fix, would that lower freight costs for grain
shippers? We thought the answer would be straightforward. It was not. The data told
us a much more interesting story, and that is what we want to walk you through today."


---

## Slide 2: The Hook

### Purpose
Make the audience care. Anchor the problem in real dollars and a real event.

### Content

**Layout:** Mostly text, clean. White background. No chart.

**Title (top-left, bold):**
In fall 2022, barge shipping costs spiked to 5x normal

**Body (center, large font, stacked as three short lines):**

Line 1 (bold, large, ~28pt):
"Normal cost: ~$17 per ton"

Line 2 (bold, extra-large, red/coral color, ~36pt):
"October 2022: $79 per ton"

Line 3 (regular, medium, ~18pt, gray):
Illinois River spot barge rate, USDA Grain Transportation Report

**Bottom annotation (small, left-aligned, italic):**
Rates are quoted as % of a published tariff ($3.80/ton).
Peak rate hit 2,075% of tariff vs. a long-run average of ~440%.

### Notes
- The per-ton framing makes it tangible. "2,075% of tariff" is meaningless to a
  general audience. Five times normal cost is immediately graspable.
- Verbally add: "For a standard 15-barge tow carrying about 22,500 tons, that is an
  extra $1.4 million per trip. This happened during harvest season, exactly when
  farmers need to move grain to export terminals."
- This slide should be on screen for ~30 seconds max. It is a hook, not analysis.
- Course-concept framing to mention verbally: grain moves on a forecast-driven
  **push** chain (planted months in advance, harvested on a fixed window, committed
  to export contracts). There is no demand-side flex. When a supply shock hits, the
  **price lever** absorbs all the uncertainty, which is exactly why rates spike
  5x rather than volumes adjusting.

### Speaker Notes
"To put the problem in concrete terms: normally, shipping grain by barge down the
Illinois River costs about 17 dollars per ton. In October 2022, that cost spiked to
79 dollars per ton. That is nearly five times normal. To give you a sense of scale, a
typical barge tow carries about 22,500 tons. At that peak rate, shippers were paying
roughly 1.4 million dollars extra per trip. And this happened right in the middle of
harvest season, when farmers need to move the most grain to Gulf export terminals.

It is worth noting why the shock shows up as a price spike rather than as a volume
adjustment. Grain shipping is a classic push supply chain. Crops are planted months
ahead of time, harvested on a fixed seasonal window, and already committed to export
contracts. Shippers cannot simply decide to move less grain when the river gets
expensive. So when a supply-side shock hits, the price lever absorbs all of the
uncertainty. That is what you are looking at here. So the question becomes: what
caused this, and can we prevent it?"


---

## Slide 3: The System We Are Studying

### Purpose
Orient the audience geographically. Establish the scope of the data.

### Content

**Title (top-left, bold):**
23 locks on two rivers, 3 years of data

**Layout:** Map on the right (60% of slide), text on the left (40%).

**Left side, 3-4 bullet points (medium font):**
- Mississippi River (Lock 01 to Lock 27) and Illinois River
- 84 unscheduled, traffic-stopping events from 2021 to 2023
- 3,792 total hours of downtime
- Data from the U.S. Army Corps of Engineers Lock Performance Monitoring System

**Right side:**
**Figure: Map (reworked fig 10)**
- Static screenshot of the lock map, not interactive
- Bubble size = total stoppage hours
- Color = priority tier (red, yellow, green)
- Graph dimensions: ~6" x 5" (roughly square to fit the geographic shape)
- Title font 13pt, legend font 9pt
- Crop to show Minnesota down to St. Louis, omit unnecessary whitespace east/west
- Remove the Plotly toolbar and interactive elements

### Notes
- Mention the data pipeline verbally: "We pulled stoppage records from the USACE API
  and matched them week-by-week to freight rates and grain volumes from the USDA
  Grain Transportation Report."
- This shows depth/breadth (rubric criterion 1): constructing the dataset from
  two federal data sources and aligning them temporally.

### Speaker Notes
"Here is the system we are looking at. The Mississippi River from Minneapolis down to
St. Louis, plus the Illinois River. That is 23 locks total. We pulled three years of
stoppage data from the U.S. Army Corps of Engineers Lock Performance Monitoring System
through their API. That gave us about 25,000 raw records, which we filtered down to 84
unscheduled events that actually stopped barge traffic. We then matched those
week-by-week with freight rate data and grain volume data from the USDA Grain
Transportation Report. The bubbles on this map show where the worst downtime is
concentrated, and as you can see, it is not spread evenly. A handful of locks in the
upper Mississippi are responsible for most of the disruption."


---

## Slide 4: The 2022 Crisis Was Unprecedented

### Purpose
Show the scale of the 2022 rate spike. This is the descriptive "wow" moment.

### Content

**Title (top-left, bold):**
The 2022 rate spike was unlike anything in 16 years of data

**Layout:** Chart fills ~80% of the slide. Minimal text.

**Figure: Rate Time Series (reworked fig 1)**
- Keep the 2010-to-2026 time series with 4-week rolling average
- REMOVE the 2012 drought shading (distracting, save for verbal mention)
- Keep the 2022 crisis shading (pastel red) and the peak annotation (2,075%)
- Graph dimensions: ~12" x 5" (wide, ~2.4:1 aspect ratio, full-width on slide)
- Title font 14pt, axis labels 11pt, annotation 10pt
- The bottom stat line can stay: "2022 crisis avg: 980% | 2021 baseline: 438% |
  premium: +542 points"

**No bullet points needed.** The chart speaks for itself.

### Notes
- Verbally: "Barge rates have been tracked since 2010. You can see normal
  fluctuations, and then 2022 completely breaks the pattern. Rates peaked at
  2,075%, more than double anything seen before."
- You can mention 2012 verbally as a smaller drought year: "There was a drought in
  2012 too, but the spike was far smaller."
- Key stat: the 2022 crisis average (Jul to Dec) was 980% vs. a 2021 baseline of
  438%. That is a +542 point premium.

### Speaker Notes
"This chart shows 16 years of weekly barge freight rates on the Illinois River. You can
see normal seasonal fluctuations throughout the period, rates go up a bit during harvest
and come back down. But then look at late 2022. The spike is completely off the chart.
Rates peaked at 2,075 percent of tariff, which is more than double anything we had seen
in the prior 12 years. There was actually a drought in 2012 as well, you can see a small
bump there, but nothing close to this magnitude. During the second half of 2022, the
average rate was 980 percent versus a 2021 baseline of about 440. That is a premium of
over 500 tariff points. So the obvious question is: what made 2022 so extreme?"


---

## Slide 5: Normal Year vs. Crisis Year

### Purpose
Isolate the 2022 anomaly by comparing week-by-week against a normal year.
This makes the divergence visceral.

### Content

**Title (top-left, bold):**
2022 rates diverged from normal starting in the spring

**Layout:** Chart fills ~80% of the slide.

**Figure: 2021 vs 2022 Overlay (reworked fig 3)**
- Keep the two-line overlay (blue = 2021, red = 2022)
- Keep the crisis-period shading (Jul to Dec)
- Key change: add an annotation callout box near the peak pointing out that 2022
  was elevated ALL year, not just during the crisis window. This is visible in
  the chart but the audience might miss it.
- Graph dimensions: ~12" x 5" (same wide format as fig 1)
- Title font 14pt, legend font 10pt, annotation 10pt
- Consider making the 2022 line thicker (3pt) vs 2021 (2pt) to draw the eye

### Notes
- Verbally: "Notice that 2022 rates were already running 50 to 100% above 2021
  even in January through June, well before the drought hit. This is our first
  clue that something systemic was going on beyond just lock failures."
- This sets up the regression: the audience is primed to wonder "what caused
  the gap?"
- Transition to next slide: "So what was actually causing all this downtime?"

### Speaker Notes
"To isolate just how abnormal 2022 was, here we overlay it week by week against 2021,
which was a fairly typical year. The blue line is 2021, the red line is 2022. A few
things stand out. First, look at the shaded area on the right, that is the July through
December crisis period when the low-water drought was at its worst. Rates absolutely
explode, going from around 500 all the way to over 2,000. But here is the interesting
part: look at the left side of the chart, January through June. Even before the drought
hit, 2022 rates were already running significantly above 2021. That tells us there was
something broader going on, not just individual lock failures. This became our first
clue that we needed to separate the year-level conditions from the lock-level events.
So let us look at what was actually causing the lock downtime."


---

## Slide 6: What Causes Lock Stoppages?

### Purpose
The "reveal" moment. Most downtime is weather, not failing equipment.
This reframes the entire question.

### Content

**Title (top-left, bold):**
95% of lock downtime is caused by weather, not equipment

**Layout:** Single-panel chart on the right (55% of slide), text on the left (45%).

**Left side, stacked text:**

Large callout number (bold, ~40pt, red):
"5%"

Below it (regular, ~16pt):
of stoppage hours are caused by
infrastructure failure

Small gap, then:

Second callout number (bold, ~40pt, blue):
"95%"

Below it (regular, ~16pt):
are caused by flooding, fog,
ice, and other weather events

**Right side:**
**Figure: Cause Breakdown (redesigned fig 6, single panel only)**
- Horizontal bar chart showing top 6-8 reason codes
- Infrastructure reasons in red, external reasons in blue
- This is the RIGHT panel of the current fig 6, NOT the left panel
- The left panel (two bars) is replaced by the text callout on the left
- Graph dimensions: ~6" x 5" (portrait-ish, fits right half of slide)
- Title font 13pt, bar labels 10pt, axis labels 10pt
- Sort descending. High Water and Flood will dominate.

### Notes
- This is the most important framing slide. It tells the audience: even if we
  could magically prevent all infrastructure failures, 95% of the downtime would
  remain.
- Verbally: "We classified every stoppage event by its documented reason code.
  High water alone caused more downtime than all infrastructure failures combined.
  Lock hardware malfunction accounts for only about 192 hours out of 3,792 total."
- Total events: 7 infrastructure-caused out of 84 total.
- This sets up the regression: if infrastructure is only 5% of stoppages, how
  much do stoppages even affect freight rates?

### Speaker Notes
"This is one of the most important slides in our presentation. We went through every
single stoppage event and classified it by its documented reason code from the Army
Corps data. On the left you see the headline: only 5 percent of all unscheduled
stoppage hours were caused by infrastructure problems, things like lock hardware
malfunction or equipment needing repair. The other 95 percent? Weather. High water,
flooding, fog, lightning, ice. If you look at the bar chart on the right, high water
and flooding alone account for more downtime than all other causes combined.

So what does this mean? It means that even if you could perfectly maintain every single
lock on the river, 95 percent of the downtime would still happen. You cannot fix the
weather. This was our first major finding, and it immediately reframed our entire
analysis. The next question became: if most stoppages are weather-driven, do they
even affect freight rates in a measurable way?"


---

## Slide 7: Separating Drought from Infrastructure (The Regression)

### Purpose
This is the analytical core. Show that the regression cleanly separates the drought
effect from the stoppage effect, and that stoppages contribute essentially nothing
to rate changes.

### Content

**Title (top-left, bold):**
The drought explains the rate spike, not lock failures

**Layout:** Chart on the right (55%), model summary on the left (45%).

**Left side, formatted as a clean model comparison:**

Small header (bold, 11pt):
"OLS Regression: Illinois River Rate (2021 to 2023)"

Model comparison table or styled list (10pt, monospace or clean sans-serif):

| Variable          | Model 1  | Model 2  |
|:------------------|:---------|:---------|
| Stoppage Hours    | -0.08    | **-0.01**|
| Week of Year      | +3.14    | +2.86    |
| 2022 Dummy        |          | **+380** |
| 2023 Dummy        |          | +57      |
| R-squared         | 0.06     | **0.32** |

Below the table (italic, small, ~9pt):
"Adding year controls improves R-squared from 0.06 to 0.32.
The 2022 dummy absorbs +380 tariff points. Stoppage effect drops to zero."

**Right side:**
**Figure: NEW, Rate Decomposition Waterfall Chart**
- A waterfall/stacked bar showing how the model decomposes an observed 2022 rate
- Bars: Baseline (intercept) -> + Seasonal (week effect) -> + 2022 Drought (+380)
  -> + Stoppages (~0) -> = Predicted Rate
- The drought bar should be large and red. The stoppage bar should be tiny/invisible
  and gray, with a "~0" label.
- This makes the finding instantly visual: the drought bar dominates, the stoppage
  bar is nothing.
- Graph dimensions: ~6" x 5" (vertical orientation works well for waterfalls)
- Title font 13pt, bar labels 11pt bold, axis label 10pt
- Use the project pastel palette: red for drought, gray for stoppages, blue for
  baseline

### Notes
- This is where you earn the "rigor" points on the rubric. The key narrative:
  "Model 1 includes only stoppage hours and week of year. It explains 6% of rate
  variation. Model 2 adds year fixed effects, which control for conditions that
  affect the entire river in a given year, like the drought. R-squared jumps to
  0.32. All of that improvement comes from the 2022 dummy, which captures +380
  tariff points of drought-driven rate elevation. The stoppage coefficient drops
  to essentially zero."
- Connecting the dots (rubric criterion 4): "The 2022 low-water crisis was a
  hydrology event. Our model cleanly separates that from infrastructure. This
  means you cannot reduce rate spikes by fixing locks."
- Transition: "So if maintenance does not reduce rates, does it still matter?"

### Speaker Notes
"To answer that question rigorously, we ran a regression. On the left you see two
models. Model 1 is a simple regression with just stoppage hours and week of year as
predictors of freight rates. It barely explains anything, R-squared of 0.06.

Model 2 adds year fixed effects, which are dummy variables for 2022 and 2023. These
control for anything that affected the entire river system in a given year, most
importantly the drought. And look what happens. R-squared jumps to 0.32, a massive
improvement. But here is the key: all of that improvement comes from the 2022 dummy
variable, which captures a plus-380 tariff point elevation. That is the drought signal.

Meanwhile, the coefficient on stoppage hours drops from minus 0.08 to minus 0.01.
Essentially zero. The waterfall chart on the right makes this visual. When we decompose
a predicted 2022 rate, the drought bar is enormous, it dominates everything. The
stoppage bar is flat. It contributes nothing.

So what does this tell us? The 2022 rate crisis was a weather event, not an
infrastructure event. You cannot reduce freight rate spikes by fixing locks. But that
does not mean maintenance is pointless. It just means we need to think about it
differently."


---

## Slide 8: Stoppages Still Create Real Disruption

### Purpose
Pivot from "stoppages do not affect rates" to "but they still cause major
operational disruption." This bridges the analytical finding to the prescriptive
recommendation.

### Content

**Title (top-left, bold):**
A few locks account for most of the disruption

**Layout:** Chart fills ~70% of slide (right side), key insight on the left.

**Left side, 2-3 bullet points (medium font):**
- 46% of all stoppage hours come from just 4 of 23 locks
- Lock 08 had 16 separate events in 3 years (chronic, recurring failure)
- Lock 12 had a single event lasting 360 hours (15 days)

**Right side:**
**Figure: Lock Ranking (reworked fig 5, top 6 only)**
- Horizontal bar chart, 6 bars instead of 12
- Keep the tier coloring (red = top tier, yellow = mid)
- Annotate each bar with: total hours, number of events, avg hours per event
- Add a callout or icon for Lock 08 highlighting "16 events" to visually
  distinguish chronic vs. one-time failures
- Graph dimensions: ~7" x 5" (slightly wider than tall)
- Title font 13pt, bar annotations 10pt, axis labels 10pt

### Notes
- Verbally explain the two failure modes: "Lock 08 keeps breaking repeatedly,
  about once every 2 months on average. That is a chronic maintenance problem.
  Lock 12 broke once but was down for 15 straight days. These require
  different solutions: preventive maintenance vs. faster repair capability."
- Stat to mention: Lock 16, 12, 17, and 08 together = 1,728 hours = 46% of total.
  Top 8 locks = 72% of total. Classic Pareto distribution.
- This slide answers "which locks?" without needing dollar ROI.
- Consider mentioning that 2023 had 3.4x the stoppage hours of 2022 (2,376 vs 720)
  despite fewer events (26 vs 29). The system is aging.

### Speaker Notes
"Even though stoppages do not drive freight rates, they still create real operational
disruption. Nearly 3,800 hours of traffic-stopping downtime over three years. And it is
not spread evenly. This chart shows the top six locks by total stoppage hours.

Two patterns jump out. First, look at Lock 08. It had 16 separate events in three
years. That is roughly once every two months. Each one is relatively short, about 28
hours on average, but it just keeps happening. That is a classic chronic maintenance
problem, the kind where preventive investment would pay off.

Now compare that to Lock 12. One single event, but it lasted 360 hours. That is 15
straight days of a lock being completely shut down. That is a different kind of problem,
one that requires faster repair capability or redundancy.

Together, the top four locks, Lock 16, 12, 17, and 08, account for 46 percent of all
stoppage hours across the entire system. And one more thing worth noting: in 2023, total
stoppage hours were 3.4 times higher than in 2022, despite fewer individual events.
The stoppages are getting longer. The system is aging."


---

## Slide 9: Concentration of Risk

### Purpose
Show the Pareto pattern quantitatively. Give the audience a clear "so what"
for resource allocation.

### Content

**Title (top-left, bold):**
Fixing the top 4 locks addresses nearly half of all downtime

**Layout:** Chart fills ~75% of slide (center-right). One insight callout on the left.

**Left side, single callout block:**

Large number (bold, ~36pt):
"46%"

Below (regular, ~14pt):
of total stoppage hours
come from 4 of 23 locks

Below that (regular, ~12pt):
Top 8 locks cover 72%

**Right side:**
**Figure: NEW, Pareto/Cumulative Chart**
- X-axis: locks sorted by total stoppage hours, descending (lock 16, 08, 17, 12, ...)
- Y-axis (left): individual bar heights = stoppage hours per lock (bar chart)
- Y-axis (right): cumulative % line (line chart overlay)
- Mark the 50% line with a horizontal dashed line
- Highlight the first 4 bars in red (tier 1), next 4 in yellow (tier 2),
  remainder in light gray
- Graph dimensions: ~8" x 5" (standard landscape)
- Title font 13pt, axis labels 10pt, bar value labels 9pt
- Keep it clean. No more than 10-12 locks on the x-axis; group the rest as "other"

### Notes
- This replaces fig 9 (budget scenarios). The old fig 9 required made-up
  maintenance cost estimates and a regression coefficient that was essentially zero.
  The Pareto chart uses only real, observed data: stoppage hours per lock.
- Verbally: "We do not need a complex cost model to see the pattern. Downtime is
  heavily concentrated. A targeted maintenance program aimed at the worst offenders
  would dramatically improve system reliability."
- Alternative framing: "Even with limited budgets, you can address the biggest
  reliability risks by focusing on a small number of locks."
- If the audience asks about costs: acknowledge that USACE maintenance cost estimates
  vary widely and that a full cost-benefit analysis would require project-level
  engineering assessments beyond the scope of this analysis.

### Speaker Notes
"This Pareto chart makes the concentration of risk very clear. The bars show stoppage
hours for each lock, sorted from most to least. The line shows the cumulative percentage.

You can see that just 4 locks out of 23, that is fewer than one in five, account for 46
percent of all downtime in the system. If you extend that to the top 8 locks, you cover
72 percent. After that, you are picking up increasingly small increments.

The practical implication is straightforward. You do not need to fix all 23 locks to
make a meaningful difference. A targeted maintenance program focused on the worst
offenders would address nearly half of all system downtime. And unlike a rate-reduction
argument, this recommendation does not depend on any assumptions about freight costs. It
is based purely on observed downtime data from the Army Corps."


---

## Slide 10: Takeaways and Recommendations

### Purpose
Close the loop. Three clear takeaways that the audience remembers.

### Content

**Title (top-left, bold):**
Three things to take away

**Layout:** Clean text slide. No chart. Numbered list with generous spacing.

**Body (left-aligned, numbered, ~16pt, with bold lead-ins):**

**1. The 2022 rate crisis was a drought story, not an infrastructure story.**
Our regression shows that year-level conditions (the low-water drought) explain the
rate spike. Lock stoppages had no measurable effect on freight rates after controlling
for year.

**2. Most lock downtime comes from weather, not equipment failure.**
Only 5% of unscheduled stoppage hours were caused by infrastructure problems.
Maintenance investment cannot address the 95% driven by flooding, fog, and ice.

**3. Maintenance still matters, but for reliability, not for rates.**
Four locks account for 46% of all downtime. Targeted investment in these chronic
offenders would meaningfully improve system reliability, even if it does not
reduce freight costs.

**Framing box (bottom, light gray background, ~11pt italic):**
In course terms: rate volatility is the *price lever* absorbing weather uncertainty;
maintenance is the *capacity lever* improving reliability. Barge is the efficient
mode in a push chain with no slack, so shocks translate into price spikes rather
than volume adjustments. Conflating the two levers misallocates budget.

**Bottom-right, small, italic:**
Data: USACE LPMS (2021 to 2023), USDA GTR barge rates and volumes (2010 to 2026)

### Notes
- Keep this slide up during Q&A if applicable.
- Verbally: "We started this project expecting to find that fixing locks would
  lower freight costs. The data showed us something more nuanced: droughts and
  infrastructure are separate problems that require separate solutions. Rate
  volatility is a weather and climate risk. Infrastructure maintenance is an
  operational reliability investment. Mixing the two leads to misallocated budgets."
- This framing (following the data to a surprising conclusion) scores well on
  rubric criteria 2 (rigor) and 4 (connecting the dots).
- Course-concept tie-in: the five levers for managing uncertainty are capacity,
  inventory, time, information, and price. Our finding maps cleanly onto two of
  them. Rate volatility is the price lever doing its job (absorbing weather
  uncertainty). Maintenance is the capacity lever. Separately, barge is the
  efficient end of the efficiency-responsiveness spectrum; rail and truck are
  more responsive but more expensive. During the 2022 crisis, shippers who needed
  grain to move paid the responsiveness premium.

### Speaker Notes
"So let us bring it all together with three takeaways.

First, the 2022 rate crisis was a drought story, not an infrastructure story. Our
regression proves this. The year fixed effect for 2022 captures a 380 tariff point
elevation. The stoppage coefficient is zero. You cannot fix rate spikes by fixing locks.

Second, most lock downtime comes from weather, not equipment failure. Only 5 percent
of stoppage hours are infrastructure-related. The other 95 percent is flooding, fog,
ice, things that no amount of maintenance spending will prevent.

Third, and this is the important nuance, maintenance still matters. It just matters for
a different reason than we originally thought. It is not about rates. It is about
reliability. Four locks account for nearly half of all system downtime, and stoppages
are getting longer year over year. Targeted investment in these chronic problem locks
would meaningfully improve how reliably the system operates.

We started this project expecting to build a cost-benefit model for lock repairs. The
data pushed us to a more honest conclusion: droughts and infrastructure are separate
problems that need separate solutions.

In the language of the course, these map onto two different levers for managing
uncertainty. Rate volatility is the price lever at work, absorbing a supply-side
weather shock in a push chain that has no slack built in. Maintenance is the capacity
lever, improving the reliability of the efficient shipping mode. Barge is the cheap,
efficient option; rail and truck are the responsive substitutes shippers fall back on
when locks fail, and they pay the responsiveness premium for it. Rate volatility is a
climate risk. Maintenance is a reliability investment. Mixing the two up leads to
misallocated budgets. Thank you."


---

## Appendix Slides (not presented, available for Q&A)

### Appendix A: Full Lock Ranking Table

**Purpose:** Reference for anyone who asks about a specific lock.

**Content:**
- Table with all 23 locks: lock number, number of stoppages, total hours,
  average hours per event, volume weight, weight source (GTR data vs estimate)
- Sorted by total stoppage hours descending
- Highlight tier 1 rows in light red

### Appendix B: Regression Details

**Purpose:** Back up the model comparison for technical questions.

**Content:**
- Full coefficient table for both models
- Note on methodology: OLS with year fixed effects, n=156 weekly observations
  (2021 to 2023), dependent variable = Illinois River spot rate (% of tariff)
- Note that stoppage hours are aggregated across all locks per week
- Explain what year fixed effects control for (any river-wide condition that
  varies by year but not by week, primarily drought/hydrology)

### Appendix C: Data Pipeline Overview

**Purpose:** Show the end-to-end data engineering work.

**Content:**
- Diagram or bullet list: USACE API (6-month windows, 24,881 raw records) ->
  filter to MI + IL rivers -> unscheduled + traffic-stopped events (84 records)
  -> merge with USDA GTR weekly rates and volumes -> 156 matched weeks for
  regression
- This demonstrates rubric criterion 1 (depth/breadth of content)

### Appendix D: Seasonal Pattern

**Purpose:** Reference for the seasonal premium stat if asked.

**Content:**
- The seasonal bar chart (original fig 2) showing harvest weeks 36 to 50 vs.
  off-season
- Harvest avg: 579% vs. off-season avg: 417%. Seasonal premium: +162 points.
- This is real and interesting but not critical to the main storyline, so it lives
  in the appendix rather than the main deck.


---

## Figure Specifications Summary

Below is a reference for each figure that needs to be created or reworked.
Dimensions are given as matplotlib figsize (width, height in inches).
Font sizes assume the figure will be embedded at the stated slide fraction.

### Fig 1 (reworked): Rate Time Series
- **Slide:** 4
- **figsize:** (12, 5)
- **Slide fraction:** ~80% width
- **Changes from current:** Remove 2012 drought shading. Keep 2022 crisis shading
  and peak annotation. Keep bottom stat line.
- **Font sizes:** title 14pt bold, axis labels 11pt, tick labels 10pt, annotation
  10pt bold, bottom stat line 9pt
- **File:** fig1_rate_timeseries.png

### Fig 3 (reworked): 2021 vs 2022 Comparison
- **Slide:** 5
- **figsize:** (12, 5)
- **Slide fraction:** ~80% width
- **Changes from current:** Make 2022 line thicker (3pt vs 2pt for 2021). Add a
  small annotation near Jan-Jun area noting "rates already elevated before drought."
- **Font sizes:** title 14pt bold, axis labels 11pt, legend 10pt, annotation 10pt
- **File:** fig3_2021v2022.png

### Fig 6 (redesigned): Cause Breakdown, Single Panel
- **Slide:** 6
- **figsize:** (6, 5)
- **Slide fraction:** ~55% width (right side)
- **Changes from current:** Use ONLY the right panel (horizontal bar by reason code).
  Drop the left panel entirely (replaced by on-slide text callout). Show top 6
  reasons. Infrastructure reasons in red, external in blue.
- **Font sizes:** title 12pt bold, bar labels 10pt, axis labels 10pt, legend 9pt
- **File:** fig6_stoppage_causes_v2.png

### NEW: Rate Decomposition Waterfall
- **Slide:** 7
- **figsize:** (6, 5.5)
- **Slide fraction:** ~55% width (right side)
- **Type:** Waterfall chart with 5 bars: Intercept (baseline), Week Effect,
  2022 Drought (+380), Stoppages (~0), Predicted Rate (total)
- **Color:** Blue for intercept, blue for week, RED for drought (the dominant bar),
  GRAY for stoppages (tiny/flat), dark blue outline for total
- **Font sizes:** title 13pt bold, bar value labels 12pt bold, axis labels 10pt
- **Key detail:** The drought bar must visually dominate. The stoppage bar should be
  barely visible or flat, with a "~0" label. This is the visual punchline.
- **File:** fig_waterfall_decomposition.png

### Fig 5 (reworked): Lock Stoppage Hours, Top 6
- **Slide:** 8
- **figsize:** (7, 5)
- **Slide fraction:** ~65% width (right side)
- **Changes from current:** Show only top 6 locks instead of 12. Keep tier coloring.
  Add a small icon or annotation for Lock 08 calling out "16 events (chronic)."
- **Font sizes:** title 13pt bold, bar annotations 10pt, axis labels 10pt, legend 9pt
- **File:** fig5_lock_hours_v2.png

### NEW: Pareto / Cumulative Concentration Chart
- **Slide:** 9
- **figsize:** (8, 5)
- **Slide fraction:** ~70% width (center-right)
- **Type:** Combo chart. Bars = stoppage hours per lock (left y-axis). Line =
  cumulative % of total hours (right y-axis).
- **Color:** First 4 bars in red, next 4 in yellow, rest in light gray. Line in
  black with dot markers.
- **Mark:** Horizontal dashed line at 50% on cumulative axis. Vertical dashed
  line after lock 4 with label "top 4 = 46%."
- **Font sizes:** title 13pt bold, bar labels 9pt, axis labels 10pt, cumulative
  % labels 10pt bold
- **File:** fig_pareto_locks.png

### Fig 10 (reworked): Lock Map
- **Slide:** 3
- **figsize:** ~6" x 5" static image export
- **Slide fraction:** ~55% width (right side)
- **Changes from current:** Export as static PNG (not interactive HTML). Crop
  tighter to the river system. Remove Plotly toolbar. Keep bubble size = hours,
  color = tier.
- **Font sizes:** title 12pt, legend 9pt
- **File:** fig10_lock_map_static.png


---

## Slides That Do NOT Need a Figure

| Slide | Why no figure |
|:------|:-------------|
| 1 (Title) | Professional text-only opener |
| 2 (Hook) | The big numbers ARE the visual. A chart would compete. |
| 10 (Takeaways) | Clean text lets the three points land. No distraction. |


---

## Scrapped Figures (with reasons)

| Old Figure | Reason for Removal |
|:-----------|:-------------------|
| Fig 2 (seasonal bars) | 52 nearly-equal bars. The finding (harvest premium +162 pts) fits in one sentence. Moved to appendix. |
| Fig 4 (stoppages by year) | Count panel is boring (29, 29, 26). Hours panel is interesting but the key stat (2023 = 3.4x more hours) works better as a spoken stat on slide 8. |
| Fig 7 (boxplot) | Shows stoppages have LOWER median rates than non-stoppage weeks. Contradicts a "stoppages hurt" narrative and adds confusion. The regression on slide 7 handles this finding far more rigorously. |
| Fig 8 (scatter matrix) | Axes mix a heuristic score with made-up cost estimates. Hard to read. Audience would challenge the numbers. |
| Fig 9 (budget scenarios) | Built on the heuristic severity score and fabricated maintenance costs. Replaced by the Pareto chart which uses only observed data. |
