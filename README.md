# House Loan Amount Prediction — Linear Regression

**Data Visualization & Analysis 
**Author:** Nguyen Hong Dang 

---

## Overview

This project applies a Linear Regression model to predict the loan sanction amount a customer can request from a bank, using their house as collateral. In addition to predictive modeling, the project conducts an in-depth exploratory analysis to identify the key demographic and property-related factors that influence loan approval amounts.

**Core conclusion:** Income level and income stability are the primary drivers of loan sanction amount. Gender, age group, and property location show minimal impact on loan outcomes, suggesting a relatively fair and stable lending environment in the dataset.

---

## Project Structure

```
DataViz-240112-Assignment2/
│
├── DataViz_240112_Assignment2.ipynb    # Main notebook: EDA, preprocessing, model, discussion
├── house-loan.csv                      # Source dataset
└── README.md
```

---

## Dataset Description

The dataset contains records of bank loan applicants, where each applicant uses their house as collateral. The target variable is the loan sanction amount.

| Feature | Type | Description |
|---|---|---|
| Gender | Categorical | Applicant gender (F / M) |
| Age | Numerical | Applicant age (years) |
| Income (USD) | Numerical | Monthly income of applicant |
| Income Stability | Categorical | Income stability rating (Low / High) |
| Property Age | Numerical | Age of collateral property (days) |
| Property Location | Categorical | Property location (Rural / Urban / Semi-Urban) |
| Property Price | Numerical | Market value of the property (USD) |
| Loan Sanction Amount (USD) | Numerical | **Target** — approved loan amount (USD) |

---

## Methodology

### 1. Exploratory Data Analysis
- Inspected data shape, types, and distributions using `df.info()`, `df.describe()`, and visualization libraries
- Identified missing values and data quality issues prior to preprocessing

### 2. Data Preprocessing
- Imputed missing `Income (USD)` values using the **column mean**
- Dropped rows with missing `Income Stability` and `Property Location` (categorical fields not suitable for imputation)
- Imputed missing `Property Age` using the **mean value per property location group**
- Removed duplicate rows
- Encoded categorical features (`Gender`, `Income Stability`, `Property Location`) using **LabelEncoder**

### 3. Model Development
- **Train/Test split:** 80% training, 20% testing
- **Pipeline:** `StandardScaler` followed by `LinearRegression` (scikit-learn)
- All features used as model inputs; `Loan Sanction Amount (USD)` as the target

### 4. Model Evaluation
- Primary metric: **Mean Absolute Error (MAE)**

---

## Results and Discussion

### Coding Tasks Summary

| Task | Description | Status |
|---|---|---|
| 1.1 | Exploratory Data Analysis | Completed |
| 1.2 | Data preprocessing and encoding | Completed |
| 1.3 | 80/20 train-test split | Completed |
| 1.4 | Linear Regression with StandardScaler pipeline | Completed |
| 1.5 | MAE evaluation on test set | Completed |

### Open Discussion Findings

**2.1 — Income vs. Income Stability**  
Both factors influence loan amounts. Higher income consistently correlates with higher loan approval amounts, with the 10k+ income group receiving the largest average amounts. Applicants with high income stability also tend to borrow more across all income groups, suggesting that lenders favor stable earners regardless of absolute income level.

**2.2 — Property Location**  
Average loan amounts across Rural, Urban, and Semi-Urban locations show minimal variation. Property location does not appear to be a significant factor in determining loan sanction amounts.

**2.3 — Gender Bias**  
The difference in average loan sanction amounts between male and female applicants is negligible. The data does not support the presence of gender bias in loan approvals.

**2.4 — Engineered Features**  
Potentially useful derived features include:
- **Income-to-Loan Ratio:** Measures the borrower's capacity to repay relative to the loan requested
- **Loan-to-Property-Value Ratio:** Assesses collateral coverage of the loan
- **Property Age-to-Loan Ratio:** Evaluates loan risk relative to property condition
- **Age Group Segmentation:** Categorizes borrowers for behavioral pattern analysis

**2.5 — Additional Insights**  
Beyond loan amount prediction, the dataset supports:
- Borrower behavior analysis by age group and income bracket
- Property market trend analysis based on price and location
- Targeted marketing strategies for high-value borrower segments (high-income, high-stability applicants)

---

## Tools and Libraries

| Library | Version | Purpose |
|---|---|---|
| Python | 3.x | Core language |
| Pandas | — | Data manipulation |
| NumPy | — | Numerical computation |
| Matplotlib | — | Data visualization |
| Seaborn | — | Statistical visualization |
| Scikit-learn | — | Preprocessing, modeling, evaluation |
| Google Colab | — | Development environment |

---

## How to Run

1. Open `DataViz_240112_Assignment2.ipynb` in [Google Colab](https://colab.research.google.com/)
2. Upload `house-loan.csv` to Google Drive
3. Mount Google Drive and update the dataset path in the first code cell:
   ```python
   loan_data = pd.read_csv('/content/drive/MyDrive/house_loan.csv')
   ```
4. Select `Runtime` → `Run all` to execute all cells in sequence

---

## Course Information

**Course:** Data Visualization and Analysis  
**Assignment:** Linear Regression  
