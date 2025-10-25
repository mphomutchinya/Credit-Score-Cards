# 🏦 Credit Risk Profiling using K-Means Clustering

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.x-orange.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Status](https://img.shields.io/badge/status-Active-success.svg)

---

## 📘 Overview
This project applies **unsupervised machine learning (K-Means clustering)** to segment credit applicants into meaningful financial profiles based on behavioral and financial ratios.  
The model identifies distinct groups such as **Low Risk**, **Medium Risk**, and **High Risk**, which can be used for **credit risk assessment**, **customer profiling**, and **loan decision support**.

---

## 🎯 Objectives
- Cluster customers by their **financial ratios** and **credit characteristics**.  
- Label clusters into interpretable **risk categories**.  
- Provide insights that support **credit policy** and **risk management**.

---

## 🧠 Methodology

### 1️⃣ Data Preparation
Input features used for clustering:
- `debt_to_income_ratio`
- `credit_score`
- `savings_to_income_ratio`

Data was scaled and cleaned prior to clustering using `StandardScaler`.

### 2️⃣ K-Means Clustering
- **Algorithm:** K-Means  
- **k (clusters):** determined using *Elbow Method* and *Silhouette Score*.  
- Each customer receives a `cluster` label representing their risk group.

### 3️⃣ Risk Categorization
Clusters were mapped to qualitative risk categories via a custom dictionary (`risk_mapping`):

| Cluster | Risk Category |
|----------|----------------|
| 0 | Low Risk |
| 1 | Medium Risk |
| 2 | High Risk |

This mapping was applied across:
- `dev_profiles`
- `val_profiles`
- `hold_profiles`

Each record includes:
- `cluster` – numerical label from K-Means  
- `risk_category` – qualitative risk level  
- `risk_score` – standardized numeric indicator

### 🧾 Sample Output
```text
| debt_to_income_ratio | credit_score | savings_to_income_ratio | cluster | risk_category | risk_score |
|----------------------:|--------------:|-------------------------:|---------:|---------------|------------:|
| 1.00 | 693 | 5.23 | 1 | Medium Risk | -1.326 |
| 0.00 | 424 | 0.81 | 0 | Low Risk | -0.579 |
| 20.42 | 769 | 7.97 | 2 | High Risk | -1.452 |


Silhouette Score – to measure separation between clusters

Risk profiles were visually inspected through 2D/3D scatter plots.

🧩 Files Description
File	Description
credit_risk_model.ipynb	Main notebook containing the model pipeline
val_profiles, hold_profiles, dev_profiles	DataFrames with final risk segmentation
risk_mapping	Dictionary used to assign qualitative risk categories
