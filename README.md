# Customer Churn Analysis and Prediction Using Python

## Project Overview

This group project was conducted as part of SIT3020 Python for Data Science at Universiti Malaya during the 2025/2026 academic session.

The project investigates customer churn using demographic, financial, and account-related data from a European bank. Statistical analysis and machine learning techniques were applied to identify factors associated with customer churn, predict customers at risk of leaving, and develop data-driven customer retention recommendations.

## Project Objectives

- Identify key factors associated with customer churn.
- Explore customer demographic, financial, and behavioural patterns.
- Perform data cleaning, preprocessing, and feature engineering.
- Develop and compare machine learning classification models.
- Identify a suitable predictive model for customer churn.
- Provide actionable insights for customer retention strategies.

## Tools and Technologies

- Python
- Google Colab
- Jupyter Notebook

### Python Libraries

- pandas
- NumPy
- SciPy
- Matplotlib
- Seaborn
- scikit-learn

## Dataset Description

The original dataset consists of 10,000 customer records and 14 variables, containing demographic, financial, and account-related information.

### Target Variable

- Exited = 0: Customer stayed with the bank
- Exited = 1: Customer left the bank

### Original Churn Distribution

| Customer Status | Count | Percentage |
|---|---:|---:|
| Retained | 7,963 | 79.63% |
| Churned | 2,037 | 20.37% |
| Total | 10,000 | 100% |

The dataset is moderately imbalanced, with approximately one-fifth of customers belonging to the churn class.

### Main Variables

| Variable | Description |
|---|---|
| CreditScore | Customer credit score |
| Geography | Customer country |
| Gender | Customer gender |
| Age | Customer age |
| Tenure | Number of years with the bank |
| Balance | Customer account balance |
| NumOfProducts | Number of banking products held |
| HasCrCard | Credit card ownership |
| IsActiveMember | Customer membership activity status |
| EstimatedSalary | Estimated annual salary |
| Exited | Customer churn status |

## Methodology

### 1. Data Inspection and Cleaning

- Inspected dataset structure, dimensions, and data types.
- Checked for missing values, duplicate records, and invalid negative values.
- Applied the Interquartile Range (IQR) method to identify outliers.
- Removed selected CreditScore outliers.
- Applied the Mann-Whitney U test to examine differences in age between churned and retained customers.
- Applied outlier capping to the Age variable.
- Removed irrelevant customer identifiers.
- Applied one-hot encoding to categorical variables.

### 2. Feature Engineering

Two additional variables were constructed to capture customer financial behaviour and engagement patterns.

| Engineered Feature | Formula |
|---|---|
| BalanceSalaryRatio | Balance / EstimatedSalary |
| ProductsPerTenure | NumOfProducts / (Tenure + 1) |

### 3. Exploratory Data Analysis (EDA)

- Descriptive statistics
- Customer churn distribution analysis
- Age distribution analysis
- Churn comparison across geographical regions
- Customer activity analysis
- Pearson correlation analysis
- Correlation heatmaps
- Bar charts and boxplots

### 4. Data Preprocessing

- Stratified 80/20 training and testing split
- StandardScaler and RobustScaler for logistic regression preprocessing
- ColumnTransformer
- Machine learning pipelines
- Class weighting for supported classification models

### 5. Machine Learning Model Development

Four supervised machine learning classification models were developed:

1. Logistic Regression
2. Decision Tree
3. Random Forest
4. Gradient Boosting

### 6. Hyperparameter Tuning and Validation

- GridSearchCV
- RandomizedSearchCV
- Five-fold stratified cross-validation
- Hyperparameter optimisation
- Held-out test set evaluation

### 7. Model Performance Evaluation

Models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion matrix

F1-score was prioritised because of the imbalanced target variable and the importance of balancing precision and recall.

## Exploratory Data Analysis: Key Findings

- Age exhibited the strongest positive correlation with customer churn (r = 0.31).
- Churned customers were generally older than retained customers.
- Inactive customers exhibited higher churn rates than active customers.
- Active membership status showed a negative correlation with churn (r = -0.16).
- Customers in Germany recorded the highest churn rate among the geographical regions analysed.
- Traditional financial indicators such as CreditScore and EstimatedSalary showed relatively weak individual correlations with churn.
- The engineered BalanceSalaryRatio feature revealed differences in financial behaviour between churned and retained customers.

## Machine Learning Model Performance

The following results were obtained from the held-out test set.

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Random Forest | 0.815 | 0.534 | 0.686 | 0.600 | 0.862 |
| Gradient Boosting | 0.865 | 0.771 | 0.475 | 0.588 | 0.860 |
| Decision Tree | 0.784 | 0.478 | 0.738 | 0.580 | 0.839 |
| Logistic Regression | 0.717 | 0.389 | 0.700 | 0.500 | 0.775 |

## Final Model Selection

Random Forest was selected as the final predictive model based on its highest F1-score and ROC-AUC.

### Random Forest Performance

- Accuracy: 81.52%
- Precision: 53.37%
- Recall: 68.56%
- F1-score: 0.600
- ROC-AUC: 0.862

### Confusion Matrix

| Actual / Predicted | Retained | Churned |
|---|---:|---:|
| Retained | 1,351 | 242 |
| Churned | 127 | 277 |

Although Gradient Boosting achieved the highest accuracy, it failed to identify more than half of the actual churned customers.

Random Forest provided a better balance between identifying at-risk customers and minimising false positives, making it more suitable for the selected evaluation objective.

## Business Insights and Recommendations

Based on the analytical findings, the following customer retention strategies were proposed:

- Develop targeted re-engagement campaigns for inactive customers.
- Introduce personalised banking services for older customer segments.
- Investigate regional factors contributing to higher churn rates in Germany.
- Improve customer engagement through personalised offers and financial consultations.
- Use predictive analytics to support proactive customer retention strategies.

## Limitations and Future Improvements

- The dataset contains an imbalanced target variable.
- Correlation analysis does not establish causation.
- Some data-dependent preprocessing was performed before the train-test split. Future work should fit these preprocessing steps using training data only to reduce potential data leakage.
- Future work could explore SMOTEENN resampling to improve minority-class prediction.
- Classification threshold optimisation could be explored to improve customer retention outcomes.
- Additional validation using independent customer datasets would help assess model generalisability.

## Conclusion

This project demonstrates the application of statistical analysis and supervised machine learning to a real-world business problem.

Random Forest achieved the highest F1-score and ROC-AUC among the four evaluated models, highlighting its potential for customer churn prediction and data-driven retention planning.

## Skills Demonstrated

- Python programming
- Data cleaning and preprocessing
- Outlier detection and treatment
- Exploratory data analysis
- Statistical hypothesis testing
- Feature engineering
- Data visualisation
- Correlation analysis
- Supervised machine learning
- Classification modelling
- Hyperparameter tuning
- Cross-validation
- Model performance evaluation
- Business analytics
- Statistical interpretation and reporting

## Repository Contents

| File | Description |
|---|---|
| customer_churn_analysis.ipynb | Complete Python analysis and machine learning notebook |
| Churn_Telco.csv | Original customer churn dataset |
| data_dictionary.csv | Dataset variable descriptions |
| customer_churn_report.pdf | Full project report and analytical findings |

## Project Information

- Institution: Universiti Malaya
- Programme: Bachelor of Science in Statistics
- Course: SIT3020 Python for Data Science
- Academic Session: 2025/2026
- Project Type: Group assignment
