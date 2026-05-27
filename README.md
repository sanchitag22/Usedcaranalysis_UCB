# What Drives the Price of a Used Car?
### CRISP-DM Analysis | Used Car Dealership Pricing Study
**Author:** Sanchita Gawand 

## Project Overview

This project applies the **CRISP-DM framework** to analyze what factors drive used car prices, providing actionable recommendations to a used car dealership on how to optimize their inventory and pricing strategy.

# 1. Business Objective 
Used car dealerships operate on thin margins in a highly competitive market where pricing decisions directly determine profitability and inventory turnover. Price a vehicle too high and it sits on the lot, tying up capital; price it too low and money is left on the table. Without a data-driven approach, pricing relies on intuition and experience alone, inconsistent and hard to scale.


---

# 2. Source: 
  a. Used car dataset
  b. Python File: https://github.com/sanchitag22/Usedcaranalysis_UCB/blob/main/Used_car_price_analysis_Sanchitag.ipynb

---
# 3. Summary of Findings

Analysis of 426,000+ used car listings reveals that **vehicle age, mileage, manufacturer, condition, and vehicle type** are the strongest drivers of used car price.

| Factor | Impact |
|--------|--------|
| Vehicle age | Each additional year significantly lowers price; steepest drop in years 0–8 |
| Mileage (odometer) | Strongest numeric predictor: Strong negative correlation ; vehicles under 60K miles hold value best |
| Vehicle type | Trucks and SUVs command the highest median prices in the market |
| Manufacturer | GMC, Ram, Toyota, and Honda sustain strong resale value |
| Condition | "Like new" and "excellent" condition vehicles price 30–50% above "fair" |
| Fuel type | Diesel commands a premium; electric vehicles also price above average |
| Transmission | Automatic and 4WD configurations add measurable price uplift |

---

# 4. Recommendations for Used Car Dealerships

1. **Prioritize newer, low-mileage inventory** : vehicles 5 years old or newer with under 60,000 miles are easiest to price competitively and turn over quickly.
2. **Stock trucks, SUVs, and select luxury brands** : these segments show the strongest pricing power and sustained resale demand.
3. **Invest in reconditioning** : upgrading a vehicle from "fair" to "good" or "excellent" condition typically yields a price uplift that more than covers the cost.
4. **Favor automatic transmission and 4WD vehicles** : these command consistent premiums and have broader buyer appeal.
5. **Be cautious with salvage-title vehicles** : they are priced dramatically lower and present higher sales risk.

---

# 5. Model Performance

| Model | R² | RMSE |
|-------|----|------|
| Linear Regression | 0.700 | $7,302 |
| **Ridge Regression** *(selected)* | **0.700** | **$7,303** |
| Lasso Regression | 0.694 | $7,456 |

**Ridge Regression** was selected as the final model. It matches Linear Regression on both metrics while offering better stability and generalizability to unseen listings. The model explains approximately **70% of price variation** using listing features alone. The remaining 30% is driven by factors not captured in the dataset (vehicle history, accident records, local market conditions).

**Evaluation metric:** RMSE was chosen because it is in dollar terms and directly meaningful for a pricing problem , large errors are costly for dealership profitability.

---

# 6. Dataset Descriptive Statistics (after cleaning)

| Feature | Mean | Median | Std Dev | Min | Max |
|---------|------|--------|---------|-----|-----|
| Price ($) | 18,426 | 14,900 | 13,841 | 500 | 150,000 |
| Odometer (miles) | 98,043 | 89,000 | 66,215 | 0 | 350,000 |
| Vehicle age (years) | 8.4 | 7 | 5.6 | 0 | 32 |

*Cleaned dataset: ~200,000 records after removing extreme price outliers, unrealistic years, and rows with missing values in key modeling columns.*

---

# 7. Next Steps

- **Enrich data** — add vehicle history (accidents, recalls), days-on-lot, and local market pricing data
- **Build segment-specific models** — separate models for trucks, luxury, and economy segments may outperform the unified model
- **Deploy as a pricing tool** — integrate the Ridge model into a lightweight pricing calculator for the sales team
- **Retrain quarterly** — EV adoption trends, fuel prices, and economic cycles shift used car pricing dynamics regularly

---

# 8. Tools & Libraries

`pandas` · `numpy` · `matplotlib` · `seaborn` · `scikit-learn`  
Models: Linear Regression, Ridge Regression (GridSearchCV), Lasso Regression  
Validation: 5-fold cross-validation · RMSE · R²

## Repository Structure

```
├── README.md                        ← This file
├── used_car_price_analysis.ipynb    ← Full analysis notebook
└── vehicles.csv                     ← Dataset (download from Kaggle)
```

---

## How to Run

1. Clone this repository
2. Download `vehicles.csv` from [Kaggle](https://www.kaggle.com/datasets/austinreese/craigslist-carstrucks-data)
3. Place `vehicles.csv` in the same folder as the notebook
4. Run `used_car_price_analysis.ipynb` in Jupyter or Google Colab

**Dependencies:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`

---

## CRISP-DM Framework Applied

```
Business Understanding → Data Understanding → Data Preparation
        ↓
    Modeling → Evaluation → Deployment (Recommendations)
```

