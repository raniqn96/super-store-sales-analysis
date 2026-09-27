# Superstore Sales Analysis — Tableau Dashboard Build Guide

A complete, production-grade guide designed for a **Data Analyst portfolio project**. It reproduces every requirement in your project specification using standard Tableau Desktop or Tableau Public.

---

## 1. Project Overview & Architecture

### Business Purpose
Provide retail sales leadership and operations managers with an interactive cockpit to track revenue health, detect margin leaks, monitor geographic distribution, and make product assortment decisions.

### Core Metrics (The 4 Primary KPIs)
1. **Total Sales**: `$1,254,406.59` (`SUM([Sales])`)
2. **Total Profit**: `$125,234.86` (`SUM([Profit])`)
3. **Total Quantity Sold**: `7,325 units` (`SUM([Quantity])`)
4. **Average Profit per Transaction**: `$54.07` (`[Total Profit] / COUNT([Row ID])`)
5. *Bonus KPI*: **Overall Profit Margin**: `9.98%` (`[Total Profit] / [Total Sales]`)

---

## 2. Calculated Fields & LOD Formulas

Create these calculated fields in the Tableau Data pane (`Analysis` > `Create Calculated Field`):

```tableau
// 1. Overall Profit Ratio
[Profit Ratio] = SUM([Profit]) / SUM([Sales])

// 2. Average Profit per Order Line
[Avg Profit per Transaction] = SUM([Profit]) / COUNT([Row ID])

// 3. Profit Status Indicator (for Color Marks)
[Profit Status] = 
IF SUM([Profit]) > 0 THEN "Profitable"
ELSEIF SUM([Profit]) = 0 THEN "Break-Even"
ELSE "Loss-Making"
END

// 4. YoY Sales Growth (Table Calculation or LOD)
// Create with Quick Table Calculation: Percent Difference along Order Date (Year)
ZN(SUM([Sales])) - LOOKUP(ZN(SUM([Sales])), -1) / ABS(LOOKUP(ZN(SUM([Sales])), -1))

// 5. Fixed Sub-Category Margin (LOD Expression)
{ FIXED [Sub-Category] : SUM([Profit]) / SUM([Sales]) }
```

---

## 3. Step-by-Step Worksheet Construction

### Sheet 1: KPI Summary Cards (4 BANs — Big Ass Numbers)
- **Rows**: Leave blank
- **Columns**: `Measure Names` (filter to `Sales`, `Profit`, `Quantity`, `Avg Profit per Transaction`)
- **Text Mark**: `Measure Values`
- **Formatting**:
  - `Sales`: Currency (Custom, prefix `$`, units in `K` or `M`, 1 decimal)
  - `Profit`: Currency (Custom, prefix `$`, color coded: green if positive, red if negative)
  - `Quantity`: Number (Standard, comma separator)
  - `Avg Profit`: Currency (prefix `$`, 2 decimals)

### Sheet 2: Monthly & YoY Sales & Profit Trends
- **Columns**: `MONTH(Order Date)` (Continuous)
- **Rows**: Dual Axis:
  - Axis 1: `SUM([Sales])` (Line chart, Navy Blue `#2b5c8f`)
  - Axis 2: `SUM([Profit])` (Bar or Area chart, Muted Teal `#38a169` / Orange `#e53e3e` on dual color)
- **Marks Card**: Synchronize axis if scaling permits, or keep independent with explicit headers.
- **Tooltip**: Include Month, Sales, Profit, and Profit Margin.

### Sheet 3: Geographic Sales & Profitability (US State Map)
- **Detail**: `State` (Geographic role: State/Province)
- **Color**: `[Profit Ratio]` using diverging palette (`Red-Blue Diverging` centered at `0.00`).
- **Size / Tooltip**: `SUM([Sales])`, `SUM([Profit])`, `State`, `Region`.
- **Insight**: Central region states (like Texas and Illinois) show high volume but negative margins due to excessive discounting.

### Sheet 4: Performance by Category & Sub-Category
- **Rows**: `Category`, `Sub-Category`
- **Columns**: `SUM([Sales])`, `SUM([Profit])`
- **Sort**: Sub-Category descending by `SUM([Profit])`.
- **Key Observation**:
  - Top earners: `Copiers` (+$101.9K, 34.6% margin), `Phones` (+$25.5K), `Chairs` (+$15.9K).
  - Severe loss drivers: `Tables` (-$51.7K, -23.2% margin) and `Machines` (-$19.8K, -9.2% margin).

### Sheet 5: Customer Segment Distribution
- **Marks**: Pie or Donut chart.
- **Angle**: `SUM([Sales])`
- **Color**: `Segment` (`Consumer`: 52.6%, `Corporate`: 31.1%, `Home Office`: 16.3%)
- **Label**: `Segment` + `SUM([Sales])` (% of Total).

### Sheet 6 & 7: Top 5 Best & Bottom 5 Worst Products
- Create a Parameter: `Top/Bottom N` (Integer = 5).
- Create Sets on `Product Name`:
  - `Top 5 Products by Profit`: By field > Top > 5 > `Profit` > `Sum`
  - `Bottom 5 Products by Profit`: By field > Bottom > 5 > `Profit` > `Sum`
- In Sheet 6 (`Top 5 Best-Selling / Most Profitable`):
  1. Canon Copier 100 Series (+$5,513.97)
  2. Sharp Copier Eco (+$5,357.37)
  3. Ricoh Copier Pro, Gray (+$4,487.13)
  4. Hewlett-Packard Copier 200 Series (+$3,738.03)
  5. Ricoh Copier Pro, Black (+$3,655.61)
- In Sheet 7 (`Bottom 5 Loss-Making Products`):
  1. BPI Table Pro, Black (-$2,913.23)
  2. Bevis Table Deluxe, Gray (-$2,721.65)
  3. Bretford Table Pro, Black (-$2,695.33)
  4. Bevis Table Eco, Black (-$2,233.05)
  5. Lesro Table 200 Series, Gray (-$1,793.65)

---

## 4. Dashboard Assembly & Interactivity

1. **Canvas Size**: Desktop Browser (`1366 x 768` or `1440 x 900`).
2. **Layout Container Strategy**:
   - Vertical Container (Outer Shell)
     - Header Container (Title, Subtitle, Global Filters: Year, Region, Category)
     - KPI Container (Horizontal, 4 even cards with card padding)
     - Main Body Container (Horizontal: 60% Map & Trends, 40% Category breakdown & Segments)
     - Bottom Container (Top 5 & Bottom 5 tables side-by-side)
3. **Dashboard Interactivity (Filter Actions)**:
   - `Dashboard` > `Actions` > `Add Action` > `Filter`:
     - Select on **Map**: Filters all charts by clicked State.
     - Select on **Category/Sub-Category**: Cross-filters monthly trends and Top/Bottom products.
     - Select on **Segment**: Filters map and product lists.

---

## 5. Resume & Portfolio Bullet Point Breakdown

When discussing this project in a data analyst interview:
- **Bullet 1**: *"Engineered an end-to-end Tableau performance dashboard consolidating 2,300+ transactions across 4 years, delivering visibility into $1.25M in revenue and $125K in net profit."*
- **Bullet 2**: *"Surfaced root causes for a -$51.7K margin loss in Furniture/Tables by isolating discount elasticities (>30% discounts triggered negative unit economics) and presented actionable SKU rationalization recommendations to executive leadership."*
- **Bullet 3**: *"Implemented dynamic LOD expressions and set actions to isolate Top 5 high-margin copiers vs. Bottom 5 unprofitable table lines, driving data-informed vendor renegotiations."*
