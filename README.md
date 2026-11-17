<div align="center">

# 🏦 Consumer Financial Complaints (CFPB) — Exploratory Data Analysis


![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Numerical-013243?logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Plots-4C72B0)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)


</div>

---

## 📑 Table of Contents
- [Project Overview](#-project-overview)
- [Objectives](#-objectives)
- [Tools & Technologies](#-tools--technologies)
- [Dataset Information](#-dataset-information)
- [Project Workflow](#-project-workflow)
- [Key Insights](#-key-insights)
- [Recommendations](#-recommendations)
- [Project Status](#-project-status)
- [Author](#-author)

---

## 📌 Project Overview

Every year, thousands of consumers file complaints about banks and financial products with the U.S. **Consumer Financial Protection Bureau (CFPB)**. This project analyses **62,516 complaints (May 2017 – Aug 2023)** from the perspective of a bank's compliance and customer-experience analytics team.

The central business question:

> *Which products, issues and channels generate the most complaints, how has that changed over time, and how fairly and promptly are complaints being resolved?*

The dataset is almost entirely categorical and date-based, with no true numeric measures. 

---

## 🎯 Objectives

1. **Measure volume and trend** — how big is complaint volume, and is it growing? Is there seasonality?
2. **Find what dominates** — which products, issues, states and submission channels generate the most complaints?
3. **Understand company responses** — how often do consumers get an explanation vs. monetary or non-monetary relief, and does the outcome depend on product or channel?
4. **Assess timeliness** — how often do companies respond on time, and is it improving or worsening?
5. **Analyse routing delays** — how long does the CFPB take to forward a complaint to the company, and what drives delays?
6. **Turn findings into action** — give practical, evidence-backed recommendations.

---

## 🛠 Tools & Technologies

| Category | Tools |
|---|---|
| **Language** | Python 3 |
| **Data manipulation** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **Environment** | Jupyter Notebook |
| **Data format** | Excel (`.xlsx`) |

---

## 📊 Dataset Information

| Item | Details |
|---|---|
| **Source** | Consumer Complaints database, U.S. Consumer Financial Protection Bureau (CFPB) |
| **Files** | `Consumer_Complaints.xlsx` and `ConsumerComplaints_DataDictionary.csv` |
| **Size** | 62,516 rows × 12 columns |
| **Period** | May 2017 – Aug 2023 (2017 and 2023 are partial years) |
| **Granularity** | One row = one complaint about a financial product or service |
| **Duplicates** | None, on full rows or on `Complaint ID` |

**Column groups**

| Group | Columns |
|---|---|
| Identifiers | `Complaint ID` |
| Dates | `Date submitted`, `Date received` |
| Product hierarchy | `Product` (9 values) → `Sub-product` (46 values) |
| Issue hierarchy | `Issue` (76 values) → `Sub-issue` |
| Geography | `State` |
| Channel | `Submitted via` |
| Company outcome | `Company response to consumer`, `Company public response`, `Timely response?` |

**Missing values (all structural, so no rows were dropped)**

| Column | Missing | Treatment |
|---|---|---|
| `Timely response?` | 1,494 (2.4%) | Exactly the "In progress" complaints. Labelled `Pending` and **excluded** from timeliness rates rather than counted as failures |
| `Sub-issue` | 10,858 (~17%) | Not every issue has a sub-issue → `Not specified` |
| `Company public response` | 2,175 (~3.5%) | → `Not provided` |
| `Sub-product` | 7 | → `Not specified` |

---

## 🔄 Project Workflow

```
1. Problem Definition  →  2. Setup  →  3. Data Loading & Overview
                                                │
                                                ▼
                                   4. Data Pre-processing
        ┌─────────────────────────────────────────────────────────────┐
        │ Standardise column names · Check duplicates · Handle missing │
        │ values · Fix data types & logic checks · Feature engineering
          · Outlier review            │
        └─────────────────────────────────────────────────────────────┘
                                                │
                                                ▼
                               5. Exploratory Data Analysis
        ┌─────────────────────────────────────────────────────────────┐
        │ Univariate  →  Time series  →  Bivariate  →  Multivariate    │
        │ → Pivot tables & statistical tests                           │
        └─────────────────────────────────────────────────────────────┘
                                                │
                                                ▼
              6. Key Insights  →  7. Recommendations  →  8. Limitations
```

**Step-by-step**

1. **Problem definition** — business context, dataset selection and five guiding questions.
2. **Loading and overview** — shape, data types, summary statistics, data dictionary review.
3. **Pre-processing**
   - Standardised column names and confirmed there were no duplicates.
   - Investigated *why* each value was missing before choosing a treatment.
   - Harmonised near-duplicate categories (e.g. `Referral` vs `Web Referral`) and shortened long labels.
   - **Engineered features:** `routing_days`, `year`, `quarter`, `month`, `weekday`, `got_relief`, `got_monetary`, `is_closed`, `is_timely` and U.S. Census `region`.
   - Kept the heavy-tailed `routing_days` values (real business events, not errors) and used medians and non-parametric tests.
   - Reconciled the clean data against the raw data to confirm no rows were lost.

---


---



---






## 📍 Project Status

| Phase | Status |
|---|---|
| Problem definition and dataset selection | ✅ Completed |
| Data cleaning and feature engineering | ✅ Completed |

---

## 👩‍💻 Author

**Sumitha A M** — Aspiring Data Analyst | Cochin, Kerala
Skills: SQL · Power BI · Python · Excel

