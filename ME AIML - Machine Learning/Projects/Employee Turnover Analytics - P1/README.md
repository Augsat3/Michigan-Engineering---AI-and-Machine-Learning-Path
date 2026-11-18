# Employee Turnover Analytics
Machine learning analysis of Portobello Tech's employee data for the HR Department. It finds the factors linked with employee turnover, clusters the employees who left, predicts who is likely to leave, and suggests retention strategies by risk zone.


## Dataset
- `HR_comma_sep.csv`: 14,999 employee records with satisfaction_level, last_evaluation, number_project, average_montly_hours, time_spend_company, Work_accident, promotion_last_5years, Department (file column `sales`), salary and the target `left` (1 = left, 0 = stayed).


## Project steps
Headings follow the task order of the problem statement.
1. Data quality checks (missing values, duplicates)
2. EDA: factors behind turnover, correlation heatmap, distribution plots, project count bar plot
3. K-means clustering (3 clusters) of employees who left, on satisfaction and evaluation
4. Pre-processing (get_dummies), stratified 80:20 split (random_state=123), SMOTE on the train set
5. 5-fold cross-validation: Logistic Regression, Random Forest, Gradient Boosting, with classification reports
6. ROC/AUC, confusion matrices, Recall vs Precision, best model selection
7. Turnover probability on the test set, four risk zones and retention strategies


## Data cleaning
- No missing values found
- 3,008 exact duplicate rows (20.05%) removed, leaving 11,991 employees (10,000 stayed, 1,991 left)
- Column `sales` renamed to `Department`


## Clusters of employees who left
| Cluster | Profile | Employees |
|---|---|---|
| 0 | Low satisfaction, high evaluation: overworked and burned out | 534 |
| 1 | High satisfaction, high evaluation: happy high performers who left | 555 |
| 2 | Medium satisfaction, low evaluation: disengaged, under-used | 902 |


## Model results (SMOTE on train only, 5-fold stratified CV)
| Model | CV recall | CV ROC AUC | Test recall | Test precision | Test AUC |
|---|---|---|---|---|---|
| Logistic Regression | 0.8292 | 0.8406 | 0.8241 | 0.4095 | 0.8312 |
| Random Forest | 0.9096 | 0.9809 | 0.9020 | 0.9703 | 0.9752 |
| Gradient Boosting | 0.9303 | 0.9856 | 0.9146 | 0.9077 | 0.9769 |

Recall is the main metric, because missing an employee who will leave costs more than a false alarm. **Best model: Gradient Boosting.**


## Risk zones (test set, 2,399 employees)
| Zone | Score | Employees | Actual leave rate |
|---|---|---|---|
| Safe (Green) | < 20% | 1,890 | 1.38% |
| Low-Risk (Yellow) | 20% to under 60% | 121 | 7.44% |
| Medium-Risk (Orange) | 60% to under 90% | 39 | 56.41% |
| High-Risk (Red) | 90% and above | 349 | 97.71% |


## Key findings
- Low satisfaction is the strongest factor linked with turnover (correlation -0.35 with left).
- Workload follows a U shape: 2 projects (54.17% left) and 6 to 7 projects (44.92% and 100.00% left) are risky, while 3 projects is the safest (1.08%).
- Very long monthly hours (above 280, 72.30% left), low salary (20.45% left) and no promotion are linked with higher leaving. Leaving by years in the company peaks at 3 to 6 years (highest at 5 years, 45.39%), and no one with 7 or more years left. These are associations in past data, not proven causes.
- Gradient Boosting catches 364 of 398 leavers in the test set.


## Requirements
- Python 3.14
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- imbalanced-learn (for SMOTE)
- Jupyter / VS Code with the Jupyter extension
Install with: `pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn`

## How to run
1. Install: Requirements, Run pip command above
2. Place `HR_comma_sep.csv` in the same folder as the notebook.
3. Open the notebook in VS Code or Jupyter and choose Run All.


## Files
- `EmployeeTurnoverAnalytics_notebook.ipynb`: full analysis
- `HR_comma_sep.csv`: source data
- `1736848192_employee_turnover_problem_statement.docx`: Problem Statement
