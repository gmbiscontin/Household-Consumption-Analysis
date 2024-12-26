# Analysis of the Relevant Factors Influencing Consumption Estimates

## 1) Introduction

### Research Objective
The goal of this research is to identify factors influencing consumption expectations among Italians at the end of 2021. The analysis examined variables such as income, employment status, savings, and other socio-economic factors.

The analysis focuses on predicting whether consumption expectations exceed or equal savings and earnings (`1`) or if savings and earnings are sufficient for the next year's consumption (`0`). This analysis aims to help policymakers understand the main factors driving consumption expectations, allowing them to design policies that boost confidence and stimulate economic growth.

---

## 2) Dataset Description

### Source
The data comes from the **Survey on Household Income and Wealth (SHIW)** for the year 2020, conducted by the Bank of Italy. It includes 6,239 households and 15,198 individuals.

### Target Variable
The key variable, `RISPARFINE`, is a binary classification of respondents' consumption behavior:
- **1**: Spending more than income (financial strain)
- **0**: Spending less or equal to income (financial stability)

### Features
The dataset includes both categorical and continuous variables, covering:
- **Socio-demographic factors** (e.g., age, household members, geographical area)
- **Income, expenditure, and savings** (e.g., payroll income, savings, consumption)
- **Wealth and debts** (e.g., real estate assets, liabilities)

---

## 3) Data Preprocessing

### Cleaning and Handling Issues
- Rows referring to the same household were removed.
- Outliers were detected using the Z-score method (threshold set at 5).
- Data types were standardized (all columns converted to float).

The final dataset has 6,239 rows and 28 columns.

---

## 4) Descriptive Statistics and Data Visualization

### Dataset Splitting
The dataset was divided into three parts:
- **Training Set**: 80% (4,991 rows)
- **Test Set**: 10% (624 rows)
- **Validation Set**: 10% (624 rows)

---

## 5) Feature Management

### Handling Categorical Features
- 10 categorical variables were identified, and some classes were merged to simplify the analysis.
- 15 dummy variables were created from 32 potential categories.

### Continuous Feature Scaling
- 18 continuous variables were standardized using the `StandardScaler` function.

### Correlation Matrix
- A correlation matrix was used to assess relationships between features and the target variable.

---

## 6) Machine Learning Techniques

### Models Used
Several machine learning models were applied to predict consumption expectations:
1. **Logistic Regression (Standardized)**  
2. **Logistic Regression with Ridge Regularization**  
3. **Logistic Regression with Lasso Regularization**  
4. **Logistic Regression with Elastic-Net Regularization**  
5. **Random Forest**  
6. **XGBoost**

### Standardized Logistic Regression
- Standardization allows easier comparison of feature importance.
- The transformation normalizes each variable to have a mean of 0 and standard deviation of 1.

### Regularization Models (Ridge, Lasso, Elastic-Net)
- **Ridge**: Minimizes the magnitude of coefficients to address multicollinearity.
- **Lasso**: Shrinks some coefficients to zero, helping in feature selection.
- **Elastic-Net**: A combination of Ridge and Lasso regularization technique:

  $\underset{\beta_0, \beta_1, \dots, \beta_p}{\text{minimize}} \left[ \text{RSS} + \lambda_1 \sum_{j=1}^{p} |\beta_j| + \lambda_2 \sum_{j=1}^{p} \beta_j^2 \right]$

### Random Forest & XGBoost
- **Random Forest**: Uses an ensemble of decision trees to reduce overfitting.
- **XGBoost**: A gradient boosting technique providing feature importance scores.

---

## 7) Model Comparison

### Performance on Validation Set
- All models performed similarly, but **XGBoost** showed the best results.
- XGBoost was selected as the final model due to its superior performance.

### Confusion Matrix and Threshold Selection
- The optimal threshold for classification was found to be between **0.2 and 0.5**, balancing precision and recall.

---

## 8) Validation and Test Set Performance

### Final Evaluation
- The XGBoost model showed the best performance when evaluated on the test set.
- The threshold of **0.5** was confirmed as the most suitable for classification
