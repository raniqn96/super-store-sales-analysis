# Superstore Sales & Operations Analysis — Executive Insights Report

**Role**: Senior Data Analyst  
**Focus**: Sales Operations, Revenue Optimization, and Assortment Rationalization  
**Dataset Time Horizon**: 2014 – 2017 (2,316 transactions across 48 US states)

---

## 1. Executive Summary

A comprehensive multi-dimensional sales performance analysis was conducted on Superstore's transactional data. While top-line sales demonstrated healthy historical momentum, reaching **$1,254,406.59** in cumulative gross sales and delivering **$125,234.86** in net operating profit (**9.98% overall profit margin**), deep operational inefficiencies and discount cannibalization were identified in specific product categories and regional markets.

### Key Performance Indicators (KPIs)
| Metric | Value | Business Context |
| :--- | :--- | :--- |
| **Total Gross Sales** | **$1,254,406.59** | 2,316 order line items across 760 active customer accounts |
| **Total Net Profit** | **$125,234.86** | Net contribution after discounts and baseline cost of goods |
| **Total Quantity Shipped** | **7,325 units** | Average basket size of 3.16 units per order line |
| **Average Profit / Order Line** | **$54.07** | High variance ($5,514 maximum to -$2,913 loss) |
| **Operating Profit Margin** | **9.98%** | Benchmark target: 12.5% |

---

## 2. Category & Sub-Category Performance

A breakdown by major category reveals that profit is heavily subsidized by Technology and Office Supplies, while Furniture is running at a significant net loss:

| Category | Sales | Profit | Margin (%) | Operational Status |
| :--- | :--- | :--- | :--- | :--- |
| **Technology** | $643,197.16 | $119,703.41 | **18.61%** | Core profit engine; highly resilient |
| **Office Supplies** | $158,894.20 | $30,799.06 | **19.38%** | Consistent cash generator across recurring supplies |
| **Furniture** | $452,315.23 | -$25,267.61 | **-5.59%** | Severe margin leakage; heavily discounted |

### Sub-Category Margin Leaders vs. Loss Drivers
1. **Top Profit Generators**:
   - **Copiers**: **$101,951.52 profit** on $294,977.50 sales (**34.6% margin**). Unmatched unit economics.
   - **Phones**: **$25,497.51 profit** on $94,546.30 sales (**27.0% margin**). High volume with stable demand.
   - **Chairs**: **$15,961.53 profit** on $131,657.10 sales (**12.1% margin**). The only profitable Furniture line.

2. **Severe Margin Drainers**:
   - **Tables**: **-$51,668.43 net loss** on $222,310.00 sales (**-23.2% margin**). Primary source of portfolio bleed.
   - **Machines**: **-$19,825.48 net loss** on $215,417.50 sales (**-9.2% margin**). High logistics and promotional overhead.

---

## 3. Top 5 Best-Selling vs. Bottom 5 Worst-Selling Products

### Top 5 Best Products (By Net Profit)
All top 5 performers originate from the enterprise Copier product line, combining premium ticket sizes with controlled discounting:
1. **Canon Copier 100 Series, White**: **+$5,513.97 profit** | $15,052.75 sales | 17 units
2. **Sharp Copier Eco, Gray**: **+$5,357.37 profit** | $13,066.76 sales | 14 units
3. **Ricoh Copier Pro, Gray**: **+$4,487.13 profit** | $10,944.23 sales | 11 units
4. **Hewlett-Packard Copier 200 Series, White**: **+$3,738.03 profit** | $10,895.48 sales | 13 units
5. **Ricoh Copier Pro, Black**: **+$3,655.61 profit** | $11,858.14 sales | 18 units

### Bottom 5 Worst Products (By Net Loss)
All bottom 5 underperformers are heavy commercial tables that suffered from steep promotional discounting (>40% to 70%):
1. **BPI Table Pro, Black**: **-$2,913.23 loss** | $11,102.04 sales | 21 units
2. **Bevis Table Deluxe, Gray**: **-$2,721.65 loss** | $5,574.12 sales | 14 units
3. **Bretford Table Pro, Black**: **-$2,695.33 loss** | $13,734.63 sales | 30 units
4. **Bevis Table Eco, Black**: **-$2,233.05 loss** | $3,072.70 sales | 12 units
5. **Lesro Table 200 Series, Gray**: **-$1,793.65 loss** | $4,030.38 sales | 13 units

---

## 4. Regional & Customer Segment Dynamics

### Geographic Distribution
- **South Region**: Highest operational efficiency at **13.10% profit margin** ($37,036.84 profit on $282,630.86 sales).
- **East Region**: Healthy margin at **10.67%** ($29,240.25 profit on $274,055.75 sales).
- **Central Region**: Highest total volume ($416,151.91 sales), but margin compressed to **9.43%** due to promotional aggressive pricing in Texas and Illinois.
- **West Region**: Lowest margin among territories at **7.00%** ($19,712.40 profit on $281,568.07 sales).

### Customer Segment Breakdown
- **Consumer**: 52.6% of sales ($659,613.15) | $68,017.71 profit (**10.31% margin**)
- **Corporate**: 31.1% of sales ($389,904.09) | $39,640.11 profit (**10.17% margin**)
- **Home Office**: 16.3% of sales ($204,889.35) | $17,577.04 profit (**8.58% margin**)

---

## 5. Strategic Analyst Recommendations

1. **Implement Hard Discount Ceilings on Furniture/Tables**:
   - Current analysis proves discounts exceeding 20% on Tables yield negative gross profit on 94% of transactions due to high freight costs.
   - Cap representative promotional discounts at 15% maximum for Furniture.
2. **Product Rationalization (SKU Pruning)**:
   - Delist or renegotiate supplier terms on the five chronic loss-making table models (BPI, Bevis, Bretford).
   - Reallocate warehouse floor space to high-velocity, high-margin Technology equipment (Copiers, Phones).
3. **Regional Margin Remediation in the West**:
   - Conduct state-level pricing reviews in California and Washington to bring Western margins (7.0%) in line with Southern operational benchmarks (13.1%).
