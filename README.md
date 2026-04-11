# PowerBI-Global-Sales-Dashboard
# 📊 Global Sales Performance Analytics | Power BI

<img width="1156" height="653" alt="Screenshot 2026-04-11 221549" src="https://github.com/user-attachments/assets/b2fd1b38-949f-4881-8a62-0a8e222d6be4" />

## 📝 Project Overview
This project is an interactive **Executive Sales Dashboard** built in Power BI, designed to provide high-level visibility into global sales performance, channel effectiveness, and product profitability. The objective is to transform raw transactional data into actionable business insights for stakeholders to optimize sales strategies.
## 🛠️ Tech Stack & Tools
* **BI Tool:** Power BI Desktop
* **Data Transformation:** Power Query
* **Data Modeling:** Star Schema design
* **Calculations:** DAX (Data Analysis Expressions)

## 🗄️ Data Modeling (Star Schema)
To ensure data integrity and optimize query performance, I architected a robust **Star Schema** consisting of:
* **1 Fact Table:** `Fact_Sales` (containing transactional data at the line-item level).
* **6 Dimension Tables:** `Dim_Date`, `Dim_Product`, `Dim_Customer`, `Dim_Reseller`, `Dim_SalesOrder`, `Dim_SalesTerritory`.
* **Relationship:** Single-directional (1-to-many) filtering from Dimensions to the Fact table to prevent ambiguity and circular dependencies.

<img width="1919" height="996" alt="Screenshot 2026-04-11 223607" src="https://github.com/user-attachments/assets/ca6b31e2-4ff6-4285-8679-46f3a35b0c72" />
## 🧮 Core DAX Measures
Created a centralized `_Measures` table to store core business logic. Key KPIs include:

```dax
// Total Revenue
Total Sales = SUM('Fact_Sales'[Sales Amount])

// Total Cost of Goods Sold
Total Cost = SUM('Fact_Sales'[Total Product Cost])

// Gross Profit
Total Profit = [Total Sales] - [Total Cost]

// Profit Margin Percentage
Profit Margin = DIVIDE([Total Profit], [Total Sales], 0)

// Order Volume
Total Orders = DISTINCTCOUNT('Fact_Sales'[SalesOrderLineKey])
