# Sales Performance Dashboard (Power BI)

An interactive Power BI dashboard that tracks sales, profit and budget performance across regions, categories and products (Jan 2025 to Jun 2026).

## Overview

The report answers four questions:

- How are sales and profit trending, and how does this year compare with last year?
- Are we meeting budget, and where are the gaps?
- Which regions, categories and products drive the business?
- What does one product look like in detail?

## Report Pages

### 1. Executive Summary
- **KPI cards:** Total Sales, Total Cost, Profit, Profit %, Orders, Customers, Average Order Value, Variance vs Budget
- **Trend:** monthly Sales vs Sales LY with YoY %
- **Actual vs Budget** by Region and Category (Variance and Variance %)
- **Region performance** and **Product performance**
- **Slicers:** Year, Region, Category

### 2. Product Detail (drill-through)
- Drill through from any product on the Executive Summary
- KPI cards, monthly trend, sales by region and channel, top customers

Screenshots are in the `images/` folder.

## Data Model

Star schema built from an Excel source.

| Table | Purpose |
|---|---|
| Sales | Fact table: orders, quantity, sales amount, cost, profit |
| Product | Product, category, subcategory |
| Customer | Customer name and region |
| Date | Date table (marked as date table), Year, Month, Year-Month |
| Budget | Monthly budget by region and category |
| Region | Shared dimension so Sales and Budget filter together |
| Category | Shared dimension so Sales and Budget filter together |
| _Measures | Holds all DAX measures, grouped in display folders |

**Relationships:** Sales to Product, Customer and Date; Sales and Budget to Region and Category; Budget to Date. All are many-to-one, single direction.

## Key DAX Measures

- **Core:** Total Sales, Total Cost, Profit, Profit %, Orders, Customers, Average Order Value
- **Time intelligence:** Sales LY, YoY %, YTD Sales, YTD Sales LY, YTD YoY % (dynamic, based on the latest sales date)
- **Budget:** Budget, Variance, Variance %
- **KPI labels:** text measures that show the sub-line under each card, such as "68.1% of sales" or "-93.8K short"

## Key Insights

- Sales are about 1% below budget overall, and under budget in 12 of 18 months.
- East region sales fell 12.2% in H1 2026 vs H1 2025, while West grew 14.9%.
- Two laptop products make up about 61% of total sales.
- Profit margin is flat at roughly 31-32% across all products.

## How to Use

1. Clone or download this repository.
2. Open the `.pbix` file in Power BI Desktop.
3. If the data source path has changed, go to **Home > Transform data > Data source settings** and point it to your copy of the Excel file.
4. Click **Refresh**.

## Tools

Power BI Desktop, DAX, Power Query, Excel

## Author

Add your name and LinkedIn link here.
