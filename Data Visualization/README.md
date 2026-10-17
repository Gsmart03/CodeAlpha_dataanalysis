# 📊 Data Visualization Task — CodeAlpha Internship
## Nigerian E-Commerce Sales Dataset (2025)

**Analyst:** Abdulsobur Adebayo

**Tool:** Tableau 

**Dataset:** codealpha_task2_3_sales_eda_visualization.csv (1,500 rows)

**Deliverable:** Interactive dashboard + data story + portfolio-ready visuals

---

## 📑 Table of Contents

1. Project Brief
2. Data Overview & Key Numbers
3. Design System
4. 8 Core Visuals Plan
5. Tableau Build Guide (Step-by-Step)
6. Dashboard Layout
7. The Data Story (5 Acts)
8. Portfolio Packaging for GitHub
9. Deliverables Checklist

---

### 1. Project Brief
The Data Visualization task requires five things. Here's how this project delivers each:

Requirement |	Delivered By
------------| --------------
Transform raw data into visuals|	8 chart types: KPI cards, line, bar, map, donut, grouped bar, treemap, scatter
Use Tableau	| Full step-by-step Tableau Desktop build guide
Design visuals| that reveal insights	Consistent color system, chart-selection matrix, data-ink ratio
Craft compelling data stories|	5-act narrative with executive call-to-action
Build a portfolio	|GitHub repo structure + Tableau Public link + screenshots

---

### 2. Data Overview & Key Numbers
**Dataset Snapshot**
- 1,500 orders across 2025 (Jan 1 → Dec 31)
- 5 categories: Mobile, Computers, Accessories, Storage, Wearables
- 10 regions: Lagos, Abuja, Rivers, Kano, Oyo, Enugu, Kaduna, Ogun, + 2 Unknown
- 4 sales channels: Online, Retail Store, Marketplace, Corporate Sales
- 5 payment methods: Card, Cash, Bank Transfer, USSD, Mobile Money
- 4 order statuses: Completed, Pending, Cancelled, Returned

Pre-Visualization Calculated Fields (Tableau)
I created these before building charts:

`// Core Metrics
[Revenue]        = SUM([revenue])
[Profit]         = SUM([profit])
[Total Cost]     = SUM([cost])
[Orders]         = COUNTD([order_id])`

// Derived Ratios
[Profit Margin %] = SUM([profit]) / SUM([revenue])
[AOV]             = SUM([revenue]) / COUNTD([order_id])
[Completion Rate] = 
  COUNTD(IF [order_status] = 'Completed' THEN [order_id] END) / COUNTD([order_id])

// Time Dimensions
[Order Month]     = DATETRUNC('month', [order_date])
[Order Quarter]   = DATETRUNC('quarter', [order_date])

// Discount Band
[Discount Band] =
IF [discount_rate] = 0 THEN 'No Discount'
ELSEIF [discount_rate] <= 0.05 THEN 'Low (≤5%)'
ELSEIF [discount_rate] <= 0.10 THEN 'Medium (6–10%)'
ELSEIF [discount_rate] <= 0.15 THEN 'High (11–15%)'
ELSE 'Very High (>15%)'
END

// Profit Status Flag
[Profit Status] = IF [profit] < 0 THEN 'Loss' ELSE 'Profit' END

// Order Outcome
[Order Outcome] =
IF [order_status] = 'Completed' THEN 'Completed' ELSE 'Leakage' END
