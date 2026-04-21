# OSCA 46-893: Complete Concept Walkthrough

---

## MODULE 1: SCM FUNDAMENTALS & STRATEGIC FRAMEWORK

### 1.1 The Five-Point Strategic Framework (Value Creation to Value Capture)

This is one of the most important conceptual models in the course. Understand each step and how they build on each other.

**1. Arbitrage** -- Find a gap between what something costs and what someone will pay. Transformations in space (move it), time (store it), or form (process it). The coffee example is perfect: beans cost ~$4/lb to produce, but a Starbucks latte sells for $5+ per cup. Every supply chain is fundamentally an arbitrage operation.

**2. Execution** -- Break tasks into atomic, granular pieces and ensure each is completed with near-certainty. The goal: make it literally impossible to fail at each step. Think of IKEA furniture (thousands of identical units assembled from a fixed instruction set) vs. a master carpenter building a custom table. Amazon's fulfillment is the gold standard here.

**3. Standardization** -- Execute the same process the same way, every time. Benefits of standardization:
- Amortization of fixed costs (higher volume = lower per-unit fixed cost; the Kraft Heinz ham factory example: $1.50/lb at 150M lbs vs. $0.15/lb at 1.5B lbs)
- Learning and process improvement (the Fuyao windshield learning curve shows output/shift climbing while first-pass yield improves over months)
- Risk pooling (independent risks cancel out; CV drops by 1/sqrt(n) when pooling n identical sources)
- Operational flexibility via delayed differentiation (keep products generic as long as possible, customize late; e.g., HP printers share identical hardware, differ only in software)

**4. Scaling (or Automation)** -- Replicate the standardized process elsewhere. Key distinction: increasing throughput is NOT the same as achieving scalability. Gordon Ramsay's restaurant produces amazing food (high throughput) but cannot be easily replicated. McDonald's produces consistent food (moderate throughput) but can be franchised 13,500+ times. The talent distribution follows a power law, not a normal distribution, which is why truly scalable systems minimize dependence on superstar talent.

**5. Value Capture** -- Execution is positive-sum (everyone benefits from a bigger pie). Dividing the profit is zero-sum. The $15 shirt breakdown: ~58% is markup, ~7% materials, ~2% labor. Who captures value depends on bargaining power, not just who creates it.

**"The Playbook"** (how the best companies operate):
1. Add scale economy (lower costs, pass savings to customers, grow volume)
2. Add flexibility (better selection, faster delivery, reinvest profit)
3. Use bargaining power (scale, monopoly/monopsony power)


### 1.2 What is a Supply Chain?

All parties involved, directly or indirectly, in fulfilling a customer request. Includes suppliers, manufacturers, warehouses, transporters, retailers, and customers themselves.

**SC Objective:** Maximize Supply Chain Surplus = Customer Value - Supply Chain Cost

**Three Flows:**
- Product/material flow (upstream to downstream, plus reverse flows/returns)
- Information flow (bidirectional)
- Funds flow (downstream to upstream)


### 1.3 Cycle View (SCOR Model) vs. Push/Pull View

**Cycle View** breaks the SC into four cycles, each with sub-processes (Plan, Source, Make, Deliver, Return):
- Customer Order Cycle (Customer <-> Retailer)
- Replenishment Cycle (Retailer <-> Distributor)
- Manufacturing Cycle (Distributor <-> Manufacturer)
- Procurement Cycle (Manufacturer <-> Supplier)

**Push/Pull View** divides processes based on what triggers them:
- **Push:** Executed in anticipation of demand (forecasts). Upstream processes.
- **Pull:** Executed in response to actual customer orders. Downstream processes.
- The **Push/Pull Boundary** is where you shift from forecast-driven to demand-driven. Moving this boundary is a strategic decision. Example: CaLNG stores LNG (push) and delivers on demand (pull), shifting uncertainty absorption upstream.


### 1.4 Supply Chain Performance Drivers

**Logistical Drivers:** Facilities, Inventory, Transportation

**Cross-Functional Drivers:** Information, Sourcing, Pricing

These drivers sit on a spectrum between Efficiency and Responsiveness. You trade off between them based on your supply chain structure. More facilities = more responsive but less efficient. More inventory = better availability but higher holding cost. Faster transportation = better service but higher cost.

**Five Levers to Manage Uncertainty:** Capacity, Inventory, Time, Information, Price


---

## MODULE 2: SUPPLY CHAIN NETWORK DESIGN

### 2.1 Facility Location (Gravity Model)

