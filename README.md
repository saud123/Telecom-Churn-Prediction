# 📊 Telecom Customer Churn Prediction

End-to-end ML pipeline predicting telecom churn on 7,043 customers, with model selection driven by **business ROI** rather than accuracy alone.

![Python](https://img.shields.io/badge/Python-3.10-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.2+-orange)
![XGBoost](https://img.shields.io/badge/XGBoost-1.7+-green)

---

## 🎯 Overview

Built Random Forest and XGBoost classifiers to identify at-risk customers and quantify retention savings. Chose **baseline XGBoost** over the tuned variant because it preserved 73% recall vs. 22% — a decision driven by the asymmetric cost of missing a churner.

> Missing a churner costs ~$1,680 (LTV). A false alarm costs ~$50 (marketing). **Recall > Precision.**

---

## 🏆 Results

| Model | Accuracy | Precision | Recall | F1 | AUC |
|-------|:--------:|:---------:|:------:|:--:|:---:|
| RF Baseline | 76.3% | 53.9% | **73.3%** | 0.621 | 0.839 |
| RF Tuned | 79.5% | 68.9% | 41.4% | 0.518 | 0.847 |
| **XGB Baseline** ⭐ | 75.0% | 52.1% | **73.0%** | **0.608** | 0.830 |
| XGB Tuned | 77.5% | 75.7% | 22.5% | 0.346 | 0.845 |

**Validation:** 5-fold CV AUC **0.844 ± 0.008** | Bootstrap 95% CI **[0.826, 0.867]** | No leakage detected

---

## 💰 Business Impact

**Current state:** 26.5% churn rate → **$3.14M annual revenue lost**

| Strategy | Churn ↓ | Customers Saved | Net Savings | ROI |
|----------|:-------:|:---------------:|:-----------:|:---:|
| Top 3 Drivers | 25% | 102 | $121,898 | 244% |
| **Top 5 Drivers** ⭐ | 35% | 143 | $190,657 | **381%** |
| Top 10 Drivers | 45% | 184 | $259,416 | 519% |

### Top 3 Churn Drivers
1. **Contract** (28.3%) — Month-to-month churns 3× more
2. **Tenure** (20.5%) — First 6–12 months are critical
3. **MonthlyCharges** (13.2%) — High price sensitivity above $90

**High-risk profile:** Month-to-month × tenure <12mo × charges >$90

---

## 🔬 Methodology
