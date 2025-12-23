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

## Visualization

<img width="892" height="497" alt="dashboard overview" src="https://github.com/user-attachments/assets/2bf4c546-237d-469b-9799-4a46a41cd506" />







