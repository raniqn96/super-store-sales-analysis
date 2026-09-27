# Superstore Sales Data — Data Dictionary

**File**: `Superstore_Sales_Data.csv` · **Rows**: 2,316 order line items · **Period**: 2014–2017 · **Grain**: one row = one product line within one order

---

## Field Definitions

### Identifiers & Dates

| # | Field | Type | Description | Example | Intended Use in Tableau |
| :-- | :--- | :--- | :--- | :--- | :--- |
| 1 | `Row ID` | Integer | Unique sequential ID for each order line | `1` | Not for analysis; use only to guarantee row uniqueness when blending or deduplicating |
| 2 | `Order ID` | String | Unique identifier for the parent sales order | `US-2017-000001` | Order-level aggregation (COUNTD) to compute orders per customer/period |
| 3 | `Order Date` | Date (ISO) | Date the order was placed | `2017-04-12` | Primary time axis: monthly/YoY trend lines, seasonality, Tableau date hierarchy |
| 4 | `Ship Date` | Date (ISO) | Date the order shipped | `2017-04-17` | Derived field: `Shipping Days = Ship Date − Order Date` for fulfillment-speed analysis |

### Fulfillment

| # | Field | Type | Description | Example | Intended Use in Tableau |
| :-- | :--- | :--- | :--- | :--- | :--- |
| 5 | `Ship Mode` | String | Shipping class chosen by the customer | `Standard Class` | Color/faceting on fulfillment analysis; compare delivery speed vs. profitability |

### Customer

| # | Field | Type | Description | Example | Intended Use in Tableau |
| :-- | :--- | :--- | :--- | :--- | :--- |
| 6 | `Customer ID` | String | Unique customer account identifier | `john-1514` | COUNTD for active accounts (760 total); customer-level ranking |
| 7 | `Customer Name` | String | Customer's full name | `John Williams` | Drill-down detail in customer tables; use ID for joins (names may repeat) |
| 8 | `Segment` | String | Customer type: Consumer, Corporate, or Home Office | `Consumer` | Segment share-of-sales and margin comparison (see report §4) |

### Geography

| # | Field | Type | Description | Example | Intended Use in Tableau |
| :-- | :--- | :--- | :--- | :--- | :--- |
| 9 | `Country` | String | Country of sale (constant: United States) | `United States` | Not analytically useful; safe to exclude from views |
| 10 | `City` | String | Shipping destination city | `Seattle` | Detail-level drill-down under state |
| 11 | `State` | String | US state of destination | `Washington` | Symbol/filled map (assign State to geographic role); state-level margin review |
| 12 | `Postal Code` | Integer | US ZIP code of destination | `35730` | Fine-grained mapping; cast to String in Tableau to avoid numeric aggregation |
| 13 | `Region` | String | US census region: East, West, Central, or South | `West` | Region-level margin dashboard panel (report §4) |

### Product

| # | Field | Type | Description | Example | Intended Use in Tableau |
| :-- | :--- | :--- | :--- | :--- | :--- |
| 14 | `Product ID` | String | Unique product/SKU identifier (encodes category) | `OFF-ART-6669` | SKU-level ranking, top/bottom product analysis |
| 15 | `Category` | String | Top-level product class: Technology, Office Supplies, or Furniture | `Office Supplies` | Primary category drill-down; core profit-engine comparison (report §2) |
| 16 | `Sub-Category` | String | Second-level product grouping (17 values, e.g. Copiers, Tables) | `Art` | LOD expression `FIXED Sub-Category Margin`; sub-category bar charts |
| 17 | `Product Name` | String | Full product display name | `Sanford Sketch Book Deluxe, Multicolor` | Detail labels in top/bottom 5 product lists; not for grouping (long names) |

### Measures

| # | Field | Type | Description | Example | Intended Use in Tableau |
| :-- | :--- | :--- | :--- | :--- | :--- |
| 18 | `Sales` | Decimal | Line revenue in USD after discount | `162.63` | SUM for all revenue KPIs; dual-axis trend with Profit |
| 19 | `Quantity` | Integer | Units sold on the line | `9` | SUM for units KPI; basket-size (avg per order) calculations |
| 20 | `Discount` | Decimal | Discount rate applied, 0–0.8 | `0.2` | Discount-impact scatter/bins; core of profit-cannibalization analysis |
| 21 | `Profit` | Decimal | Net profit in USD after COGS and discount (can be negative) | `73.18` | SUM for profit KPIs; ratio `SUM(Profit)/SUM(Sales)` for Profit Ratio |

---

## Calculated Fields Used in the Dashboard

Defined in full in `Tableau_Dashboard_Build_Guide.md`:

| Calculated Field | Formula | Purpose |
| :--- | :--- | :--- |
| **Profit Ratio** | `SUM([Profit]) / SUM([Sales])` | Margin % at any level of the hierarchy |
| **Profit Status** | `IF [Profit] < 0 THEN 'Loss' ELSE 'Profitable' END` | Binary coloring on maps and bars |
| **YoY Growth** | `(SUM([Sales]) - LOOKUP(SUM([Sales]), -1)) / LOOKUP(SUM([Sales]), -1)` | Year-over-year trend annotation |
| **Fixed Sub-Category Margin** | `{ FIXED [Sub-Category] : SUM([Profit]) / SUM([Sales]) }` | Stable sub-category margins regardless of view filters |

## Data Notes & Caveats

- **Grain matters**: sales and profit must always be summed (`SUM`), never averaged, to match the headline figures.
- **Postal Code** ships as a number; cast to String and assign the ZIP Code geographic role before mapping.
- **Negative Profit** values are legitimate — they represent loss-making lines and drive the Tables/Machines findings.
- **Dates** are ISO `YYYY-MM-DD`; Tableau parses them automatically. Use `Order Date` (not Ship Date) for revenue timelines.