For the P&G facility location problem, the approach is:
1. Formulate: min sum of Fn * Wn * dn(Latx, Longx) across all sources/markets
2. Get lat/long coordinates for each location
3. Compute distances using the Great Circle formula (haversine)
4. Solve for optimal (Latx, Longx) using Excel Solver or grid search
5. Refine with actual driving distances via APIs

The Great Circle distance formula: d = r * arccos(sin(phi1)*sin(phi2) + cos(phi1)*cos(phi2)*cos(delta_lambda))


### 2.2 SunOil: Capacitated Plant Location

This is a classic mixed-integer optimization problem:

**Decision variables:**
- yi = 1 if plant is located at site i, 0 otherwise (binary)
- xij = Quantity shipped from plant i to customer j (continuous)

**Objective:** Min sum(fi * yi) + sum(cij * xij) over all i,j

**Constraints:**
- Demand satisfaction: sum_i(xij) = Dj for all j
- Capacity: sum_j(xij) <= Ki * yi for all i
- Binary: yi in {0,1}

**Key takeaways from SunOil:**
- Economies of scale drive concentrated production
- Capacity decisions are long-term and irreversible
- Tariffs can be mitigated by adjusting product flows (easier) or moving facilities (expensive, irreversible)
- Any plant can supply any market (works well for uniform goods like chemicals)


### 2.3 Factors Influencing Network Design

Regional demand configuration, fixed facility cost (economies of scale), transportation cost and lead time, production cost and flexibility, inventory cost, coordination cost, taxes and tariffs, exchange rates, service level requirements, competition/industry clusters.


### 2.4 SC Design: Tariffs and Global Trade

The course covers tariffs extensively given 2025-2026 developments:
- IEEPA tariffs (struck down by Supreme Court Feb 2026)
- Section 232 (steel, aluminum, automotive)
- Reciprocal tariffs (April 2025 "Liberation Day")
- Overall average effective U.S. tariff rose to ~10%, with China at ~34%

**Reshoring trends:** Manufacturing Import Ratio (MIR) from 14 Asian LCCRs has been declining since 2020. Mexico surpassed China as the largest exporter to the U.S. Construction spending in U.S. manufacturing is at all-time highs.

**Key academic finding (Pierce & Schott):** The sharp decline in U.S. manufacturing employment after 2000 was linked to PNTR (Permanent Normal Trade Relations) with China, which eliminated the uncertainty of potential tariff increases. It was the removal of tariff uncertainty, not the tariff level itself, that triggered offshoring.


### 2.5 CaLNG: Tailoring the Supply Chain

CaLNG demonstrates several core concepts at once:

**Push/Pull Boundary:** Pipeline is push (price-driven); LNG delivery is pull (demand-driven). CaLNG absorbs demand uncertainty by providing peak-shaving capacity.

**Value Creation:** Pipeline pricing is exponential in gas intake. By capping peak demand using LNG, CaLNG dramatically reduces pipeline costs. Average cost with peak charges ($40.2M) vs. cost at flat average demand ($15.3M).

**Network Design (three strategies):**
- Centralized: Large Coos Bay tank, no satellite tanks, many trailers (507), NPV = $10.00M
- Slow Buildup: Small Coos Bay tank, satellite tanks at each customer, fewer trailers (113), NPV = $0.69M
- Hybrid: Medium Coos Bay tank, selective satellite tanks, moderate trailers (169), NPV = $36.66M (best)

**Value-Based Pricing:** Price is set by the customer's next-best alternative (building their own LNG facility). Breakeven prices: SoCalGas $7.94/Mcf, Coalinga $11.12/Mcf, PG&E $7.50/Mcf. CaLNG creates the most surplus for small, remote customers who cannot replicate its scale economics.


### 2.6 Risk Management and Flexibility

**Risk management strategies:** Hedging, Supplier/Customer Diversification, Investing in SC relationships, Flexibility (new product, mix, volume).

**Capacity Investment Strategies:**
- Speculative: Single-source, couple with financial hedge
- Natural-hedge (local-for-local): Match revenue and cost currency exposure
- Flexible: Match suppliers and markets, dedicated + backup
- Chained (Jordan & Graves 1995): "A little bit of flexibility is all you need." Long chain connects each plant to two markets and each market to two plants.
- Full flexibility: Every plant can serve every market (expensive for non-uniform goods)

