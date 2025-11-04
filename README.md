# 🛒 Blinkit Data Analysis (SQL Project)

![SQL](https://img.shields.io/badge/Language-SQL-blue?style=for-the-badge)
![Tool](https://img.shields.io/badge/Tool-Microsoft%20SQL%20Server-red?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

---

## 📖 Overview
This project focuses on analyzing **Blinkit’s retail dataset** using **Structured Query Language (SQL)** to extract meaningful business insights.  
The analysis covers **data cleaning, KPI generation, sales breakdowns, and pivot-based summaries**, providing a complete data-driven view of outlet performance and sales patterns.

---

## 🧹 Data Cleaning
Data quality and consistency were ensured by standardizing categorical fields.  
Example — fixing inconsistent values in `Item_Fat_Content`:

```sql
UPDATE blinkit_data
SET Item_Fat_Content = 
    CASE 
        WHEN Item_Fat_Content IN ('LF', 'low fat') THEN 'Low Fat'
        WHEN Item_Fat_Content = 'reg' THEN 'Regular'
        ELSE Item_Fat_Content
    END;
#KPI'S
| KPI                              | Description                   | Query Used         |
| -------------------------------- | ----------------------------- | ------------------ |
| 💰 **Total Sales (in Millions)** | Overall sales performance     | `SUM(Total_Sales)` |
| 📦 **Average Sales**             | Mean sales per item           | `AVG(Total_Sales)` |
| 🛍️ **Number of Items Sold**     | Total orders/items            | `COUNT(*)`         |
| ⭐ **Average Rating**             | Product performance by rating | `AVG(Rating)`      |


📈 Analytical Insights
1️⃣ Sales by Fat Content

Shows how “Low Fat” vs “Regular” products perform in total sales.

2️⃣ Sales by Item Type

Ranks all item categories based on revenue contribution.

3️⃣ Fat Content by Outlet (Pivot)

Visualizes total sales per Outlet_Location_Type grouped by fat category using a PIVOT operation.

4️⃣ Sales by Outlet Establishment Year

Tracks yearly performance trends to identify growth and maturity patterns.

5️⃣ Percentage of Sales by Outlet Size

Calculates each outlet size’s percentage share of total revenue using a window function:
6️⃣ Sales by Outlet Location

Highlights the best-performing outlet locations geographically.

7️⃣ All Metrics by Outlet Type

Combines key KPIs — Total Sales, Avg Sales, Ratings, and Item Visibility — in one query for quick outlet comparison.


⚙️ SQL Concepts Used

GROUP BY, ORDER BY, CASE

CAST and DECIMAL formatting for precision

PIVOT for matrix-style transformations

ISNULL for handling missing values

Window functions OVER() for percentage calculations

🧠 Insights Gained

Low Fat items slightly outperform Regular ones in overall sales.

Medium and Large outlets contribute the highest revenue percentages.

Urban outlet locations show stronger performance than smaller towns.

Established outlets (pre-2010) tend to have higher average sales, indicating customer trust and loyalty.

Tools & Environment
Component	Description
🗄️ Database	Microsoft SQL Server
💾 Dataset	Blinkit retail sales data
💬 Language	SQL
📊 Visualization	Pivot tables and aggregations within SQL
