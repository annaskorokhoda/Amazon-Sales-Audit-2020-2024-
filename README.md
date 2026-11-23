# Amazon-Sales-Audit-2020-2024
Сonducting an analysis of financial indicators to determine trends in the company's revenue and losses

---
## 📌 Project Overview
A comprehensive business audit of Amazon marketplace sales over a 5-year period (2020–2024) based on a dataset of 100,000 orders. The goal of this project is to evaluate actual net revenue dynamics, identify key sources of financial loss (cancellations, returns, ineffective discounting), analyze customer loyalty, and build an interactive tool for granular sales exploration.

---
## 🛠 Tech Stack
PostgreSQL (pgAdmin): data storage, KPI calculations, CTEs, window functions (LAG, OVER), conditional aggregation (CASE WHEN), and correlation analysis (CORR).   
Power BI: interactive visualization, Decomposition Tree, dynamic Field Parameters, custom Tooltips, and dynamic page navigation to detailed tables.   

---
## 📈 Interactive Dashboard (Power BI)
Designed in a dark Amazon-inspired theme, the dashboard centers around an interactive Decomposition Tree that breaks down total turnover ($91.83M) across the Country → City → Category → Brand hierarchy.   
Dynamic Metric Switching: Powered by Field Parameters, allowing users to seamlessly toggle between Avg shippingCost, Quantity, Revenue, and Sales.
Custom Tooltips: Hovering over any category reveals granular details including TotalAmount, Quantity, and Tax.   

---
## 🔍 Key SQL Analysis Results
* **MetricValueGross Turnover** $91,825,647.92   
* **Net Revenue** $68,372,677.10 (74,628 orders)   
* **Lost Revenue** $5,631,784.85 (6,077 orders)  
* **Repeat Customer Rate** 57.00%    
* **discount ↔ quantity Correlation** 0.0028 (no linear relationship)   

**Core Business Insights:**
  *Revenue Dynamics & Seasonality:* An analysis of Amazon sales from 2020 to 2024 reveals that the highest number of orders and net revenue occurred in 2020. A decline followed over the next four years. This trend is attributed to a significant surge in demand for online shopping in 2020, driven by global lockdowns, which prompted a large number of consumers to shift from offline to online retail. The year 2021 saw the sharpest drop in revenue, as quarantine measures ended and customers returned to brick-and-mortar stores. In 2022, both the average transaction value and company profitability increased compared to the previous period. This stands in contrast to 2023 and 2024, during which net revenue figures were negative, albeit only slightly.
  Overall, sales declined in 2021, 2023, and 2024. The loss of revenue following the end of the lockdowns—a period when online retail was the primary driver—is a logical consequence of the resumption of normal offline retail operations and does not necessarily indicate a destructive trend. Nevertheless, it is worth investigating the underlying causes of the negative revenue growth rates.
  Peak revenue months are consistently January ($5.98M), May ($5.91M), and August ($5.84M), while February sees the sharpest dip ($5.23M).

  *Losses from Cancellations & Returns:* Revenue loss occurs following order cancellations or returns. The share of revenue from returns is 0.34% higher. However, the primary driver of revenue loss is order cancellations, which result in a shortfall of $2,851,122.39—an amount $70,459.93 greater than the loss associated with orders marked as "returned."
  Breaking down losses by category, the highest figures are found in Home & Kitchen (6.27%), Toys & Entertainment (6.09%), and Books (6.11%). It is also worth noting the categories of Clothing (5.91%), Electronics (6.05%), and Sports (6.04%).
  When examining losses by payment method, the highest number of declines was observed with credit and debit card payments. Conversely, Cash on Delivery shows the lowest level of losses in monetary terms.

  *High-Risk Sellers:* Order cancellations or returns occur most frequently with sellers such as SELL 011062, SELL00191, SELL00156, SELL01533, SELL00642, SELL01444, SELL01852, SELL011472, SELL01239, and SELL00050. It is recommended that the company investigate the reasons behind these occurrences and consider reviewing the terms of cooperation with specific counterparties—namely, SELL 011062 and SELL01472. These particular sellers account for the highest value of lost revenue, amounting to over 11,000 USD.

  *Discount Ineffectiveness:* An analysis of the relationship between discounts and the average number of items per receipt revealed that these variables do not have a direct positive influence on each other. In fact, as the discount percentage increases, the average number of items purchased actually decreases. Consequently, such actions only result in a loss of profit for the company.
  `discount` and `quantity` = 0.0028 — there is no correlation at all. This mathematically supports a business conclusion: larger discounts do not encourage customers to purchase more units of a product.
  `discount` and `total_amount` = -0.1053 — a weak negative correlation. The larger the discount, the lower the final transaction amount (the discount simply "eats up" a portion of the revenue).
  `unit_price` and `quantity` = 0.0058 — no correlation: on average, customers purchase the same number of units regardless of whether the product is inexpensive or expensive.
  `shipping_cost` and `total_amount` = 0.0387 — shipping costs are practically independent of the order total.

  *Customers & Geography:* 57% of customers are repeat buyers. The United States leads in net revenue ($47.94M), followed by India ($10.38M). AOV ($907.56–$918.08) and shipping cost share (0.81%–0.82%) remain consistent across all 5 markets.

---
## 🚀 Business Recommendations
* *Restructure Discount Policy:* Replace unconditional 20%–30% discounts with threshold-based promotions (e.g., discounts on orders of 4+ units) to actively drive basket size growth.   
* *Audit Underperforming Sellers:* Review partner terms and enforce SLA thresholds for sellers exceeding a 15% failure rate (prioritizing SELL01062 and SELL01472).   
* *Boost Low-Season Demand:* Launch targeted retention campaigns for the 43% one-time buyer segment (16,672 customers) in February to smooth seasonal revenue dips.   