**D-Solar Case (Onshore vs. Offshore):**
- Using expected values only (Approach 1): Offshore (China) wins at EUR 6,822,302 vs. EUR 6,429,091
- Using decision trees (Approach 2): Onshore (Europe) wins at EUR 6,429,091 vs. EUR 6,247,497
- The difference is the **value of flexibility**. The European plant has wider volume flexibility (60-150k) vs. the Chinese plant (100-130k). Under uncertainty, the ability to scale production up/down is worth paying for.
- This is a powerful illustration of the **fallacy of averages**: evaluating at expected demand/FX hides the cost of inflexibility in adverse scenarios.

**Decision Tree Mechanics:**
- Map out all demand/FX states and transition probabilities per period
- Compute profit at each terminal node
- Work backwards: at each node, compute profit = profit(this period) + PV of expected future profits
- Discount using factor k (0.1 in D-Solar)
- Transition probabilities: multiply demand prob * FX prob (e.g., 0.8 * 0.7 = 0.56)


---

## MODULE 3: DEMAND FORECASTING

### 3.1 Demand Patterns

Observed demand = Systematic component + Random component

Systematic component has three sub-components: **Level**, **Trend**, **Seasonality**

Goal of forecasting: predict the systematic component and estimate the size of the random component.


### 3.2 Time-Series Methods

