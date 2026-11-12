# Lung_Cancer
Lung-Cancer-Risk-Dataset with machine learning \ data science
# 🫁 Lung Cancer Risk Analysis & Prediction

> EraaSoft Community Challenge project — **[Your Name]** | Track: **[Your Track]** | Group Code: **[Your Group Code]**

Exploratory analysis, interactive dashboards, and a machine-learning model that estimates lung-cancer risk from patient risk factors, to support **early screening and prioritisation of high-risk patients**.

---

## 🎯 Problem
Lung cancer is often detected late, when treatment options are limited. Screening everyone is expensive, so the question is: **which patients should be prioritised for early screening?**

This project answers it by:
1. Finding which risk factors matter most (EDA + dashboards).
2. Building a model that predicts a patient's probability of lung cancer.

## 📦 Dataset
- `lung_cancer_dataset.csv` — 50,000 patients, 11 columns.
- Target: `lung_cancer` (Yes / No). Overall rate: **68.7%** (imbalanced).
- Features: age, gender, pack-years, radon exposure, asbestos exposure, secondhand smoke, COPD, alcohol consumption, family history.
- ⚠️ The data appears **synthetic** (very sharp thresholds), so results are for learning only.

**Cleaning decisions**
- `alcohol_consumption` had ~33% blanks. Existing values are only *Moderate* / *Heavy*, so blanks were treated as **"None"** (assumption).
- Dropped `patient_id`. No duplicates found.

## 🔍 Key Insights
| Finding | Result |
|---|---|
| Smoking intensity | **~41%** cancer rate at ≤ 20 pack-years → **~76%** above 20 |
| Age | **~60%** at ≤ 50 years → **~74%** above 50 |
| Radon | High exposure **~78%** vs ~64-65% for Low/Medium |
| Asbestos / COPD | ~76% vs ~62% when not exposed |
| Gender | No difference (68.7% both) |
| **Risk-factor accumulation** | 0 factors **39%** → 3 factors **78%** → 5 factors **96%** |

## 🤖 Model Results (20% hold-out test set)
| Model | AUC | Recall | Precision |
|---|---|---|---|
| **Logistic Regression** | **0.778** | 0.688 | 0.837 |
| Gradient Boosting | 0.776 | 0.905 | 0.765 |
| Random Forest | 0.756 | 0.696 | 0.822 |

- Lowering the decision threshold to 0.3 raises recall to ~89% — important in medicine, where **missing a patient is worse than a false alarm**.
- Features engineered: `age_over_50`, `heavy_smoker` (> 20 pack-years), `risk_factor_count`.

## 📊 Dashboards
- **Excel** (`Lung_Cancer_Dashboard.xlsx`): 4 KPI cards, 7 charts, age × radon heatmap, and 5 dropdown filters that update everything.
- **Power BI**: see `PowerBI_Dashboard_Guide.md` for DAX measures, layout, and the colour theme.

> 📸 Add your dashboard screenshots here: `![Dashboard](images/dashboard.png)`

## 🛠 Tech Stack
Python · pandas · NumPy · scikit-learn · matplotlib · seaborn · Jupyter · Power BI · Excel (openpyxl formulas)

## 📁 Repository Structure

├── Lung_Cancer_Prediction.ipynb      # full analysis + model
├── lung_cancer_dataset.csv           # raw data
├── lung_cancer_clean_for_powerbi.csv # cleaned data for BI
├── Lung_Cancer_Dashboard.xlsx        # interactive Excel dashboard
├── PowerBI_Dashboard_Guide.md        # Power BI build guide
├── requirements.txt
└── README.md


## ▶️ How to Run
```bash
pip install -r requirements.txt
jupyter notebook Lung_Cancer_Prediction.ipynb
```
Keep the CSV in the same folder as the notebook.

## ⚠️ Limitations
- Synthetic-looking data; model AUC ≈ 0.78 is the ceiling of this dataset.
- Correlation is not causation.
- Decision-support tool for **screening prioritisation only — not a diagnosis or medical advice**.

## 👤 Author
**[mostafa mohamed sayed]** — [www.linkedin.com/in/mostafa-mohamed-475886277] · [mostafamohamed11408@gmail.com]

#EraaSoft_Community_Challenge
