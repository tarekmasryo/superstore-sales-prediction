# 🧠 Case Study — Superstore Sales Analytics and Profit Prediction

## Problem

Retail teams need more than a dashboard of totals. They need a practical view of:

- where sales and profit are coming from
- which categories or geographies create margin pressure
- which customers are valuable or at risk
- whether a baseline model can estimate order-line profit from known order details

This project turns the Superstore dataset into a decision-oriented analytics notebook.

---

## Data

- **Dataset:** Sample - Superstore
- **Time range:** 2014–2017
- **Grain:** one row per order line
- **Core fields:** sales, profit, quantity, discount, shipping mode, customer segment, geography, category, sub-category, order date, and ship date

Important data notes:

- Profit can be negative, especially in discount-heavy or loss-making sub-categories.
- Date fields support seasonality analysis and time-based model validation.
- The raw dataset is not included in the repo; users should place it under `data/raw/`.

---

## Approach

### 1. Data quality and preparation

The notebook checks:

- dataset shape and schema
- missing values
- duplicates
- date parsing
- categorical coverage
- basic numeric distributions

### 2. Business analytics

The EDA section covers:

- monthly and yearly sales patterns
- region, state, and city performance
- category and sub-category performance
- sales versus profit behavior
- discount impact on profit
- loss-making sub-categories
- customer-level sales and profit

### 3. Customer analytics

RFM segmentation is used to group customers into actionable segments such as:

- Champions
- Loyal
- Potential
- At Risk

These segments can support retention, reactivation, and account prioritization.

### 4. Profit prediction

The supervised modeling target is:

```text
Profit
```

The model estimates order-line profit using known transaction and customer/product attributes.

To reduce leakage and identifier noise, the notebook excludes:

- direct identifiers
- target-derived fields
- raw datetime fields after calendar extraction
- shipping outcome fields such as shipping time

The evaluation uses:

- time-based train/test split
- time-aware cross-validation
- RMSE
- R²

### 5. Exploratory sales forecast

The final section adds a lightweight monthly sales forecast and compares it against a seasonal naive baseline. This is included for planning context, not as a production forecasting system.

---

## Key decisions

- Reframe the project as **analytics + profit prediction**, not pure sales forecasting.
- Use a time-based holdout to better simulate future-period evaluation.
- Keep the model as a practical baseline rather than over-optimizing a small dataset.
- Save generated outputs under `artifacts/` for easier handoff and reuse.
- Keep the dataset outside Git to avoid tracking raw data files.

---

## Limitations

- The profit model is a baseline, not a production-ready decision engine.
- The forecast is exploratory and needs stronger backtesting before production planning.
- Discount and profitability decisions should be validated with business constraints and cost assumptions.
- The dataset is small and historical, so results should not be generalized without fresh data.

---

## Next steps

- Package the profit prediction workflow into a margin monitoring dashboard.
- Add drift checks by month, category, region, and discount band.
- Add scenario analysis for discount changes and loss-making sub-categories.
- Build a dedicated forecasting notebook if monthly sales forecasting becomes the primary goal.
