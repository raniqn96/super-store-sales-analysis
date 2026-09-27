# Portfolio Project Summary — Superstore Sales Analysis

**Project**: End-to-end retail sales analysis with an interactive Tableau executive dashboard
**Role**: Senior Data Analyst · **Dataset**: 2,316 order lines, 760 customers, 48 US states, 2014–2017
**Stack**: CSV ingestion → data profiling & EDA → Tableau dashboard (KPIs, trends, maps, LOD expressions) → executive insights report

---

## Key Findings

1. **Healthy top line, thin margin.** $1.25M cumulative sales generated $125K profit — a 9.98% margin against a 12.5% benchmark. Profit is highly concentrated, not broadly earned.
2. **Furniture is bleeding.** Technology (18.6% margin) and Office Supplies (19.4%) fund the business; Furniture runs at **−5.6% margin (−$25.3K)**. The Tables sub-category alone lost **$51.7K (−23.2% margin)**.
3. **Discounting cannibalizes profit.** Deep discounts (>40–70%) on commercial table lines produced the five worst loss-making products (up to −$2.9K per line). Discounts above ~20% on Tables yield negative profit on 94% of transactions.
4. **Uneven regional efficiency.** The South runs at 13.1% margin while the West trails at 7.0% — a ~6-point spread pointing at state-level pricing gaps in California and Washington.
5. **Copiers are the profit engine.** The enterprise copier line delivers a 34.6% margin — unmatched unit economics that warrant more shelf space and marketing spend.

## Strategic Recommendations Delivered

- Cap Furniture promotional discounts at 15%; enforce a hard ceiling on Tables.
- Prune the five chronic loss-making table SKUs (BPI, Bevis, Bretford); reallocate space to Copiers and Phones.
- Run state-level pricing reviews in the West to close the margin gap toward the South benchmark.

## Tableau Skills Demonstrated

| Skill | Where It's Applied |
| :--- | :--- |
| **KPI banner design** | Big-number cards for Sales, Profit, Quantity, Avg Profit/Line |
| **Dual-axis time series** | Monthly Sales vs. Profit trend with YoY growth annotation |
| **LOD expressions** | `{ FIXED [Sub-Category] : ... }` for filter-stable sub-category margins |
| **Table calculations** | `LOOKUP`-based YoY growth; running totals on the trend line |
| **Calculated fields** | Profit Ratio, Profit Status (profitable/loss flagging) |
| **Geographic visualization** | State-level symbol map with geographic roles and ZIP code handling |
| **Drill-down hierarchies** | Category → Sub-Category → Product navigation |
| **Segmentation & ranking** | Segment share analysis; top/bottom 5 product bar charts |
| **Dashboard composition** | Interactive executive cockpit with cross-filtering, built to work in Tableau Desktop and Tableau Public |

## Supporting Files

- `Superstore_Sales_Data.csv` — raw transactional data
- `Data_Dictionary.md` — field definitions and intended analytical use
- `Tableau_Dashboard_Build_Guide.md` — step-by-step reproduction guide
- `Superstore_Sales_Executive_Report.md` — full findings and recommendations
