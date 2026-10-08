# PowerBI-Global-Sales-Dashboard
#  Global Sales Performance Analytics | Power BI

<img width="1156" height="653" alt="Screenshot 2026-04-11 221549" src="https://github.com/user-attachments/assets/b2fd1b38-949f-4881-8a62-0a8e222d6be4" />

##  Project Overview
This project is an interactive **Executive Sales Dashboard** built in Power BI, designed to provide high-level visibility into global sales performance, channel effectiveness, and product profitability. The objective is to transform raw transactional data into actionable business insights for stakeholders to optimize sales strategies.
## Tech Stack & Tools
* **BI Tool:** Power BI Desktop
* **Data Transformation:** Power Query
* **Data Modeling:** Star Schema design
* **Calculations:** DAX (Data Analysis Expressions)

##  Data Modeling (Star Schema)
To ensure data integrity and optimize query performance, I architected a robust **Star Schema** consisting of:
* **1 Fact Table:** `Fact_Sales` (containing transactional data at the line-item level).
* **6 Dimension Tables:** `Dim_Date`, `Dim_Product`, `Dim_Customer`, `Dim_Reseller`, `Dim_SalesOrder`, `Dim_SalesTerritory`.
* **Relationship:** Single-directional (1-to-many) filtering from Dimensions to the Fact table to prevent ambiguity and circular dependencies.

<img width="1919" height="996" alt="Screenshot 2026-04-11 223607" src="https://github.com/user-attachments/assets/ca6b31e2-4ff6-4285-8679-46f3a35b0c72" />
##  Core DAX Measures
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
```
## Key Business Insights & Recommendations
Through analyzing the multi-year dataset (FY2018 - FY2021) and utilizing cross-filtering interactions, several critical business insights emerged:

1. **Consistent YoY Revenue Growth & Seasonal Peaks:** * **Observation:** The company experienced strong Year-over-Year (YoY) growth, with Total Sales nearly doubling from $23.86M in FY2018 to $43.43M in FY2020. *(Note: FY2021 data is currently incomplete).* Sales consistently peak around the Nov-Dec holiday season and mid-year (May-Jun).
   * **Recommendation:** Supply chain and inventory planning teams should pre-allocate stock 1-2 months ahead of these historical peaks to prevent stockouts and maximize holiday revenue.

2. **The "Pareto Principle" in Product Profitability:** * **Observation:** The core business relies heavily on the "Bikes" category. Mountain Bikes and Road Bikes are the absolute cash cows, generating over $11M in all-time profit. Conversely, apparel subcategories like `Jerseys` and `Caps` frequently record negative margins (e.g., -$0.01M).
   * **Recommendation:** The Product team must investigate the supply chain costs of the apparel lines. Consider implementing a "cross-selling" strategy (bundling loss-making jerseys with high-margin bikes) or discontinuing unprofitable lines entirely.

3. **B2B Channel Dominance vs. B2C Potential:** * **Observation:** The wholesale/B2B channel (`Reseller`) is the structural backbone of the business, consistently driving around 70-74% of the total revenue every year. However, in the Direct-to-Consumer (`Internet`) segment, the United States completely overshadows other regions.
   * **Recommendation:** While maintaining strong Reseller relationships is critical for cash flow, the Marketing team should investigate why Internet sales are lagging in European markets (Germany, France) and deploy localized online campaigns to capture B2C market share there.

##  Repository Contents
* `AdventureWorks Sales.pbix` : The main Power BI project file.
* `AdventureWorks Sales.pdf` : A high-quality PDF export of the dashboard for quick viewing.

##  How to View
1. **Quick View:** Open the `.pdf` file to see the final layout.
2. **Interactive View:** Download the `.pbix` file and open it with Power BI Desktop to interact with the slicers and cross-filtering features.
