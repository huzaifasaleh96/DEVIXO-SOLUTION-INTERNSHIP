# Superstore Sales & Profit Analysis

End-to-end data analysis project on a 12,000-order Superstore sales dataset, covering data cleaning, feature engineering, exploratory data analysis (EDA), sales forecasting, and an interactive Power BI dashboard.

## Project Overview

This project analyzes two years (2024–2025) of Superstore order data to understand sales and profit drivers across product categories, regions, customers, and shipping performance, and to surface actionable business recommendations.

**Deliverables in this project:**

| File | Description |
|---|---|
| `huzaifa_task_3 (1).ipynb` | Jupyter/Colab notebook — data cleaning, feature engineering, EDA, correlation & outlier analysis, and a Prophet sales forecast |
| `Sales_Profit_Analysis_Dashboard_pbix_mee.pbix` | Power BI dashboard built on the cleaned dataset |
| `REPORT.md` | Full write-up of methodology, findings, and business recommendations |
| `README.md` | This file |

## Dataset

- **Source file:** `Devixo_Task_03_Superstore_Sales_12000.csv`
- **Size:** 12,015 rows × 19 original columns
- **Time span:** January 2024 – December 2025
- **Key fields:** Order ID, Order/Ship Date, Customer, Segment, Region, State, City, Category, Sub-Category, Product Name, Unit Price, Quantity, Discount, Sales, Profit, Payment Mode, Order Priority

## Workflow

### 1. Data Cleaning
- Loaded the CSV from Google Drive into pandas
- Checked missing values and duplicates
- Imputed missing `Customer Name`, `State`, and `Payment Mode` with the column mode
- Converted `Order Date` / `Ship Date` to datetime
- Identified 15 duplicate records (see [Notes / Known Issues](#notes--known-issues))

### 2. Feature Engineering
New columns derived from the raw data:
- `Year`, `Month`, `Day`, `Day_of_Week` — extracted from `Order Date`
- `Discount_Amount` = `Sales × Discount`
- `Profit_Margin` = `Profit / Sales × 100`
- `Shipping Days` = `Ship Date − Order Date`
- `Shipping_Category` — bucketed into **Fast** (0–2 days), **Standard** (3–5 days), **Slow** (6+ days)

The enriched dataset (27 columns) is exported to `sales_feature_engineered.csv`, which is the source file for the Power BI dashboard.

### 3. Exploratory Data Analysis
- Sales & profit by Category, Region, State, City, Segment, Payment Mode, Shipping Category
- Monthly sales and profit trends
- Top 10 products and customers by sales/profit
- Correlation heatmap across numeric features
- Outlier detection (IQR method) and distribution plots (histograms, box plots, scatter plots)

### 4. Forecasting
- A Prophet time-series model is fit on monthly sales to project sales for the next 12 months, including trend and seasonality components.

### 5. Power BI Dashboard
A single-page interactive dashboard (**"Sales & Profit Analysis Dashboard"**) built on the feature-engineered dataset, featuring:
- KPI cards: Total Sales, Total Profit, Total Customers
- Sales by Region and by Category (column charts)
- Profit by Category (column chart)
- Sales trend over time (line charts)
- Top customers and top products by sales (bar charts)
- Slicers: Region, Category, Order Date

## How to Reproduce

1. Open `huzaifa_task_3 (1).ipynb` in Google Colab (it mounts Google Drive) or Jupyter.
2. Point `file_path` to your copy of `Devixo_Task_03_Superstore_Sales_12000.csv`.
3. Run all cells top to bottom to clean, engineer features, and reproduce the EDA charts and forecast.
4. The notebook exports `sales_feature_engineered.csv` — load this file as the data source in Power BI.
5. Open `Sales_Profit_Analysis_Dashboard_pbix_mee.pbix` in Power BI Desktop to view/interact with the dashboard.

## Tools & Libraries

- Python: `pandas`, `matplotlib`, `seaborn`, `prophet`
- Power BI Desktop

## Notes / Known Issues

- 15 duplicate rows were detected but not removed in the notebook — consider adding a `drop_duplicates()` step before analysis.
- The `City` column retained 12 missing values after the imputation step (only `Customer Name`, `State`, and `Payment Mode` were imputed).

## See Also

For detailed findings, KPIs, and business recommendations, see [`REPORT.md`](./REPORT.md).
