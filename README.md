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

1. Data Type Standardization
  - Converted columns imported as text to appropriate numeric and date data types.
  - Ensured monetary values (price, freight_value, payment_value) were stored as DECIMAL.
  - Converted date fields (order_purchase_timestamp, order_delivered_customer_date, order_estimated_delivery_date) to DATETIME.
  Purpose:
  - Prevents calculation errors and ensures accurate aggregations in Power BI.

2. Handling Missing and Invalid Values
  - Identified and handled NULL values in key fields such as:
  - Customer location
  - Product weight and dimensions

  Review scores
  - Excluded records with missing primary keys (order_id, customer_id).
  - Retained valid incomplete records where business logic allowed (e.g., undelivered orders).

  Purpose:
  - Preserves data integrity while avoiding unnecessary data loss.

3. Duplicate Record Removal
  - Removed duplicate rows using primary key checks and row number logic.

Ensured uniqueness across:
  - Orders
  - Customers
  - Sellers
  - Products

  Purpose:
  - Prevents inflated KPIs such as total revenue and order count.
4. Creation of Fact and Dimension Tables
  - The dataset was transformed into a star schema for efficient analysis.
  - Fact Table
  - fact_orders
  - order_id
  - customer_id
  - seller_id
  - product_id
  - payment_value
  - order_status
  - purchase_date
  - delivery_date

Dimension Tables
  - dim_customers – customer demographics and location
  - dim_products – product attributes and categories
  - dim_sellers – seller location details
  - dim_payments – payment type and installment data
  - dim_reviews – customer review scores and feedback
  - dim_date – derived calendar attributes (year, month, day)

  Purpose:
  - Optimizes Power BI performance and enables clear relationship modeling.

5. Data Enrichment & Feature Engineering
  - Translated product category names from Portuguese to English using lookup tables.
  - Derived additional fields such as:
  - Order delivery delay (actual vs estimated)
  - Order month and year for time-series analysis
  - Created calculated fields for analytics readiness.

  Purpose:
  - Improves interpretability and supports business-level insights.

6. Referential Integrity Enforcement
  - Established primary and foreign key relationships between fact and dimension tables.
  - Validated joins to ensure no orphan records exist.

  Purpose:
  - Ensures reliable slicing and filtering across dashboards.

7. Validation & Quality Checks
  - Verified row counts before and after transformation.
  - Cross-checked total revenue and order counts against raw data.
  - Ensured no negative or unrealistic values exist in numeric fields.

  Purpose:
  - Guarantees analytical accuracy and stakeholder confidence.

Outcome
  - The cleaned and structured dataset was successfully loaded into Power BI, enabling the creation of an interactive Business Intelligence dashboard that provides insights into revenue trends, customer behavior, product performance, and geographic distribution across Brazil.

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

## 🛠️ Tools & Technologies
- SQL
- Power BI

