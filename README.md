# Superstore Sales Analysis — Project Package

A complete data analyst portfolio project: US retail sales data analyzed end-to-end, with a step-by-step Tableau dashboard build guide and a finished executive insights report.

---

## What's Inside

| File | Description |
| :--- | :--- |
| `Superstore_Sales_Data.csv` | The raw dataset — 2,316 order line items (2014–2017) across 48 US states |
| `Data_Dictionary.md` | Field-by-field definitions of the dataset and how each field feeds the Tableau analysis |
| `Tableau_Dashboard_Build_Guide.md` | Step-by-step instructions to reproduce the full Tableau dashboard |
| `Superstore_Sales_Executive_Report.md` | Finished analysis: KPIs, category performance, and recommendations |
| `Portfolio_Project_Summary.md` | One-page portfolio summary: key findings and Tableau skills demonstrated |
| `README.md` | This file |

---

## The Dataset

`Superstore_Sales_Data.csv` contains transactional sales records for a US office-supplies retailer.

**Key columns:**

- **Order info**: Order ID, Order Date, Ship Date, Ship Mode
- **Customer**: Customer ID, Customer Name, Segment (Consumer / Corporate / Home Office)
- **Geography**: City, State, Postal Code, Region
- **Product**: Product ID, Category (Technology / Office Supplies / Furniture), Sub-Category, Product Name
- **Measures**: Sales, Quantity, Discount, Profit

**Headline numbers (2014–2017):**

- Total Sales: **$1,254,406.59**
- Total Profit: **$125,234.86** (9.98% margin)
- Quantity Sold: **7,325 units**
- Avg Profit per Order Line: **$54.07**

---

## Tableau Dashboard Goals

The build guide walks you through creating an interactive executive cockpit for sales leadership:

1. **KPI summary cards** — Sales, Profit, Quantity, and Avg Profit per Transaction as big-number banners
2. **Monthly & YoY trends** — dual-axis sales/profit timeline to spot seasonality and growth
3. **Category & sub-category performance** — find margin leaks (e.g. Tables at -23.2% margin)
4. **Geographic distribution** — map sales and profit by state/region
5. **Discount impact analysis** — quantify how discounting cannibalizes profit

It includes the exact calculated fields and LOD expressions needed (Profit Ratio, Profit Status, YoY Growth, Fixed Sub-Category Margin) and works in Tableau Desktop or Tableau Public.

---

## How to Use

1. **Read the report first** — `Superstore_Sales_Executive_Report.md` gives you the findings and business context.
2. **Open the data** — import `Superstore_Sales_Data.csv` into Tableau (or Excel/Python) to explore.
3. **Build the dashboard** — follow `Tableau_Dashboard_Build_Guide.md` sheet by sheet to reproduce the analysis yourself.

---

*Prepared as a data analyst portfolio project. Dataset time horizon: 2014–2017.*
# super-store-sales-analysis
