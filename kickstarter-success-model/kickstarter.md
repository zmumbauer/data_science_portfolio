# 🎯 Kickstarter Campaign Success Prediction

This project explores whether the success of a crowdfunding campaign can be predicted using only the metadata available before launch. Leveraging a large dataset of over 160,000 Kickstarter projects, the goal is to assist creators in optimizing campaigns and help platforms surface high-potential projects.

## 📌 Objective
Determine if campaign success (funded vs. not funded) can be accurately predicted using pre-launch features such as campaign goal, duration, location, and promotional flags.

## 📊 Dataset Overview
- **Source**: Web-scraped Kickstarter data
- **Size**: 160,000+ rows
- **Key Fields**:
  - Campaign goal (USD)
  - Launch and deadline timestamps
  - Category and location (JSON-parsed)
  - staff_pick, spotlight, prelaunch_activated, and other binary tags
- **Target Variable**: `successful` (1 if campaign met funding goal, 0 otherwise)

## 🧹 Data Preparation
- Removed duplicates and campaigns with invalid goals
- Extracted city/country from nested JSON
- Converted Unix timestamps to datetime and derived `duration_days`
- Dropped post-launch or outcome-based features to prevent leakage
- Binary-encoded all boolean fields

## 📈 Exploratory Analysis
- Heatmaps revealed strong correlation between staff_pick and success
- Prelaunch_activated campaigns showed significantly higher success rates
- Duration distribution peaked near 30 days, with extremes showing higher success rates
- Goal distribution was highly skewed — most campaigns asked for <$10,000

## 🧠 Models Used
Three classification algorithms were tested using only pre-launch data:
- Logistic Regression (Baseline)
- Random Forest (with GridSearchCV tuning)
- XGBoost

Class imbalance was addressed using SMOTE, and models were evaluated using:
- Accuracy
- F1 Score
- Precision/Recall
- ROC AUC

## 🏆 Model Results

| Model               | Accuracy | F1 Score | ROC AUC |
|--------------------|----------|----------|---------|
| Logistic Regression| 67%      | 0.66     | 0.76    |
| Random Forest      | 72%      | 0.77     | 0.79    |
| XGBoost            | 73%      | 0.79     | 0.81    |

**XGBoost** outperformed the others with the best recall and AUC.

## 🔍 Key Insights
- Campaigns with **low funding goals**, **staff_pick**, and **prelaunch activation** flags had higher chances of success.
- Duration has a **nonlinear effect**: 1–15 and 61–90 day campaigns had better outcomes than 30–45 day ones.
- SHAP values confirmed the importance of these features and showed how they impacted individual predictions.

## 💡 Recommendations
- **For Creators**: Set achievable goals, build early momentum, and time your campaign strategically.
- **For Platforms**: Use predictive models to assist new creators and spotlight high-potential underdogs.

## ⚖️ Ethical Considerations
- Avoid reinforcing bias toward campaigns with more platform support or previous success.
- Model interpretability (via SHAP) was prioritized to ensure transparency and fairness.

## 📚 References
- Lundberg, S., & Lee, S. (2017). A unified approach to interpreting model predictions. [arXiv:1705.07874](https://arxiv.org/abs/1705.07874)
- Smithwrick, B. (2024). [Award-Winning Kickstarter Campaign Tips](https://updates.kickstarter.com/the-secrets-to-creating-award-winning-kickstarter-campaigns/)
