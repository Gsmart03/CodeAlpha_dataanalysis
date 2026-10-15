# Tasks One Executive Summary: E-Commerce Sales Transactions EDA
## 1. Project Objective
To perform a comprehensive Exploratory Data Analysis (EDA) on a year's worth of Nigerian e-commerce sales data. The goal was to uncover revenue trends, evaluate regional and channel performance, test business hypotheses regarding discounts and seasonality, and identify critical data quality issues to inform strategic business decisions.

## 2. Methodology
The analysis followed a structured five-step framework:
1. **Ask Meaningful Questions:** Defined key business questions around revenue, seasonality, customer behavior, and data quality.
2. **Explore Data Structure:** Profiled the dataset (1,500 records, 15 columns) to understand schema, distinct values, and date ranges.
3. **Identify Trends & Anomalies:** Analyzed revenue by category, region, sales channel, and month. Detected negative profits and extreme discounts.
4. **Test Hypotheses:** Validated four core assumptions (H1–H4) using SQL aggregations.
5. **Detect Data Quality Issues:** Checked for NULLs, duplicates, inconsistent casing, and invalid ranges.

## 3. Key Findings (Verified Against Data)

**📈 Revenue & Product Performance**
- **Total Revenue:** ₦711.9M across 1,500 orders.
- **Top Categories:** Computers (₦366.2M, 51.4%) and Mobile (₦226.6M, 31.8%) dominate, accounting for **83.3%** of total revenue.
- **Order Frequency:** Accessories lead in order volume (519 orders) but contribute only 7.6% of revenue.
- **Profitability:** Computers and Mobile also lead in total profit, with profit margins ranging from 20.7% to 22.4% across categories.

**🌍 Regional Performance**
- **Lagos** is the dominant region (418 orders, ₦203.2M revenue), followed by **Abuja** (187 orders, ₦86.7M).
- **Underserved Regions:** Oyo (₦56.4M), Kaduna (₦61.3M), and Kano (₦70.8M) show significant untapped potential.
- **Data Anomaly:** 3 orders have a missing region (labeled "Unknown"), contributing ₦424K.

**🛒 Sales Channel Analysis**
- **Online** leads in order volume (577 orders).
- **Retail Store** has the highest Average Order Value (AOV) at ₦546,244, followed by Corporate Sales (₦462,811).
- **Data Quality Issue:** A duplicate "Online" row appeared with only 2 orders and a much lower AOV (₦260K), indicating a potential data entry inconsistency (likely trailing whitespace).

**📅 Seasonality & Trends**
- **Monthly Revenue:** Revenue is relatively flat across the year. Q4 (Oct–Dec) does **not** show a significant spike; in fact, March (₦62.8M) and August (₦72.6M) were the strongest months.
- **Q4 Revenue:** ₦183.8M, which is comparable to Q1 (₦177.9M).

**💸 Discount Impact (Hypothesis Testing)**
- **H1 (Discounts increase quantity):** **REJECTED.** Orders with "No Discount" had the highest average quantity (2.24), while "Very High (>15%)" discounts had the lowest (2.07).
- **H2 (Q4 generates higher revenue):** **REJECTED.** Q4 was not significantly higher than other quarters.
- **H3 (Corporate Sales has highest AOV):** **REJECTED.** Retail Store had the highest AOV.
- **H4 (Mobile dominates revenue):** **REJECTED.** Computers dominate revenue (51.4%), not Mobile.

**⚠️ Data Quality & Anomalies**
- **Missing Values:** 3 NULL regions, 2 NULL quantities.
- **Negative Profits:** Multiple loss-making orders identified, primarily driven by high discounts (15–20%) on Laptops, Smartphones, and External SSDs. Example: ORD00069 (Laptop) lost ₦69,194.
- **Duplicates:** No duplicate `order_id` values found.
- **Inconsistent Categorical Values:** No case-sensitivity issues detected in product names.

## 4. Strategic Recommendations

**🛠️ Data Engineering**
1. **Enforce Schema Validation:** Apply `NOT NULL` constraints on `region` and `quantity`, and `CHECK` constraints on `discount_rate` (0–1).
2. **Standardize Text Fields:** Use `TRIM()` and consistent casing for `sales_channel` to eliminate duplicate entries like the "Online" anomaly.
3. **Recalculate Financials:** Audit and recompute `revenue` and `profit` fields to ensure formula consistency.

**📊 Business Strategy**
1. **Re-evaluate Discount Strategy:** Since discounts do not increase order quantity and directly cause negative profits, **cap discounts at 10%** or eliminate them entirely for high-margin electronics.
2. **Investigate Q4 Flatness:** Q4 did not spike as expected. Investigate potential stockouts, increased competition, or reduced marketing spend during Oct–Dec.
3. **Focus on Underserved Regions:** Launch targeted campaigns in Oyo, Kaduna, and Kano to capitalize on untapped demand.
4. **Leverage Retail & Corporate Channels:** These channels have the highest AOV. Prioritize corporate partnerships and retail expansion.
5. **Address Order Leakage:** ~25–30% of orders are Cancelled, Returned, or Pending. Investigate logistics and customer service issues.

## 5. Conclusion
This EDA reveals a business with strong revenue concentration in Computers and Mobile, but significant operational and data quality challenges. The most critical finding is that **discounts are destroying profit without increasing sales volume**. Additionally, the expected Q4 holiday spike did not materialize. By addressing data hygiene issues and re-strategizing discounts, the business can protect margins and unlock growth in underserved regions.

---

# Task two DATA VISTUALIZATION 
