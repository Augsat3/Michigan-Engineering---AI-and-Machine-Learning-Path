# Marketing Campaign Analysis
Exploratory data analysis and hypothesis testing on a customer marketing dataset, to understand which factors influence customer purchases and response to campaigns (Product, Price, Place and Promotion).


## Dataset
- `marketing_data.csv`: 2,240 customers, with demographics (Education, Marital_Status, Country, Year_Birth, Kidhome, Teenhome), Income, spending on six products (Mnt columns), purchases by channel (web, catalog, store), web visits, deals, complaints and campaign responses.


## Project steps
1. Import data and examine variables
2. Data cleaning
3. Feature creation
4. Distributions and outlier checks
5. Encoding of categorical variables
6. Correlation heatmap
7. Hypothesis testing
8. Visualizations


## Data cleaning
- Income converted from text to numbers, Dt_Customer converted to a date, column-name spaces removed
- 24 missing Income values filled with the Education + Marital_Status group mean
- Marital_Status merged: Alone and YOLO into Single, Absurd renamed Other
- Top 0.4% of Income capped with winsorization
- 3 impossible ages removed
- 53 Children_count outliers (3 children) kept as valid
- Performed Fix Data Types, Data Imputation, Treat Outliers  operations


## Feature Engineering - New features
Children_count, Age, TotalSpending, TotalPurchases


## Correlation analysis
Education was ordinal encoded. Marital_Status and Country were one-hot encoded but left out of the heatmap, along with ID, Year_Birth and other columns that don't suit correlation. 18 numeric columns were used.


## Hypothesis tests (Z-test, alpha = 0.05)
| | Hypothesis | Result |
|---|---|---|
| H1 | Older customers shop more in store | Supported (small effect) |
| H2 | Customers with children shop more online | Not supported |
| H3 | Other channels affect store sales | Supported, positive link, no cannibalization |
| H4 | US buys more than the rest of the world | Not supported |


## Key findings
- Income is the strongest driver of spending and purchases.
- Children at home lower spending sharply.
- Wine and Meat bring most of the revenue.
- Web, catalog and store channels support each other.
- Age and country alone do not explain campaign acceptance.
- Complaints are rare, and Education does not explain them.


## Requirements
- Python 3.14
- pandas
- numpy
- matplotlib
- seaborn
- scipy
- statsmodels (for the Z-test)
- Jupyter / VS Code with the Jupyter extension
Install with: `pip install pandas numpy matplotlib seaborn scipy statsmodels`

## How to run
1. Install: Requirements, Run pip command above
2. Place `marketing_data.csv` in the same folder as the notebook.
3. Open the notebook in VS Code or Jupyter and choose Run All.


## Files
- `Marketing_Campaign_Notebook.ipynb`: full analysis
- `marketing_data.csv`: source data
- `marketing_data_cleaned_final.csv`: Cleaned data
- `Data Dictionary - Response to marketing campaigns.xlsx`: Data Dictionary
- `Marketing_campaign_problem_statement.docx`: Problem Statement