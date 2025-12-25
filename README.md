# Brazilian-E-Commerce-Sales-Analysis-SQL-Power-BI-
📌 Project Overview

This project presents an end-to-end data analytics workflow using the Olist Brazilian E-Commerce dataset. The goal was to transform raw transactional data into actionable business insights by applying SQL-based data modeling and Power BI visualization.

The project covers the full analytics lifecycle: data ingestion, cleaning, dimensional modeling (star schema), metric creation, and interactive dashboard development.


🎯 Business Objectives

- Analyze overall sales and revenue performance

- Understand customer purchasing behavior across regions

- Identify top-performing products and sellers

- Evaluate order fulfillment and customer satisfaction

- Provide a scalable analytics model for business decision-making


🗂️ Dataset

Source: Kaggle — Olist Brazilian E-Commerce Dataset

The dataset contains real anonymized data from Brazilian e-commerce orders, including:

- Customers
- Orders
- Order items
- Payments
- Reviews
- Products
- Sellers
- Geolocation
- Product category translations


🏗️ Data Modeling

A star schema was designed to support efficient analytics and BI reporting.

- Fact Table
- fact_orders
- order_id
- customer_id
- product_id
- seller_id
- price
- freight_value
- payment_value
- review_score
- order_status
- order timestamps
- Dimension Tables
- dim_customers – customer location and identifiers
- dim_products – product categories and physical attributes
- dim_sellers – seller location and identifiers
- dim_geolocation (optional) – geographic mapping support

 ## 🧹 Data Cleaning & Preparation (SQL)
 The raw Olist e-commerce dataset was imported into Microsoft SQL Server and systematically cleaned and prepared to ensure accuracy, consistency, and analytical readiness before visualization in Power BI.
 - Standardize types & handle missing values
   ALTER TABLE raw_orders ALTER COLUMN order_purchase_timestamp DATETIME;
DELETE FROM raw_orders WHERE order_id IS NULL;
- Remove duplicates

WITH cte AS (
  SELECT *, ROW_NUMBER() OVER (PARTITION BY order_id ORDER BY order_id) rn
  FROM raw_orders
)
DELETE FROM cte WHERE rn > 1;
- Create fact & dimension tables

SELECT o.order_id, o.customer_id, i.product_id, i.price
INTO fact_orders
FROM raw_orders o
JOIN raw_order_items i ON o.order_id = i.order_id;


Outcome
  - The cleaned and structured dataset was successfully loaded into Power BI, enabling the creation of an interactive Business Intelligence dashboard that provides insights into revenue trends, customer behavior, product performance, and geographic distribution across Brazil.

## 🛠️ Tools & Technologies
- SQL: Data cleaning, joins, transformations, and analysis
- Power BI: Data modeling, DAX measures, and dashboard creation

## Visualization

<img width="912" height="499" alt="dashboard overview" src="https://github.com/user-attachments/assets/41d9d5af-2c69-4f02-989b-0e7c0d2dad85" />




## 📌 Business Questions & Insights
How has revenue evolved over time?
- Total revenue of $16.64M shows clear seasonality, with sales peaking around mid-year and declining toward the later months.
- Business implication:
Marketing campaigns, inventory planning, and logistics capacity should be aligned with peak sales periods to maximize revenue and reduce operational bottlenecks.

Which product categories generate the most revenue?
- Insight:
Revenue is highly concentrated in a small number of product categories, with top categories collectively contributing the majority of the $16.64M total revenue.
- Business implication:
Prioritizing high-performing categories for promotions, pricing optimization, and supplier partnerships can significantly increase overall revenue.

 Which states generate the highest number of orders?
- Insight:
Customer orders (99,441 total orders) are concentrated in a few key states, particularly São Paulo (SP), followed by other major commercial regions.
- Business implication:
Strengthening logistics infrastructure and delivery efficiency in high-demand states can improve customer experience and reduce shipping costs.

 Who are the top-performing sellers?
- Insight:
A small group of sellers accounts for a disproportionately large share of the 99,441 total orders and $16.64M in revenue.
- Business implication:
Implementing retention and incentive programs for top sellers can stabilize revenue and reduce reliance on lower-performing sellers.

 What is the average order value (AOV)?
- Insight:
The average order value is $167.37, indicating moderate per-transaction spending across the platform.
- Business implication:
Upselling, cross-selling, and bundled offers could help increase AOV and maximize revenue without increasing customer acquisition costs.

Is there a relationship between delivery cost and customer review scores?
- Insight:
Despite high order volume, the average review score stands at 4.02, suggesting generally positive customer satisfaction, though delivery costs may still influence ratings.
- Business implication:
Optimizing shipping costs and delivery timelines could further improve customer satisfaction and long-term retention.

 How do order statuses impact revenue?
- Insight:
While total orders reached 99,441, cancelled or unavailable orders represent lost revenue opportunities.
- Business implication:
Reducing order cancellations through better inventory forecasting and seller reliability checks can directly improve realized revenue.

 Which product categories have the lowest customer satisfaction?
- Insight:
Some product categories consistently receive lower review scores compared to the overall average of 4.02.
- Business implication:
Targeted quality control and logistics improvements in low-rated categories can improve customer perception and reduce negative reviews.

 How is customer demand distributed geographically?
- Insight:
Customer demand is unevenly distributed across Brazil, with higher concentration in economically active states.
- Business implication:
Expanding logistics coverage and targeted marketing in underrepresented regions presents growth opportunities.

 Are customers making repeat purchases?
- Insight:
With 99,441 total customers and 99,441 total orders, repeat purchasing behavior appears limited.
- Business implication:
Introducing loyalty programs, personalized recommendations, and retention campaigns could significantly increase customer lifetime value.


## Recommendations

 - Prioritize high-revenue product categories by increasing marketing and inventory investment in top performers such as home, beauty, and lifestyle products.

 - Improve delivery performance to reduce late orders, as delivery delays are strongly linked to lower customer review scores.

 - Optimize seller performance by region by replicating best practices from high-performing states (e.g., São Paulo) across underperforming regions.

 - Leverage geographic insights to run targeted campaigns in low-penetration states and drive demand growth.

 - Increase average order value (AOV) through product bundling, cross-selling, and promotional incentives.



