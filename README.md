# 🛍️ Customer Shopping Behavior Analysis | End-to-End Data Analytics Project

![Python](https://shields.io)
![SQL Server](https://shields.io)
![Power BI](https://shields.io)

## 📌 Project Overview
This end-to-end data analytics project explores **3,900 customer transactions** generating **\$233,081 in total revenue** to uncover key drivers of sales, customer loyalty, product performance, and operational bottlenecks. 

The workflow covers the complete data lifecycle: **Data Cleaning & Feature Engineering in Python**, **Database Storage & Business Querying in MS SQL Server**, and **Interactive Executive Reporting in Power BI**.

---

## 🎯 Business Problem
Retail decision-makers lacked a unified view of customer purchasing patterns and satisfaction drivers. Key challenges included:
* **Unclear Revenue & Loyalty Drivers:** Difficulty identifying which demographic segments and product categories drive repeat business.
* **Subscription & Retention Gaps:** Low overall subscription rate (**27%**) without clear visibility into why certain segments fail to subscribe.
* **Customer Satisfaction Bottlenecks:** A moderate overall review rating (**3.75 / 5.0**) requiring root-cause analysis across product categories, shipping methods, and payment gateways.

---

## 🛠️ Tech Stack & Workflow

### 1. Data Cleaning & Feature Engineering (`Python - Pandas & SQLAlchemy`)
* **Missing Value Imputation:** Identified **37 missing values** in `Review Rating` and imputed them using the **category-specific median** (`groupby('Category')`) to preserve data distribution accuracy.
* **Standardization:** Converted column names to clean `snake_case` formatting for seamless SQL integration.
* **Feature Engineering:**
  * Created `age_group` (`Young Adult`, `Adult`, `Middle Age`, `Senior`) using quantile-based discretization (`pd.qcut`).
  * Mapped text-based purchase frequencies (`Weekly`, `Fortnightly`, `Monthly`, etc.) into numeric `purchase_frequency_days`.
* **Redundancy Removal:** Verified a 100% match between `discount_applied` and `promo_code_used` and dropped the redundant column.
* **ETL Pipeline:** Loaded the cleaned dataset directly into **MS SQL Server** (`customer_behavior1` database) using `SQLAlchemy` and `pyodbc`.

### 2. Business Analysis (`MS SQL Server`)
Answered **10 targeted business questions** using advanced SQL techniques including **CTEs**, **Subqueries**, **Conditional Aggregation**, and **Window Functions (`ROW_NUMBER`)**:
1. **Revenue by Gender:** Compared total revenue contribution between male and female shoppers.
2. **High-Value Discount Users:** Identified discount users spending at or above the store's average order value.
3. **Top-Rated Products:** Ranked the top 5 products by average review rating.
4. **Shipping Spend Comparison:** Contrasted average purchase amounts between `Standard` and `Express` shipping.
5. **Subscription Impact:** Evaluated customer count, average spend, and total revenue across subscription statuses.
6. **Discount Dependency:** Calculated the percentage of discounted purchases per product to identify discount-reliant items.
7. **Customer Segmentation:** Classified customers into `New` (1 purchase), `Returning` (2–10 purchases), and `Loyal` (>10 purchases) using CTEs and `CASE` statements.
8. **Category Best-Sellers:** Used `ROW_NUMBER() OVER (PARTITION BY category ...)` to rank the top 3 best-selling items within each category.
9. **Repeat Buyer Subscriptions:** Analyzed subscription adoption among frequent buyers (`previous_purchases > 5`).
10. **Revenue by Age Group:** Ranked demographic age segments by total revenue contribution.

### 3. Interactive Visualization (`Power BI`)
Built an executive dashboard featuring dynamic KPI cards, demographic breakdowns, top-10 product rankings, and interactive slicers (`Subscription Status`, `Gender`, `Category`, `Shipping Type`, `Payment Method`) with a one-click **Reset** bookmark.

---

## 📊 Dashboard Preview
> **Note:** Replace the placeholder below with screenshots of your Power BI dashboard (e.g., Overview & Filtered Subscription view).

![Dashboard Overview](assets/dashboard_overview.png)

---

## 💡 Key Insights & Findings
* **100% Male Subscription Skew (Critical Gap):** Only **27%** of customers (1,053) are subscribed, and **100% of them are male**. Female shoppers represent **0% of subscribers** despite contributing **32.26% of revenue** and having a higher average order value (**\$60.25** vs. **\$59.54** for males). This leaves the business without a direct retention channel for high-spending female customers.
* **Male Gifting Behavior:** Male shoppers generate **67.74% of total revenue (\$157,890)**, with female-oriented items like `Dress`, `Jewelry`, and `Scarf` ranking among their top purchases—strongly indicating gifting or household purchasing behavior.
* **Category Quality vs. Volume Trade-off:** `Clothing` drives **44.7% of revenue (\$104,264)** but records the **lowest satisfaction rating (3.72)**. Conversely, `Footwear` achieves the **highest rating (3.79)** and highest average spend (**\$60.26**) with a smaller customer base.
* **Logistics & Payment Friction:** `Standard` shipping yields the highest satisfaction (**3.82**), whereas `Store Pickup` (**3.71**) and `Next Day Air` (**3.72**) underperform—indicating fulfillment delays that negatively affect subscribers. Similarly, `Credit Card` payments lead in revenue and satisfaction (**3.79**), while `Bank Transfer` lags behind (**3.70**).

---

## 🚀 Strategic Recommendations
1. **Launch a Female-Focused Loyalty Campaign:** Introduce targeted checkout incentives (e.g., instant discounts or free shipping on `Blouse` and `Jewelry`) to convert high-AOV female shoppers into subscribers.
2. **Audit `Clothing` Quality & Sizing:** Investigate customer feedback on top-selling clothing items to address sizing/material issues and raise the category rating above **4.2**.
3. **Capitalize on Male Gifting Seasons:** Introduce gift-wrapping options, curated gift bundles, and seasonal campaigns targeting male shoppers.
4. **Optimize Pickup & Express Fulfillment:** Create dedicated express counters for `Store Pickup` orders and review carrier SLAs for `Next Day Air` deliveries.
5. **Scale `Footwear` Marketing & Streamline Payments:** Increase ad spend on high-performing `Footwear` items and automate `Bank Transfer` verification (or incentivize card payments) to reduce checkout friction.

---

## 📁 Repository Structure
```text
├── data/
│   └── customer_shopping_behavior.csv       # Raw dataset
├── notebooks/
│   └── Customer_Shopping_Behavior.ipynb     # Python data cleaning & SQL ETL script
├── sql/
│   └── customer_behavior_queries.sql        # 10 analytical SQL queries
├── powerbi/
│   └── Customer_Behavior_Dashboard.pbix     # Interactive Power BI dashboard
└── README.md                                # Project documentation
```

---

## 📬 Contact
* **LinkedIn:** [Your LinkedIn Profile](https://linkedin.com)
* **GitHub:** [Your GitHub Profile](https://github.com)
