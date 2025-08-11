# 🧪 Clinical Trial Success Prediction

This project uses metadata from the **Aggregate Analysis of ClinicalTrials.gov (AACT)** to predict the likelihood of a clinical trial’s success based on its design features. The goal is to help **pharmaceutical companies**, **research sponsors**, and **regulatory strategists** make more informed decisions before and during trial execution.

---

## 📌 Objective
Develop a predictive model that:
- Estimates the probability of a trial’s success using structured design data.
- Identifies the most important features influencing success.
- Supports early decision-making and risk assessment.

---

## 📊 Dataset Overview
- **Source**: Aggregate Analysis of ClinicalTrials.gov (AACT)
- **Tables Used**: Study metadata, sponsors, interventions, design elements, outcomes, eligibility criteria.
- **Key Variables**:
  - Phase
  - Study type
  - Enrollment size
  - Masking
  - Allocation
  - Intervention type
  - Agency class
  - Outcome type
  - Gender eligibility
  - Age ranges
- **Target Variable**: Trial success, proxied by submission of results.
- **Preprocessing**:
  - Missing value imputation.
  - One-hot encoding for categorical variables.
  - Feature engineering for derived metrics.

---

## 🛠 Methods
- **Models Tested**:
  - Logistic Regression (scaled inputs)
  - Random Forest
  - XGBoost
- **Evaluation Metrics**: AUC-ROC, precision, recall, F1-score.
- **Interpretability**: SHAP analysis for feature importance.
- **Data Split**: 80/20 train–test split.

---

## 📈 Analysis & Results
- **Best Model**: Random Forest – AUC = 0.80, F1-score = 0.71 (successful trials).
- **XGBoost**: Underperformed in recall.
- **Logistic Regression**: Only slightly better than random.
- **Key Predictors** (SHAP):
  - Enrollment size
  - Sponsor type
  - Presence of primary outcomes
  - Intervention type

---

## 🏆 Key Findings
1. Decision-tree-based models outperform linear and boosting approaches in this domain.
2. Sponsor type and trial scale are strong predictors of success.
3. Presence of clearly defined primary outcomes correlates with better results.

---

## 💡 Recommendations
- Use Random Forest predictions as a **decision support tool**, not a sole decision-maker.
- Develop **therapeutic area-specific models** for higher precision.
- Provide **probabilistic outputs** to allow risk threshold calibration.

---

## ⚖️ Ethical Considerations
- **Bias Risks**: Potential to deprioritize underrepresented diseases.
- **Transparency**: Essential — use SHAP or similar interpretability tools.
- **Use Case Boundaries**: Model should complement expert judgment, not replace it.

---

## ❓ Audience Q&A
1. How was trial success defined, and why was result submission used as a proxy?
2. Why did Random Forest outperform XGBoost and Logistic Regression?
3. How were trials with missing or ambiguous design characteristics handled?
4. Can the model be applied at the proposal stage?
5. Does the model reinforce existing biases in clinical research funding?
6. How well would predictions generalize to international trials?
7. What validation strategies could improve generalizability?
8. Could the model be tailored to specific therapeutic areas?
9. What safeguards exist to reduce bias from eligibility and demographic fields?
10. How could this model help detect low-quality or noncompliant trials early?

---

## 📚 References
- ClinicalTrials.gov AACT Database
- Lund, B. et al. (2020). Predicting Clinical Trial Success: A Machine Learning Approach. *Nature Medicine*.
- Lundberg, S.M., & Lee, S.-I. (2017). A Unified Approach to Interpreting Model Predictions. *Advances in Neural Information Processing Systems*.
