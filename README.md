# Bank Marketing Deposit Prediction

Machine learning project to predict whether a bank customer will subscribe to a term deposit, so the bank can focus its marketing calls on the customers most likely to say yes.

## Problem Statement

Banks run phone marketing campaigns to sell term deposits, but most calls do not convert. This project builds classification models on customer and campaign data to predict the `deposit` outcome (yes / no).

## Dataset

- **Size:** 11,162 records, 17 columns (16 after preprocessing)
- **Target:** `deposit` (yes = 1, no = 0)
- **Source:** *(add the dataset link here, e.g. Kaggle / UCI)*

| Type | Columns |
|---|---|
| Customer | age, job, marital, education, default, balance, housing, loan |
| Campaign | contact, day, month, duration, campaign, previous, poutcome |

## Tools Used

Python, Pandas, Seaborn, Matplotlib, Scikit-learn, Google Colab

## Workflow

1. **Data checks:** no missing values and no duplicate rows found.
2. **Cleaning:** dropped the `pdays` column; filtered out unrealistic ages (above 100).
3. **Outlier inspection:** boxplots for age, balance, duration, campaign and previous.
4. **Encoding:** converted categorical columns to numbers with `LabelEncoder`.
5. **Split:** 75% train (8,371 rows) / 25% test (2,791 rows), `random_state=97`.
6. **Scaling:** `StandardScaler` applied for KNN and SVM.
7. **Modelling and evaluation:** accuracy score and confusion matrix heatmap for each model.

## Model Results

| Model | Accuracy |
|---|---|
| **Random Forest** (50 trees, max depth 9) | **84.09%** |
| SVM (polynomial kernel) | 80.83% |
| SVM (linear kernel) | 79.65% |
| Decision Tree | 78.00% |
| Logistic Regression | 76.71% |
| KNN (k = 6) | 75.49% |
| SVM (sigmoid kernel) | 64.21% |

**Best model: Random Forest.** On the test set it correctly identified 1,138 of 1,299 actual subscribers (about 88% recall) and 1,209 of 1,492 non-subscribers.

```
Confusion matrix (Random Forest)
                 Predicted No   Predicted Yes
Actual No             1209            283
Actual Yes             161           1138
```

## Project Structure

```
bank-marketing-deposit-prediction/
├── Bank marketing project.ipynb
├── bank.csv
└── README.md
```

## How to Run

1. Clone the repo and open the notebook in Jupyter or Google Colab.
2. Update the file path in the first cell to point to `bank.csv`:
   ```python
   data = pd.read_csv('bank.csv')
   ```
3. Run all cells.

## Possible Improvements

- Hyperparameter tuning with GridSearchCV and cross-validation.
- Try gradient boosting models such as XGBoost.
- Use one-hot encoding instead of label encoding for nominal columns like `job`.
- `duration` (call length) is only known after the call, so test results without it for a more realistic pre-call prediction model.
- Add feature importance analysis and EDA charts.

## Author

**Anirudh**
Data Analyst | Python, SQL, Excel, Power BI
