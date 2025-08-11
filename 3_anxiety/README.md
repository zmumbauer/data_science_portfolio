# 🧠 Predicting Anxiety Attack Severity

This project uses self-reported lifestyle, physiological, and behavioral data to predict the **severity of anxiety attacks** on a scale of 1–10. The goal is to help healthcare providers, mental health practitioners, and individuals identify high-risk situations and take preventative action.

---

## 📌 Objective
Build a machine learning model that:
- Predicts anxiety attack severity based on daily lifestyle and physiological metrics.
- Identifies the most influential factors contributing to severe episodes.
- Supports targeted, data-driven interventions for anxiety management.

---

## 📊 Dataset Overview
- **Source**: Anxiety Attack Dataset (self-reported + physiological measurements)
- **Size**: Includes daily lifestyle and biometric data for multiple individuals.
- **Key Variables**:
  - Sleep hours
  - Stress levels
  - Heart rate
  - Breathing rate
  - Physical activity (steps/day)
  - Caffeine intake (mg/day)
  - Alcohol consumption
  - Dietary quality
  - Major life events
- **Transformations**:
  - Created **Caffeine Intake Category** (Low/Medium/High) based on <100mg, 100–300mg, >300mg thresholds.
  - One-hot encoding for categorical variables.
  - Standardization for numeric variables.

---

## 🛠 Methods
- **Preprocessing**:
  - Handling missing values.
  - Encoding categorical features.
  - Scaling numerical features.
- **Modeling**:
  - Linear Regression
  - Random Forest Regressor
  - Evaluation using MAE, RMSE, and R².
- **Feature Importance**:
  - Extracted from tree-based models to identify most predictive lifestyle factors.

---

## 📈 Analysis & Results
- **Regression Performance**:
  - Random Forest performed best with higher R² and lower RMSE than Linear Regression.
  - Sleep hours, stress level, heart rate, and caffeine intake category emerged as strong predictors.
- **Correlations**:
  - Strong negative correlation between sleep hours and severity.
  - High stress levels and elevated heart rate strongly associated with severe episodes.
- **Lifestyle Indicators**:
  - High caffeine (>300mg/day) often linked to higher severity scores.
  - Poor dietary quality and low activity correlated with more frequent severe episodes.

---

## 🏆 Key Findings
1. **Sleep & Stress**: Poor sleep and high stress are the strongest severity predictors.
2. **Physiological Signals**: Elevated heart and breathing rates are early warning signs.
3. **Lifestyle Choices**: High caffeine and poor diet exacerbate severity.

---

## 💡 Recommendations
- Encourage **consistent sleep routines** and stress-reduction techniques.
- Monitor **heart rate and breathing** as early-warning indicators.
- Reduce **high caffeine consumption** for individuals at risk.
- Incorporate **dietary improvements** into treatment plans.

---

## ⚖️ Ethical Considerations
- Self-reported data may include recall bias or inaccuracies.
- Models should **not replace clinical diagnosis**.
- Use predictions as part of a broader **holistic treatment plan**.
- Ensure privacy and confidentiality when handling sensitive health data.

---

## 📚 References
- American Psychiatric Association – [Anxiety Disorders](https://www.psychiatry.org/patients-families/anxiety-disorders)
- Mayo Clinic – [Generalized Anxiety Disorder: Diagnosis & Treatment](https://www.mayoclinic.org/diseases-conditions/generalized-anxiety-disorder)
