# 🏬 Superstore Sales Prediction

A production-style **notebook repo** for the classic Superstore dataset (2014–2017):  
**EDA → business insights → profit prediction → saved artifacts**.

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Notebook](https://img.shields.io/badge/Format-Jupyter%20Notebook-orange)

---

## ✅ What’s inside

- 📊 Decision-ready EDA (seasonality, geo/product performance, margins)
- 👥 Customer analytics (RFM segmentation + cohort-style retention views)
- 🤖 Profit modeling (`Profit` as target) with:
  - RandomForest baseline + tuning
  - XGBoost baseline (when available)
  - CV metrics (R² / RMSE) + feature importance
- 📦 Saved outputs in `artifacts/` (model + metrics table)

---

## 📁 Repo layout

```text
.
├── data-analysis-for-superstore-dataset.ipynb
├── data/
│   └── raw/                 # place the dataset file here (not tracked)
├── artifacts/               # saved model + metrics (not tracked)
├── repo_utils/
│   └── pathing.py           # local data/raw + Kaggle fallback
├── CASE_STUDY.md
├── requirements.txt
├── LICENSE
└── .gitignore
```

---

## 🚀 Run locally

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
```

Open and run the notebook top-to-bottom.

---

## 📦 Dataset

Expected file name: **`Sample - Superstore.csv`**

- **Local (recommended):** put it in `data/raw/` (see `data/raw/README.md`)
- **Kaggle:** the notebook falls back to `/kaggle/input/superstore-dataset-final/...`

The path logic lives in: `repo_utils/pathing.py`.

---

## 🧾 Case Study

See **CASE_STUDY.md** for the project story, decisions, and next steps.
