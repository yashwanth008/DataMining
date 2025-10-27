# DataMining
All my assignments will be here

Assignment - 1: Medium article Link: https://medium.com/@yashu.paladugu/predicting-survival-on-the-titanic-with-machine-learning-4280c982747c

Assignment - 2:
01) IEEE-CIS Fraud Detection (classification)
Goal: train an AutoGluon baseline and produce a submission_like.csv.
Note: The original Kaggle competition is ended, so the Kaggle competitions API may be blocked. Use one of the two options below.
Input data options
A. Synthetic (recommended for grading without Kaggle):
Place these 4 CSVs under data/ieee/:
train_transaction.csv
train_identity.csv
test_transaction.csv
test_identity.csv
If you don’t have them yet, you can generate synthetic IEEE-style CSVs locally or via a helper cell (we provided a generator during setup; otherwise ask your grader for the synthetic bundle).
B. Community mirror (if available):
Use a Kaggle datasets mirror (not competitions). After placing CSVs under data/ieee/, proceed the same way.
What to run (inside the notebook)
Merge *_transaction.csv with *_identity.csv on TransactionID
Train:
TabularPredictor(label="isFraud", problem_type="binary", eval_metric="roc_auc")
Use a modest time_limit 
Output:
leaderboard() printed
Artifacts saved: ieee_Fraud_Det.csv

02) California Housing (regression)
Goal: predict median_house_value with AutoGluon.
Dataset options:
Kaggle dataset: camnugent/california-housing-prices (requires kaggle.json)
Automatic fallback: scikit-learn’s built-in California Housing (no Kaggle needed)
What to run:
Load data, drop NAs, train_test_split
Train:
TabularPredictor(label="median_house_value", problem_type="regression", eval_metric="root_mean_squared_error")
presets="medium_quality" and a short time_limit (e.g., 10–15 min)
Evaluate: print RMSE; show leaderboard()
Artifacts saved:
california_housing_predictions.csv (true vs predicted)

03) Tabular Classification (quick demo)
Goal: minimal end-to-end classification on a public dataset.
Dataset: Adult Income (downloaded directly via URL).
What to run:
TabularPredictor(label="class").fit(train, time_limit=180)
predictor.evaluate(test) and predictor.leaderboard(test)
Artifacts (optional):
You can save predictions to adult_income_predictions.csv if desired.

04) Multi-Label Tabular (CPU-light)
Goal: demonstrate multi-label learning (multiple binary labels at once) with AutoGluon.
Dataset: small synthetic dataset combining numeric + categorical + text features.
Labels: e.g., ["is_playful", "is_senior", "needs_experience"].
What to run:
Build small synthetic data (provided in the notebook).
Train a multilabel model:
Option A (native): TabularPredictor(label=[...], problem_type="multilabel", eval_metric="f1_micro").fit(...)
Option B (fallback wrapper): a minimal MultilabelPredictor that trains one binary head per label and optionally feeds earlier predictions as features (useful if your environment is finicky).
Evaluate: print micro-F1 and/or per-label F1; preview predictions.
Artifacts saved:
multilabel_predictions.csv