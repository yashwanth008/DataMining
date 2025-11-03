# 🧠 Assignment 4 — CRISP-DM, KDD, and SEMMA: Three Methodologies in Practice

### 📅 San José State University — CMPE 256: Data Science Systems  
**Student:** *Venkata Yashwanth Paladugu*  
**Date:** 2nd November 2025  

Demo video: https://drive.google.com/file/d/1yGRzHAl8v1xj3yDbZcqkpUJcFLNyQbkm/view?usp=sharing

---

## 🧭 Project Overview

This repository demonstrates **three structured data science methodologies** —  
**CRISP-DM**, **KDD**, and **SEMMA** — applied to different datasets and problem types.

Each subdirectory (`crispdm/`, `kdd/`, and `semma/`) contains a **complete, end-to-end project**:
- all methodological phases,
- Python code in Google Colab format,
- AI-assisted critiques (using GPT-5 critic personas),
- generated artifacts (models, figures, and reports),
- and a Medium article + short demo video.

---

## 🧰 Tech Stack

| Category | Tools / Libraries |
|-----------|-------------------|
| Data | `pandas`, `numpy`, `openpyxl` |
| Modeling | `scikit-learn`, `xgboost`, `mlxtend`, `statsmodels` |
| Visualization | `matplotlib`, `seaborn`, `plotly` |
| Deployment | `FastAPI`, `joblib`, `uvicorn` |
| Environment | Google Colab (Python 3.12) |
| AI Reviewer | GPT-5 / Claude (critic persona prompts) |

---

## 📊 Projects Overview

### **1️⃣ CRISP-DM — Telco Customer Churn Prediction**
**Goal:** Predict which telecom customers are likely to leave the service.  
**Dataset:** Kaggle Telco Customer Churn (7,043 rows, 20 features)  
**Model:** XGBoost Classifier (AUC = 0.84, PR-AUC = 0.76)

**Phases:**
1. Business Understanding — Defined retention KPIs and cost constraints.  
2. Data Understanding — Performed EDA and data quality checks.  
3. Data Preparation — Encoding, imputation, feature scaling.  
4. Modeling — Compared Logistic, RF, and XGBoost.  
5. Evaluation — Chose optimal threshold and validated results.  
6. Deployment — Exported model pipeline and FastAPI service.

---

### **2️⃣ KDD — Market Basket Association Rules**
**Goal:** Identify frequent product combinations to optimize cross-selling.  
**Dataset:** Online Retail (10,000 invoices subset)  
**Technique:** FP-Growth (min_support = 0.02, max_len = 2)

**Pipeline:**
1. Selection → clean transactions.  
2. Preprocessing → remove cancellations.  
3. Transformation → build invoice × item matrix.  
4. Data Mining → discover frequent itemsets.  
5. Interpretation → visualize top rules by lift.

**Example Rules:**
| Antecedent | Consequent | Lift |
|-------------|-------------|------|
| Tea Cup | Tea Saucer | 3.12 |
| Gift Bag | Gift Wrap | 2.74 |
| Candle Holder | Scented Candle | 2.45 |


---

### **3️⃣ SEMMA — Credit Card Default Modeling**
**Goal:** Predict whether a client will default next month.  
**Dataset:** UCI Credit Default (10,000 records, 24 features)  
**Model:** Logistic Regression & Gradient Boosting (AUC = 0.82)

**Workflow:**
1. **Sample:** stratified split 80/20  
2. **Explore:** descriptive stats, correlation heatmap  
3. **Modify:** feature engineering (payment delay, credit utilization)  
4. **Model:** compared models, selected GBM  
5. **Assess:** evaluated KS, gains chart, threshold optimization



---

## 🤖 AI Critic Review Loop

Each notebook includes a **Critic Review section** where GPT-5 (or Claude) acted as a domain expert:
- **CRISP-DM:** Dr. Alex Marin, CRISP-DM authority  
- **KDD:** Prof. Lin Tao, KDD process expert  
- **SEMMA:** Dr. Rivera, SAS SEMMA Fellow  

Each section documents:
- The **prompt used**  
- **Top 5 improvements** applied based on AI feedback  
- A **checklist of verified fixes**

This step demonstrates an iterative, AI-assisted refinement workflow — a required part of this assignment.

---

## 🧾 Medium Articles

Each subdirectory includes:
- `medium_article` → [Full project write-up for publication.](https://medium.com/@yashu.paladugu/applying-crisp-dm-kdd-and-semma-three-roads-to-real-world-data-science-1af5a9b3ec91)  



---

## 🧪 Reproducibility Instructions

1. Open the notebooks in **Google Colab**.  
2. Upload the corresponding dataset in `/data/`.  
3. Run all cells (runtime ~1–2 minutes each).  
4. Saved artifacts appear in `/reports/`, `/models/`, or `/figures/`.

To recreate the environment locally:
```bash
pip install -r requirements.txt


