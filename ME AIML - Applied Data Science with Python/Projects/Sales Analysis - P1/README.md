# Sales Analysis - AAL (Australian Apparel Ltd), Q4 2020
Exploratory data analysis of AAL's fourth quarter 2020 sales, state by state. It finds the highest and lowest revenue states, suggests sales programs for the low revenue states, and gives data-driven insights to the Head of Sales and Marketing.


## Dataset
- `AusApparalSales4thQrt2020.csv`: 7,560 rows, one row for each Date + Time of day + State + Group. Columns are Date, Time (Morning, Afternoon, Evening), State (7 states), Group (Kids, Women, Men, Seniors), Unit and Sales. Covers 1 Oct 2020 to 30 Dec 2020.


## Project steps
Headings follow the task order and lettering of the problem statement.
1. STEP1 : Data wrangling
   - 1.a Clean data, missing / incorrect entries (isna and notna, duplicates, cleaning, incorrect values, outliers)
   - 1.b Recommendations for treating missing and incorrect data
   - 1.c Normalization (Min-Max)
   - 1.d GroupBy insights (chunking and merging)
2. STEP2 : Data analysis
   - 2.a Descriptive statistics of Sales and Unit with box plot
   - 2.b Group with highest and lowest sales
   - 2.c State with highest and lowest sales
   - 2.d Weekly, monthly and quarterly reports
3. STEP3 : Data visualization
   - 3.a Dashboard: State x Group, Group x State, Time of the day (peak / off-peak)
   - 3.b Daily, weekly, monthly and quarterly charts, and the Dashboard for the Head of Sales and Marketing (8 charts, two per row)
   - 3.c Seaborn recommendation and the reason
4. STEP4 : Report generation
   - 4.a Jupyter notebook report and cleaned data
   - 4.b Markdown
   - 4.c Box plot, Seaborn distribution plot, Growth target, SUMMARY and RECOMMENDATIONS


## Data cleaning
- Extra leading spaces removed from Time, State and Group
- Date converted from text to a date
- No missing values, no duplicate rows and no incorrect values (Price per Unit checked, fixed at 2500 for every row)
- 2 days are not in the data for any state (2020-10-31 and 2020-12-31), they were not filled
- 123 high Sales rows (all from VIC) are real sales, so they were kept (no capping)
- Performed Fix Data Types, Data Validation, Treat Outliers operations


## Feature Engineering - New features
Price_per_Unit, Sales_Normalization, Unit_Normalization (Min-Max), Week, Month, Month_Name, Quarter, Quarter_Name, Day_Name


## Key findings
- Q4 2020 sales: 340.30 million from 136,121 units.
- Highest revenue states: VIC (105.56 million), NSW (74.97 million), SA (58.86 million), together 70.35% of sales.
- Lowest revenue states: WA (22.15 million), NT (22.58 million), TAS (22.76 million). QLD (33.42 million) is the middle state.
- The four groups are almost equal (Men highest, Seniors lowest, 2.04% difference).
- December is the best month (135.33 million, 49.23% above November), November the weakest (90.68 million).
- Morning is the peak and Evening is the off-peak, but the gap is only 1.89%.
- Sales programs for WA, NT and TAS: a November offer, stock and staff ready by 1 December, and group-wise offers. If they reach the QLD level, sales grow by 32.76 million (9.63%).


## Results (Q4 2020, Sales in millions)
| State | Sales | Share (%) |
|---|---|---|
| VIC | 105.56 | 31.02 |
| NSW | 74.97 | 22.03 |
| SA | 58.86 | 17.30 |
| QLD | 33.42 | 9.82 |
| TAS | 22.76 | 6.69 |
| NT | 22.58 | 6.64 |
| WA | 22.15 | 6.51 |

| Month | Sales |
|---|---|
| October | 114.29 |
| November | 90.68 |
| December | 135.33 |


## Requirements
- Python 3.14
- pandas
- numpy
- matplotlib
- seaborn
- scipy
- Jupyter / VS Code with the Jupyter extension
Install with: `pip install pandas numpy matplotlib seaborn scipy`

## How to run
1. Install: Requirements, Run pip command above
2. Place `AusApparalSales4thQrt2020.csv` in the same folder as the notebook.
3. Open the notebook in VS Code or Jupyter and choose Run All.


## Files
- `Sales_Analysis_Notebook.ipynb`: full analysis
- `AusApparalSales4thQrt2020.csv`: source data
- `Sales_Analysis_cleaned.csv`: Cleaned data
- `problem_statement.docx`: Problem Statement
