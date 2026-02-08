# 🧠 Case Study — Superstore Sales Prediction (2014–2017)

## Problem
Support **profit-focused decisions** for a retail “Superstore” by combining:
- clear business insights (what drives sales/profit)
- a baseline model to **predict Profit** from order and customer features

## Data
- **Dataset:** Sample - Superstore (Orders)
- **Typical grain:** one row per order line
- **Time range:** 2014–2017
- **Core fields:** sales, profit, discount, quantity, shipping mode, region/state/city, category/sub-category, dates

Notes:
- Profit can be negative (loss-making orders / heavy discounts).
- Date fields are used for seasonality and cohort-style views.

## Approach
- **EDA + KPIs:** sales/profit totals, margin, shipping time, seasonality peaks
- **Geography & product performance:** region/state/city, category/sub-category winners vs loss-makers
- **Customer analytics:** RFM segmentation + cohort retention signals
- **Modeling (target = Profit):**
  - preprocessing with imputation + one-hot encoding
  - baselines: **RandomForestRegressor** + **XGBoost** (when available)
  - evaluation: cross-validation with **R²** and **RMSE**
  - interpretation: permutation importance / feature importance

## Decisions & Takeaways
- Revisit **discount policy** in loss-making sub-categories (e.g., tables/bookcases patterns).
- Plan for seasonal peaks (often **December**) in staffing and inventory.
- Use the trained model to score new orders and support margin-aware pricing or promo decisions.

## Next Steps
- Add cost-aware thresholding (e.g., flag orders likely to be unprofitable).
- Train with time-aware splits to stress-test generalization across years.
- Ship the best model as a small API endpoint or dashboard component.
