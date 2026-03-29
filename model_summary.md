MODELS:
Model 1- Logistic Regression
Accuracy: 0.68
-chosen for simplicity
The model slightly better than it did with the data without smote.

Model 2- Random Forest
Accuracy: 0.80
Ensemble of decision trees. Handles non-linear relationships much better.

Model 3- XGBoost
Accuracy: 0.81
Gradient Boosting builds trees sequentially and outperformed the other two after hyperparameter tuning.

HYPERPARAMETER TUNING
RandomizedSearchCV was used.
Initially tuned on SMOTE resampled data which lead to poor generalisation as the parametrs for the synthtic data.
Tried to modify it by tuning the model on the scaled data which learns the best parametrs based on the actual patterns and then retrained models in SMOTE data for class balancing.

<img width="500" height="331" alt="image" src="https://github.com/user-attachments/assets/2a3225c3-4ea0-4eef-b539-b580ef876ba8" />

**Rule Based Logic**
A rule-based system derived from the correlation analysis and EDA. 
Rules:
1. Customer Aged 45+ and who are inactive would probably churn
2. Balance higher than 200000 and being an inactive member
3. Too many purchases and they are still inactive.
4. Low engagement that is they have too low purchases and they are an inactive member.

The rule based logic worked pretty good achieveing an accuracy of 73%

Conclusion:
Machine learning models,especially XGBoost, outperformed the rule-based approach by effectively capturing complex patterns in the data. Feature engineering further enhanced model performance,particularly for simpler models.
