# ✈️ TSA Complaints Analysis (2015–2019)

This project analyzes Transportation Security Administration (TSA) customer complaint data from 2015–2019 to help **TSA Regional Operations Executives** and **Airport Managers** identify high-risk airports and problem categories, enabling targeted operational improvements.

---

## 📌 Objective
Evaluate patterns in TSA complaints by airport, category, and time period to guide:
- Targeted staff training
- Process redesign for baggage screening
- Technology investment in high-complaint regions

---

## 📊 Dataset Overview
- **Source**: TSA public complaint data (2015–2019) merged with U.S. airport metadata
- **Size**: Multiple CSVs covering complaints by airport, category, and subcategory
- **Key Variables**:
  - `airport` (IATA code) & airport name
  - `year_month` – complaint date
  - `count` – complaint volume
  - `clean_cat` – cleaned complaint category
  - Latitude & longitude (for mapping)
- **Transformations**:
  - Filtered to U.S. airports
  - Merged complaint data with airport geolocation
  - Created pivot tables for heatmaps

---

## 📈 Exploratory Analysis
- **Top Airports by Complaints**: Identified 10 airports with the highest total complaints over 5 years.
- **Monthly Trends**: Line charts show fluctuations and seasonal spikes in complaint volume for top airports.
- **Heatmap by Month/Airport**: Highlights persistent issues and seasonal peaks at major airports.
- **Category Distributions**: Box plots reveal variability in complaint volumes for top categories (e.g., baggage, customer service).
- **Spatial Mapping**: Geographical plots show concentration of high-complaint airports.

---

## 🏆 Key Findings
1. **Concentration at Major Hubs**: Most complaints come from a small set of high-volume airports.
2. **Seasonal Spikes**: Complaint volumes increase during holiday travel periods.
3. **Baggage & Customer Service Issues**: These categories show the greatest variability and highest counts.
4. **Geographic Clustering**: High complaint rates concentrated in certain metropolitan hubs.

---

## 💡 Recommendations
- Prioritize **staff training** in baggage handling and customer interaction at top 10 complaint airports.
- Deploy **seasonal surge staffing** in anticipation of holiday travel peaks.
- Consider **technology upgrades** in baggage screening at high-complaint locations.
- Establish **monthly monitoring dashboards** to track complaint trends and act quickly.

---

## ⚖️ Ethical Considerations
- All data is public and anonymized; no passenger identities are included.
- Results should be used to improve service quality, not penalize staff without additional context.
- Data cleaning and filtering steps are documented to maintain transparency.

---

## 📚 References
- Transportation Security Administration (TSA) – Public Complaint Data
- IATA/ICAO Airport Metadata
