# 🏬 Superstore Sales Analytics and Profit Prediction

Practical retail analytics for the classic **Superstore dataset (2014–2017)**: data quality checks, sales and profit exploration, customer segmentation, order-line profit prediction, and a lightweight monthly sales forecast.

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Notebook](https://img.shields.io/badge/Format-Jupyter%20Notebook-orange)
![License](https://img.shields.io/badge/License-MIT-green)

---

## ✨ What this project covers

- 📊 **Sales and profit analytics** across months, regions, categories, and sub-categories
- 🧹 **Data quality checks** for missing values, duplicates, date parsing, and categorical coverage
- 👥 **Customer analytics** using RFM segmentation
- 💸 **Discount and margin review** to surface loss-making product areas
- 🤖 **Order-line profit prediction** using reusable preprocessing and baseline regression models
- 📈 **Exploratory monthly sales forecast** for lightweight planning context
- 📦 **Generated artifacts** such as model performance tables, feature importance, forecast evaluation, and the best baseline model

---

## 🎯 Main business questions

This notebook is designed to answer:

1. Which months, regions, categories, and sub-categories drive sales and profit?
2. Where do discounts, geography, or product mix create margin pressure?
3. Which customers are most valuable or at risk based on RFM segmentation?
4. Can we estimate order-line profit from known order details?
5. What does a simple monthly sales forecast suggest for near-term planning?

---

## ⚠️ Scope note

The main supervised model is **profit prediction**, not pure future sales forecasting.

The model predicts **line-item profit after core transaction details are known**. The final forecasting section is included as a lightweight exploratory sales trend estimate. A dedicated forecasting workflow with stronger backtesting would be needed before using forecasts for production planning.

---

## 📁 Repo layout

```text
.
├── superstore-sales-analytics-profit-prediction.ipynb
├── data/
│   └── raw/
│       ├── .gitkeep
│       └── README.md
├── artifacts/
│   ├── .gitkeep
│   └── README.md
├── CASE_STUDY.md
├── CHANGELOG.md
├── requirements.txt
├── LICENSE
└── .gitignore
```

---

## 📦 Dataset

Expected file name:

```text
Sample - Superstore.csv
```

The notebook supports both Kaggle and local GitHub-style usage:

| Environment | Expected path |
|---|---|
| Kaggle | `/kaggle/input/superstore-dataset-final/Sample - Superstore.csv` |
| Local / GitHub | `data/raw/Sample - Superstore.csv` |
| Notebook run from subfolder | `../data/raw/Sample - Superstore.csv` |

The dataset file is **not tracked** in this repo.

---

## 🚀 Run locally

Create an environment and install dependencies:

```bash
python -m venv .venv
```

Activate it:

```bash
# Windows
.venv\Scripts\activate

# macOS/Linux
source .venv/bin/activate
```

Install requirements:

```bash
pip install -r requirements.txt
```

Then place the dataset here:

```text
data/raw/Sample - Superstore.csv
```

Open and run:

```text
superstore-sales-analytics-profit-prediction.ipynb
```

---

## 🧪 Modeling approach

The modeling section uses:

- time-based train/test split
- time-aware cross-validation on a recent training slice
- `ColumnTransformer` preprocessing
- `RandomForestRegressor` baseline and compact tuning
- optional `XGBoost` baseline when available
- RMSE and R² for evaluation
- feature importance for interpretation

The model excludes direct identifiers, target-derived fields, raw datetimes, and shipping outcome fields to reduce leakage and identifier noise.

---

## 📊 Generated artifacts

When the notebook is run, it writes local outputs to `artifacts/`:

```text
artifacts/
├── best_profit_model.joblib
├── feature_importance.csv
├── forecast_evaluation.csv
└── model_performance.csv
```

These files are ignored by Git because they are generated outputs.

---

## 🧾 Case study

See [`CASE_STUDY.md`](CASE_STUDY.md) for the project story, technical decisions, limitations, and next steps.

---

## 📄 License

MIT License. See [`LICENSE`](LICENSE) for details.
