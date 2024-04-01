# Credit Card Fraud Detection
Kaggle: https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

### I. EDA
1. **Class(Target) Distribution**: The dataset exhibits a highly imbalanced distribution between legitimate transactions (284,315 instances) and fraudulent transactions (492 instances).
2. **Missing Values**: No missing values are present.
3. **Variable Types**  
    - 'V1'\~'V28': Variables transformed via PCA (continuous variables)
    - 'Time', 'Amount': Continuous variables
    - 'Class': Response variable (categorical variable)
4. **Multicollinearity**: No significant correlations observed among the variables.
5. **Distribution of Variables**
      - 'Amount': The distribution is right-skewed, suggesting the need for a log transformation.
      - 'Time': Has been modified to add an 'Hour' variable, allowing the examination of transaction volumes based on a 24-hour cycle.
      - 'V1'\~'V28': 'V12', 'V14', 'V17' variable show distinctly different distributions between legitimate and fraudulent transactions.

### II. Data Preprocessing
1. **Removal of Outliers** in 'V12', 'V14', 'V17'
2. Application of **Standard Scaling** to the 'Amount' and 'Time' variables
3. Attempted **SMOTE** to address the imbalance in the 'Class' response variable

### III. Modeling
- Utilized the validation set to identify the optimal hyperparameters for tuning.
- Decided against proceeding with SMOTE as it did not lead to a significant performance improvement.

1. **No Outlier Removal**
<img width="873" alt="Outlier Removal X" src="https://github.com/ssuummm/creditcard_fraud_detection/assets/139437305/9b165a48-0038-49c3-a477-dfc623ae6af4">
<br/>
<br/>

2. **Outlier Removal Conducted** (f1 score)
<img width="859" alt="Outlier Removal O" src="https://github.com/ssuummm/creditcard_fraud_detection/assets/139437305/e254a313-b61a-487f-9a05-95a1de23563a">

### Conclusion
- Boosting-based models such as XGBoost, ADABoost, and LightGBM have shown good performance.
- While removing outliers generally leads to performance improvement, it's important to note that outliers can also contain meaningful information. Excessive removal may result in significant information loss.
