# DEVIXO-SOLUTION-INTERNSHIP
Task 1 — Marketing Campaign Analytics (EDA)
Overview
This notebook (`DEVIXO_TASK_1.ipynb`) performs an end-to-end exploratory data analysis (EDA) on a synthetic Pakistani marketing dataset to understand what drives customer conversion and purchase behavior across marketing channels, campaigns, cities, and devices.
Dataset
File: `marketing_dataset_1000_records.csv`
Records: 1,000 customers
Columns: 19
`Customer_ID`, `Age`, `Gender`, `City`, `Income_PKR`
`Marketing_Channel`, `Campaign`
`Ad_Impressions`, `Ad_Clicks`, `Website_Visits`, `Email_Opened`
`Previous_Purchases`, `Purchase_Amount_PKR`
`Device`, `Traffic_Source`
`Customer_Satisfaction`, `Converted` (target)
`Click_Through_Rate_%`, `Conversion_Rate_%`
Environment / Requirements
Google Colab (uses `google.colab.drive` to mount the dataset from Google Drive)
Python 3
`pandas`, `numpy`, `matplotlib`, `seaborn`
To run outside Colab, replace the `drive.mount(...)` cell with a direct path to the local CSV file.
Workflow / Notebook Structure
Load data — mount Google Drive, read the CSV into `df`, preview with `head()`.
Data quality check
No missing values found (1000 × 19 → unchanged).
No duplicate rows found.
`df.info()` confirms dtypes (11 int, 2 float, 6 object columns).
Univariate EDA
Histograms (with KDE) for `Age`, `Income_PKR`, `Purchase_Amount_PKR`, `Ad_Impressions`, `Ad_Clicks`, `Website_Visits`.
Count plots for categorical features (`Gender`, `City`, `Marketing_Channel`, `Campaign`, `Device`, `Traffic_Source`, `Converted`).
Descriptive statistics table (`df.describe()`).
Correlation analysis
Full correlation heatmap of numerical features.
Correlations against the target `Converted` (all weak; strongest is `Conversion_Rate_%` at 0.22).
Bivariate / relationship EDA
Box plots of `Purchase_Amount_PKR` by category (Gender, City, Channel, Campaign, Device, Traffic Source).
Box plots of `Income_PKR` and `Purchase_Amount_PKR` by `Converted` status.
Violin plots of `Age` and `Income_PKR` by conversion status.
Box plots of `Ad_Impressions`, `Ad_Clicks`, `Website_Visits`, `Previous_Purchases` by conversion status.
Count plot of `Customer_Satisfaction` by conversion status.
Bar charts of conversion rate by every categorical feature.
Scatter plot of `Purchase_Amount_PKR` vs `Income_PKR`, colored by conversion.
Step 9 — 15 evidence-based business insights, computed programmatically (not hand-written) from grouped aggregations (channel, campaign, city, device, traffic source, gender, email-opened) and from correlation with `Converted`.
Key Results (from the executed run)
Overall conversion rate: 28.9% (289 / 1000 customers).
Best channel: Google Ads (31.9% conversion); worst: Facebook Ads (24.6%) — though Facebook Ads has the highest average purchase value (PKR 55,056).
Best campaign: New Product (35.0% conversion); worst: Summer Sale (21.4%).
Best city: Quetta (36.5% conversion); worst: Karachi (24.6%).
Device: Desktop converts best (32.5%) vs Mobile (26.7%).
Traffic source: Referral converts best (31.7%); Organic converts worst (24.3%).
Gender: Female customers convert slightly more (30.5%) than Male (27.4%).
Numerical features (income, ad impressions/clicks, website visits, previous purchases, satisfaction) all show very weak correlation with conversion — behavioral/categorical factors (channel, campaign, city, traffic source) are more informative than raw engagement volume in this dataset.
All findings are explicitly framed as associations, not causal proof.
How to Reproduce
Open the notebook in Google Colab (or Jupyter).
Update the dataset path in the "load data" cell to point to your copy of `marketing_dataset_1000_records.csv`.
Run all cells top to bottom.
Output
Inline visualizations (histograms, count plots, box/violin plots, heatmap, scatter plot).
Printed summary tables (by channel, campaign, city, device, traffic source, and converted vs non-converted).
A printed list of 15 numbered business insights.
