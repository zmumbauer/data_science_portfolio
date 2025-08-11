# 💻 Job Satisfaction & Retention Prediction

This project analyzes the **2024 Stack Overflow Developer Survey** to identify predictors of job satisfaction and the likelihood of job change among developers. The goal is to help **technology companies** improve retention strategies and assist **developers** in assessing job fit.

---

## 📌 Objective
Use regression and classification modeling to:
- Predict developer job satisfaction (JobSat).
- Estimate the probability of job change intent (JobChangeIntent).
- Identify key factors influencing satisfaction and retention risk.

---

## 📊 Dataset Overview
- **Source**: Stack Overflow Developer Survey 2024 (public dataset)
- **Size**: 65,437 responses, 114 variables
- **Key Variables**:
  - JobSat (0–10 scale)
  - Employment type
  - ConvertedCompYearly (compensation in USD)
  - Developer type (DevType)
  - Years of coding experience (YearsCode)
  - Remote work status
  - Country, education level, age
- **Target Variable**: `JobChangeIntent` — derived from JobSat ≤ 5 to indicate intent to leave.
- **Preprocessing**:
  - Dropped columns with >50% missing values.
  - Filtered out outlier compensation values using IQR.
  - Encoded categorical variables (one-hot/label encoding).
  - Engineered features: experience level, tech diversity score, compensation category, age group.

---

## 🛠 Methods
- **Regression**: Linear Regression, Random Forest Regressor (to predict JobSat)
- **Classification**: Logistic Regression, Random Forest Classifier (to predict JobChangeIntent)
- **Evaluation Metrics**:
  - Regression: RMSE, MAE, R²
  - Classification: Accuracy, F1-score, ROC-AUC
- **Data Split**: 70/15/15 train–validation–test with stratified sampling to address class imbalance.

---

## 📈 Analysis & Results
- **Regression**:
  - Linear Regression: RMSE = 2.088, R² = 0.027 (low predictive power)
  - Random Forest Regressor: Train R² = 0.859, Validation R² = -0.082 (overfitting)
- **Classification**:
  - Logistic Regression: ROC-AUC = 0.644, F1 (minority class) = 0.000
  - Random Forest: ROC-AUC = 0.681, F1 (minority class) = 0.000
- **Exploratory Insights**:
  - 60% of developers rated satisfaction at ≥7 (Figure 1).
  - Median salary = $65k; max salary reported = $16M (Figure 2).
  - Majority demographic: age 25–34, remote/hybrid, U.S.-based (Figure 3).
  - Key predictors: tech diversity, compensation, experience level (Figure 5).

---

## 🏆 Key Findings
1. Class imbalance (only 8.6% likely to leave) severely limits classification accuracy.
2. Linear models struggled; tree-based models overfit without generalizing well.
3. Compensation, tech diversity, and experience level are strong predictors of satisfaction.

---

## 💡 Recommendations
- Monitor metrics like tech diversity and experience level in retention planning.
- Conduct quarterly JobSat surveys to track sentiment changes.
- Retrain models regularly to adapt to market conditions.
- Apply SMOTE or similar techniques to mitigate imbalance in classification tasks.

---

## ⚖️ Ethical Considerations
- Survey is self-selected; may not generalize to underrepresented groups.
- Outputs must be aggregated (team/department level) and anonymized.
- Predictions should guide supportive, not punitive, actions.
- Transparency and human oversight are essential.

---

## ❓ Audience Q&A
1. **Why JobSat ≤ 5 for intent to leave?** Aligns with engagement research; midpoint or lower signals higher turnover risk.
2. **Why tree-based models over linear?** Better at capturing nonlinear feature interactions.
3. **How address imbalance?** Tested oversampling/undersampling; used SMOTE for advanced models.
4. **Features dropped due to missing data?** Yes, >50% missing dropped; retained key demographics and career factors.
5. **Why low F1 for Logistic Regression?** Without resampling, model defaulted to majority class.
6. **Top predictors?** Tech exposure, compensation, years coding, country.
7. **Directly usable for companies?** Must be retrained on internal data for accuracy.
8. **Generalizable to other regions/roles?** Limited due to survey demographics.
9. **Ethical safeguards?** Aggregate predictions, ensure transparency, avoid punitive use.
10. **Next steps for orgs?** Use as screening tool, pair with qualitative feedback, pilot targeted strategies.

---

## 📚 References
- Stack Overflow Developer Survey 2024 (https://survey.stackoverflow.co/)
- Imbalanced-learn documentation on SMOTE
- Breiman, L. (2001). Random Forests. Machine Learning, 45(1), 5–32.