**1. Naive:** Ft+1 = At (last period's actual)

**2. Moving Average MA(n):** Ft+1 = (1/n) * sum of last n actuals

**3. Weighted Moving Average:** Same but with weights summing to 1

**4. Simple Exponential Smoothing:** Ft+1 = alpha * At + (1 - alpha) * Ft
- alpha close to 1: responsive (tracks actuals closely)
- alpha close to 0: stable (smooths out noise)

**5. Exponential Smoothing with Trend (Holt's / Double Exponential Smoothing):**
- Lt+1 = alpha * At + (1 - alpha) * Ft (level update)
- Tt+1 = beta * (Lt+1 - Lt) + (1 - beta) * Tt (trend update)
- Ft+1 = Lt+1 + Tt+1

For multi-period forecasting: Ft+k = Lt+1 + k * Tt+1

**6. Triple Exponential Smoothing (Winters' Method):**
Adds a seasonality index (SI) component:
- Ft+1 = (Lt+1 + Tt+1) * SIt+1
- Level: Lt+1 = alpha * (At / SIt) + (1 - alpha) * (Lt + Tt)
- Trend: Tt+1 = beta * (Lt+1 - Lt) + (1 - beta) * Tt
- Season: SIt+p = gamma * (At / (Lt + Tt)) + (1 - gamma) * SIt

### 3.3 Seasonality Index

1. Compute overall average demand across all periods
2. Compute average demand for each "season" (e.g., each fiscal quarter)
3. SI = (average for that season) / (overall average)

To forecast with seasonality:
1. De-seasonalize raw data (divide by SI)
2. Forecast using exponential smoothing on de-seasonalized data
3. Re-seasonalize the forecast (multiply by SI)


### 3.4 Forecast Error Metrics

- **MFE** = (1/n) * sum(FEt) -- checks for bias
- **MAD** = (1/n) * sum(|FEt|) -- average absolute error
- **MSE** = (1/n) * sum(FEt^2) -- penalizes large errors
- **MAPE** = (1/n) * sum(|FEt| / At) -- percentage error

Evaluate both in-sample (fit) and out-of-sample (predictive power). Be cautious when in-sample fit is too good (overfitting).


### 3.5 Characteristics of Forecasts

- Forecasts are always wrong. Include expected value AND measure of error.
- Long-term forecasts are less accurate than short-term.
- Aggregate forecasts are more accurate than disaggregate (risk pooling).
- Push processes need forecasts; pull processes respond to actual demand.
- When no historical data exists: use peer groups, real-time data, or Delphi method.


---

## MODULE 4: EFFICIENCY MEASURES (Finance-Operations Link)

### 4.1 Key Financial/Operational Metrics

**Inventory Turnover (IT)** = COGS / Avg. Inventory
- Higher IT = better efficiency
- Walmart example: IT = 9.19 (turns inventory ~9 times/year)

**Days of Inventory Outstanding (DIO)** = 365 / IT
- Lower DIO = better (Walmart: ~40 days)

**Accounts Payable Turnover (APT)** = COGS / Accounts Payable
**Days Payable Outstanding (DPO)** = 365 / APT
- Higher DPO = more command over suppliers (Walmart: ~42 days)

**Accounts Receivable Turnover (ART)** = Sales / Accounts Receivable
**Days Sales Outstanding (DSO)** = 365 / ART
- Lower DSO = faster cash collection (Walmart: ~5 days)

**Cash Conversion Cycle (CCC)** = DIO + DSO - DPO
- Most important composite metric. Lower = better.
- Walmart: CCC = 39.72 + 5.35 - 41.86 = 3.21 days
- Measures how quickly a company converts inventory investment into cash.

**GMROI** = Gross Profit / Avg. Inventory
- Walmart: $3.04 per $1 of inventory investment

**Asset Turnover (AT)** = Sales / Avg. Total Assets
**Fixed Asset Turnover (FAT/PPET)** = Sales / Avg. Fixed Assets


---

## MODULE 5: INVENTORY MANAGEMENT

### 5.1 Role of Inventory

Inventory exists to improve matching of supply and demand:
- **Cycle Inventory:** From economies of scale in ordering/production
- **Safety Inventory:** Buffer against demand/supply variability
- **Seasonal Inventory:** Build ahead for predictable demand peaks

### 5.2 EOQ (Economic Order Quantity)

When demand is known and constant:

**EOQ = sqrt(2 * D * S / h)**

Where:
- D = annual demand
- S = fixed order/setup cost per order
- h = holding cost per unit per year (often h = H * C where H = holding cost rate, C = unit cost)

Total annual cost = (D/Q)*S + (Q/2)*h + D*C

EOQ balances ordering costs (decrease with larger Q) against holding costs (increase with larger Q).


### 5.3 Continuous Review Policy (Q-system)

Order a **fixed quantity Q** when inventory drops to the **Reorder Point (ROP)**.

**ROP = mu_L + SS**

Where:
- mu_L = mean demand during lead time = mu * L
- sigma_L = std dev of demand during lead time = sigma * sqrt(L)
- SS = z(CSL) * sigma_L

**z(CSL)** is the inverse standard normal corresponding to the desired Cycle Service Level.

Example: D = 2,500/week, sigma = 500, L = 4 weeks, CSL = 0.90
- sigma_L = 500 * sqrt(4) = 1,000
- z(0.90) = 1.28
- SS = 1.28 * 1,000 = 1,280
- ROP = 2,500 * 4 + 1,280 = 11,280

**Working backwards:** If ROP = 12,000, then SS = 12,000 - 10,000 = 2,000, and CSL = F(2,000/1,000) = F(2) = 97.7%


### 5.4 Periodic Review Policy (T-system)

Order at **fixed intervals T**, raise inventory to **Order-Up-To Level (OUL)**.

Order quantity Q = OUL - I (current inventory on hand)

**Risk exposure interval = T + L** (not just L, because you must cover demand from now until the NEXT order arrives)

**OUL = mu * (T + L) + z(CSL) * sigma * sqrt(T + L)**

Deterministic example: T = 7 weeks, L = 4 weeks, D = 100/week, I = 300
- OUL = (7+4) * 100 = 1,100
- Q = 1,100 - 300 = 800


### 5.5 Continuous vs. Periodic Review

| Feature | Continuous (Q) | Periodic (T) |
|---------|---------------|--------------|
| When to order | When inventory hits ROP | Every T periods |
| How much | Fixed Q (EOQ) | Variable: OUL - I |
| Risk interval | L periods | T + L periods |
| Safety stock | z * sigma * sqrt(L) | z * sigma * sqrt(T+L) |
| Monitoring | Constant tracking needed | Check only at intervals |

Periodic review requires MORE safety stock for the same service level because the risk exposure interval is longer.


### 5.6 Key Drivers of Safety Stock

Safety stock increases with:
- Higher demand variability (sigma)
- Longer lead time (L)
- Higher desired service level (CSL, which increases z)

Safety stock decreases with:
- Better forecasting (lower sigma)
- Shorter lead times
- Accepting lower service levels


---

## MODULE 6: NEWSVENDOR MODEL & SUPPLY CHAIN CONTRACTS

### 6.1 Newsvendor Problem (Short Life-Cycle Products)

For products with a single selling season (fashion, seasonal goods), you order once before demand is realized.

**Critical Fractile (CF) = Cu / (Cu + Co)**

Where:
- Cu = underage cost = p - c (profit lost per unit of unmet demand)
- Co = overage cost = c - s (cost of each unsold unit; s = salvage value)

**Optimal order Q* satisfies:** F(Q*) = CF, where F is the demand CDF.

For normal demand N(mu, sigma): Q* = mu + z(CF) * sigma

Example: TF jacket. p = $200, c = $10, D ~ N(1000, 300)
- Direct to customer: Cu = 190, Co = 10, CF = 190/200 = 0.95, Q* = 1000 + z(0.95)*300 = 1,493


### 6.2 Double Marginalization

When a manufacturer sells through a retailer at wholesale price w:
- Retailer's Cu = p - w (lower than p - c)
- Retailer's CF = (p - w) / p (lower than (p - c) / p)
- Lower CF means lower optimal order, more stockouts
- Total SC profit is LOWER than if they acted as one integrated firm

This is the fundamental incentive conflict: both parties making a margin on the same sale creates a gap between potential and actual SC profits.


### 6.3 Buyback Contracts

Manufacturer sets wholesale price w AND buyback price b for unsold units.

The buyback price increases the retailer's effective salvage value, lowering Co and raising CF, which increases the order quantity.

**Optimal buyback price** (to achieve first-best/coordinated outcome):

b* = p - (p - w)(p - s) / (p - c)

This sets the retailer's cost structure equal to the supplier's, so CF matches the integrated SC.

Both w and b are levers. The wholesale price w determines the profit split. Higher w shifts more profit to the manufacturer.

Key property: for any demand realization, the profit allocation between the two parties is constant (a fixed fraction of total SC profit).


### 6.4 Revenue Sharing Contracts

Manufacturer charges a LOW wholesale price w, and the retailer shares a fraction (1 - phi) of revenue.

The lower w reduces the retailer's overage cost, inducing higher orders.

**Coordinating revenue sharing contract:**
w = phi * c (if salvage = 0), or more generally w = phi * (c - s) / (p - s)

Higher phi allocates more profit to the retailer.

**Key result (Cachon and Lariviere, 2005):** Coordinating buyback and revenue sharing contracts are equivalent in a very strong sense: for any demand realization, they produce the same profit allocation. The Blockbuster/movie studio example is the classic case.


### 6.5 Other Contracts

- **Quantity flexibility:** Free returns within a limit
- **Quantity discounts:** Incentivize larger purchases and higher availability
- **Rebates:** Manufacturer pays retailer for each unit sold above a threshold

**Core principle:** "Grow the pie first, then worry about splitting it." It IS possible to achieve the first-best (integrated SC) outcome through contract design.


---

## QUICK-REFERENCE: FORMULAS TO KNOW

| Concept | Formula |
|---------|---------|
| EOQ | Q* = sqrt(2DS/h) |
| ROP (continuous) | mu*L + z(CSL) * sigma * sqrt(L) |
| OUL (periodic) | mu*(T+L) + z(CSL) * sigma * sqrt(T+L) |
| Safety Stock | SS = z(CSL) * sigma * sqrt(risk interval) |
| Critical Fractile | CF = Cu / (Cu + Co) |
| Newsvendor Q* | mu + z(CF) * sigma |
| Buyback b* | p - (p-w)(p-s)/(p-c) |
| Revenue sharing w | phi * (c-s)/(p-s) |
| Risk pooling CV | CV of sum of n iid = sigma/(sqrt(n)*mu) |
| CCC | DIO + DSO - DPO |
| Inventory Turnover | COGS / Avg Inventory |
| GMROI | Gross Profit / Avg Inventory |
| Exp. Smoothing | Ft+1 = alpha*At + (1-alpha)*Ft |
| Holt's (Level) | Lt+1 = alpha*At + (1-alpha)*(Lt + Tt) |
| Holt's (Trend) | Tt+1 = beta*(Lt+1 - Lt) + (1-beta)*Tt |
| Forecast | Ft+1 = Lt+1 + Tt+1 |


---

## CONCEPTS MOST LIKELY TO APPEAR ON A CLOSED-BOOK QUIZ

1. **The Five-Point Framework** (arbitrage, execution, standardization, scaling, value capture) and examples
2. **Push vs. Pull** and what the boundary means operationally
3. **SC Performance Drivers** and the efficiency-responsiveness tradeoff
4. **Newsvendor / Critical Fractile** calculation (Cu, Co, CF, optimal Q*)
5. **Double Marginalization** and why it happens
6. **Buyback / Revenue Sharing** mechanics and the coordinating condition
7. **EOQ formula** and its intuition (trading off ordering vs. holding cost)
8. **Safety Stock / ROP** calculation for continuous review
9. **Continuous vs. Periodic review** differences (especially risk exposure interval)
10. **Forecasting methods** (exponential smoothing, Holt's, Winters'), seasonality index, error metrics
11. **CCC, DIO, DSO, DPO** definitions and what "better" means for each
12. **D-Solar / Value of Flexibility** and the fallacy of averages
13. **Decision tree** mechanics (transition probabilities, working backwards)
14. **Risk pooling** math (sigma of sum = sigma * sqrt(n))
15. **Delayed differentiation / postponement** and when it works
