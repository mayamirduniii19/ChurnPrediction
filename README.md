# Customer Churn Prediction
This project focuses on predicting whether a customer is likely to churn(or leave a service) using machine learning techniques. The main aim is to understand and showcase how different models makes decision, how their performance varies and what differentiates them.Explores how combining models can improve overall predictions.

**THE DATASET**
Source : Churn-Modelling Dataset -Kaggle
Rows: 10000
Original Features:14
Target Variable(after preprocessing): Churn(0=No, 1=Yes)
Class Distribution : 80% No churn, 20% Churn - Imbalance
Null and Missing Values: None
Column Mapping-columns were renamed to match the requirements of the task.

**STEPS:**
1. Data Loading and Cleaning - loaded the data and checked for missing values. Removed irrelevant columns and converted the catrgorical data into numeric data.
2. Feature Engineering -Created new features to capture combined patterns of the data.
3. Class Imbalance Handling- identified class imbalance and applied SMOTE on the rescaled training data.
4. Model Training - used Logistic Rgression, Random Forest and XGBoost.
5. Hyperparameter Tuning - RandomizedSearchCV
6. Evaluation Metrics - Accuracy, F1-Score, Confusion Matrix, PR Curves
7. Rule-Based Logic- built a rules based engine for the prediction.
8. Model Comparison and Conclusion.

**FEATURE ENGINEERING**

Individual features showed weak correlation with Churn.
4 new features were created:
1. balance_income_ratio 
2. is_inactive_highbalance-inactive member with above-median balance
3. age_group -age binned into groups
4. products_pre_creditcore- purchases relative to creditscore.
The columns Age and age_group (0.92 correlation) as well as CreditScore and products_pre_creditscore had multicollinearity issue and therfore the original columns were dropped.

**MODELS:**

Model 1- LOGISTIC REGRESSION

Accuracy: 0.68
-chosen for simplicity
The model slightly better than it did with the data without smote.

Model 2- RANDOM FOREST

Accuracy: 0.80
Ensemble of decision trees. Handles non-linear relationships much better.

Model 3- XGBOOST

Accuracy: 0.81
Gradient Boosting builds trees sequentially and outperformed the other two after hyperparameter tuning.

**HYPERPARAMETER TUNING**

RandomizedSearchCV was used.
Initially tuned on SMOTE resampled data which lead to poor generalisation as the parametrs for the synthtic data.
Tried to modify it by tuning the model on the scaled data which learns the best parametrs based on the actual patterns and then retrained models in SMOTE data for class balancing.


**RULE BASED LOGIC**

A rule-based system derived from the correlation analysis and EDA. 
Rules:
1. Customer Aged 45+ and who are inactive would probably churn
2. Balance higher than 200000 and being an inactive member
3. Too many purchases and they are still inactive.
4. Low engagement that is they have too low purchases and they are an inactive member.
The rule based logic worked pretty good achieveing an accuracy of 73%

**MODEL COMPARISONS:**

<img width="700" height="286" alt="image" src="https://github.com/user-attachments/assets/b9f36cba-6963-4e52-a8c6-2ffd7c07a64d" />



**FINAL INSIGHTS:**

Tuned XGBoost is the best working model.
-Had the highest recall for churners:0.71
-best F1 Score- 0.60
-The train-test gap was reasonable
-Hit highest PR-AUC:0/69

The key improvement came from the tuning on the scaled original data rather than the smote resampled data, allowing model to find the best parameters that genralise much better.

