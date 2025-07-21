# 🏠 Airbnb Revenue Prediction

This project develops a machine learning model to predict annual revenue for Airbnb listings in the Northeast U.S., helping hosts and platforms make more informed decisions around pricing, features, and listing management.

---

## 📌 Objective
Estimate `estimated_revenue_l365d` using property metadata, host characteristics, location details, and guest sentiment — all available pre-booking.

## 🌐 Regions Included
- Rhode Island  
- Boston  
- Cambridge  
- New York City  

---

## 📊 Data Sources
- **Listings Data**: 48,433 records with 80+ features (Inside Airbnb)
- **Reviews Data**: 1.5M+ comments used for sentiment analysis
- **Target Variable**: `estimated_revenue_l365d`

---

## 🧹 Data Cleaning & Feature Engineering
- Dropped high-missing columns (e.g., `license`, `host_about`)
- Converted percentage fields (e.g., `host_response_rate`) to floats
- Binary-encoded booleans like `host_is_superhost`
- Extracted review sentiment using **VADER**
- Parsed complex fields:
  - `bathrooms_text` → Full/half, private/shared counts
  - `amenities` → Over 700 binary indicators
- Created derived features:
  - Host tenure (`host_since_days`)
  - Avg. review length
  - Review count, region, property type (encoded)

Total: Over 200 engineered features

---

## 📈 Exploratory Analysis
- Revenue distribution was highly skewed — log transformation applied
- Correlation heatmaps showed important drivers like `price`, `review_count`, and `minimum_nights`
- Region-specific revenue trends highlighted variance across cities

---

## 🧠 Modeling Approaches
Three models were compared:

| Model                     | RMSE         | R²     |
|--------------------------|--------------|--------|
| Random Forest Regressor  | $12,978.97   | 0.778  |
| HistGradientBoosting     | $13,753.88   | 0.751  |
| ElasticNet (baseline)    | $23,324.33   | 0.283  |

➡️ **Random Forest** achieved the best balance of accuracy and interpretability.

---

## 🔍 Top Features
- `avg_review_length`
- `host_acceptance_rate`
- `review_count`
- `minimum_nights`
- `price`
- `sentiment`

See full feature importance chart in the notebook.

---

## ✅ Use Cases
- **For Hosts**: Get predictive insights on expected revenue; tweak pricing and amenity offerings.
- **For Airbnb**: Improve host onboarding, highlight high-performing listings, support pricing simulations.

---

## ⚖️ Ethical Considerations
- No use of protected attributes
- Model avoids favoring experienced hosts by focusing on listing metadata
- Sentiment analysis uses only public, anonymized review data

---

## ❗ Limitations
- No modeling of seasonality due to missing calendar data
- Amenity sparsity and skewed distributions may affect generalization
- Assumes `estimated_revenue_l365d` is accurate and consistent across regions

---

## 🔮 Future Improvements
- Integrate calendar data to model seasonal trends
- Fine-tune hyperparameters for boosting models
- Build dashboards for scenario planning (e.g., price vs. occupancy tradeoffs)
- Extend the model to dynamic pricing engines

---

## 📂 Files
- `airbnb_model.ipynb`: Full analysis and model pipeline
- `airbnb_cleaned_optimized.pdf`: Cleaned and processed notebook summary
- `whitepaper.pdf`: Formal project documentation
- `airbnb.pptx`: Presentation with speaker notes

