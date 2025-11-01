# AutoGluon Colabs — IEEE Fraud, California Housing, Tabular Classification, Multi‑Label
Demo video link: https://drive.google.com/file/d/1RMlGWjMu8vGFIMTVcDY2tNYKOecMqtrJ/view?usp=sharing

This repo contains **four Google Colab notebooks** demonstrating AutoGluon on classic tabular problems. Each notebook is designed to run on **CPU** (no GPU required) and **saves artifacts** for grading.

## Repo layout

```
autogluon-colabs/

│  ├─ 01_ieee_fraud_autogluon.ipynb
│  ├─ 02_california_housing.ipynb
│  ├─ 03_tabular_classification.ipynb
│  └─ 04_multilabel_tabular.ipynb         
└─ README.md
```

---

## Quick start (run once per fresh Colab runtime)

Paste this **setup cell** at the top of any notebook and run it before other cells:

```python
# === SETUP (run once per fresh runtime) ===
!pip -q uninstall -y scikit-learn scikit-learn-intelex umap-learn >/dev/null
!pip -q install -U pip setuptools wheel >/dev/null
!pip -q install -U "scikit-learn==1.6.1" "autogluon==1.4.0" kaggle >/dev/null

# (Optional) show versions
import sys, autogluon, sklearn
print("Python:", sys.version)
print("AutoGluon:", autogluon.__version__)
print("scikit-learn:", sklearn.__version__)
```

If the runtime restarts, re-run the setup cell.

---

## 01) IEEE‑CIS Fraud Detection (classification)

**Goal:** Train an AutoGluon baseline and create a `submission_like.csv` (Kaggle-style).  
**Note:** The original competition is **ended**, so use **synthetic or mirrored CSVs** instead of Kaggle *competitions* API.

**Expected input files (place under `data/ieee/`):**
- `train_transaction.csv`
- `train_identity.csv`
- `test_transaction.csv`
- `test_identity.csv`

**Notebook flow:**
1. Merge `*_transaction` and `*_identity` on `TransactionID` → train/test tables.  
2. Train `TabularPredictor(label="isFraud", problem_type="binary", eval_metric="roc_auc")` with a small `time_limit`.  
3. Show `leaderboard()`.  
4. Predict probabilities on test and save **`submission_like.csv`** with columns `TransactionID,isFraud`.

**Artifacts saved:** `submission_like.csv`

---

## 02) California Housing (regression)

**Goal:** Predict `median_house_value` using AutoGluon.

**Dataset options:**
- Kaggle dataset `camnugent/california-housing-prices` (requires `kaggle.json`), or  
- Fallback: scikit‑learn’s built‑in California Housing (no Kaggle required).

**Notebook flow:**
1. Load data, `dropna()`, and `train_test_split`.  
2. Train `TabularPredictor(label="median_house_value", problem_type="regression", eval_metric="root_mean_squared_error")`.  
3. Print RMSE and show `leaderboard()`.  
4. Save predictions and feature importances.

**Artifacts saved:**  
- `california_housing_predictions.csv`  
- `feature_importance.csv`

---

## 03) Tabular Classification (quick demo)

**Goal:** Minimal end‑to‑end classification on the Adult Income dataset.

**Notebook flow:**
1. Load train/test CSVs from URL.  
2. Train `TabularPredictor(label="class")` with a short `time_limit`.  
3. Evaluate and show `leaderboard()`.

**Artifacts (optional):** `adult_income_predictions.csv`

---

## 04) Multi‑Label Tabular (CPU‑light)

**Goal:** Demonstrate **multi‑label** learning (multiple binary labels simultaneously).

**Dataset:** Small **synthetic** table mixing numeric, categorical, and text features.  
**Labels example:** `["is_playful","is_senior","needs_experience"]`.

**Two ways to train:**
- **Native**: `TabularPredictor(label=[...], problem_type="multilabel", eval_metric="f1_micro")`.  
- **Fallback wrapper**: Minimal `MultilabelPredictor` (one predictor per label; optionally model label correlations).

**Artifacts saved:** `multilabel_predictions.csv`

---

## Kaggle token (only for Kaggle downloads)

1. In Kaggle: **Account → API → Create New API Token** → downloads `kaggle.json`.  
2. In Colab: upload the file and ensure it is saved to `~/.kaggle/kaggle.json` (chmod 600).  
3. Alternative (env vars in a cell):
   ```python
   import os, json, pathlib
   kag = pathlib.Path.home()/".kaggle"; kag.mkdir(exist_ok=True)
   with open(kag/"kaggle.json","w") as f:
       f.write(json.dumps({"username":"<USER>","key":"<KEY>"}))
   os.chmod(kag/"kaggle.json", 0o600)
   ```

> For **IEEE**, do **not** use Kaggle *competitions* API (ended). Use the synthetic/mirror CSVs method.

---

## How to save executed outputs to GitHub

In Colab after **Runtime → Run all** finishes:  
**File → Save a copy in GitHub** → pick your repo and path.  
This commits the notebook **with cell outputs** so graders can verify results.

---

## Deliverables checklist (per notebook)

- [ ] Runs end‑to‑end on a fresh runtime  
- [ ] Dataset path printed and data loaded  
- [ ] `fit()` shows training summary (`time_limit`, `presets` stated)  
- [ ] `leaderboard()` displayed  
- [ ] Metric reported (AUC / RMSE / Accuracy / F1)  
- [ ] Artifacts saved (CSV outputs)  
- [ ] Notebook pushed to GitHub **with outputs**

---

## Troubleshooting

- **scikit‑learn import errors** (e.g., `_get_additional_lbfgs_options_dict`, `_add_to_diagonal`)  
  Use the pinned setup above: `autogluon==1.4.0`, `scikit-learn==1.6.1`, then re‑run.

- **Kaggle permission/403**  
  For active comps: Join + Accept rules in browser. For IEEE (ended): use synthetic/mirror CSVs.

- **Colab memory/time**  
  Reduce `time_limit`, switch to `presets="medium_quality_faster_train"`, or sample rows for faster runs.

Author : Venkata Yashwanth Paladugu