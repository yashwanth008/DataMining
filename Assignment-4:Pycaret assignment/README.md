#  PyCaret & Lightweight AutoML — All-in-One Colab

Demo video Link: https://drive.google.com/file/d/1Znw7vOB0PU2dmqksxdYNp-zljWpSjdhl/view?usp=sharing 

This single Google Colab notebook demonstrates **end-to-end machine learning workflows** using both **PyCaret** and lightweight libraries like **FLAML**, **XGBoost**, **LightGBM**, **pmdarima**, and **mlxtend** — covering all major data mining tasks in one place.

---

##  Overview
The notebook integrates multiple tasks:
- Classification (Binary + Multiclass)
- Regression
- Clustering
- Anomaly Detection
- Association Rule Mining
- Time Series Forecasting (with and without exogenous variables)


Each section is fully executable in Colab with **GPU acceleration** and uses **open-source datasets** or **synthetic fallbacks** to ensure reproducibility.

---

## How to Run
1. Open the notebook in **Google Colab**.  
2. Go to **Runtime → Change runtime type → GPU** (recommended).  
3. Run all cells top-to-bottom.  
4. Observe printed metrics, plots, and Gradio demos at the end.  
5. Save your notebook **with outputs** before submission or pushing to GitHub.

---

## Sections in the Notebook
| Section | Task | Libraries Used | Dataset |
|----------|------|----------------|----------|
| A1 | Binary Classification | FLAML, XGBoost | Telco Customer Churn |
| A2 | Multiclass Classification | FLAML | Dry Bean Dataset |
| A3 | Regression | FLAML | Bike Sharing (day.csv) |
| B | Clustering | scikit-learn (KMeans) | Mall Customers |
| C | Anomaly Detection | Isolation Forest | Shuttle / Synthetic |
| D | Association Rules | mlxtend Apriori | Online Retail / Synthetic |
| E1 | Time Series Forecast | pmdarima ARIMA | Airline Passengers |
| E2 | Time Series + Exogenous Vars | pmdarima ARIMA | Synthetic Retail |
| F | Gradio Demos | gradio | Churn Predictor & Forecast App |

---

## Video Demonstration
Each task has a **short walkthrough (≈1 minute)** explaining:
- Dataset used  
- Model setup and AutoML process  
- Evaluation metrics and insights  
- Model saving or deployment (for Gradio demos)

The final video shows all tasks executed sequentially in a single Colab runtime.

---

## Key Features
- One unified Colab notebook — no switching needed  
- Fully reproducible and GPU-accelerated  
- Handles dataset unavailability with automatic synthetic generation  
- Clean outputs and concise explanations for each stage  
- Includes two **Gradio apps** for interactive predictions  

---

## Metadata
**Author:** Venkata Yashwanth Paladugu 
**Course:** Data Mining / Machine Learning  
**Date:** October 2025  
**Environment:** Google Colab (Tesla T4 GPU, Python 3.12)  
**Submission Type:** Single consolidated notebook with all modules + video demo

---
