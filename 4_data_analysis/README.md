# 🛰️ Satellite Pass Prediction & Observation Success Rate
## Machine Learning Modeling – Phase 4

![MIT License](https://img.shields.io/badge/License-MIT-green.svg)
![Project Status](https://img.shields.io/badge/Status-Phase%204%20Complete-success)
![Last Updated](https://img.shields.io/badge/Last%20Updated-Dec%202024-blue)
![ML](https://img.shields.io/badge/Machine%20Learning-RandomForest%20%7C%20XGBoost-orange)

---

## 📌 Table of Contents
1. Overview  
2. Business Impact  
3. Project Structure  
4. Dataset Information  
5. Data Leakage Discovery  
6. Modeling Pipeline  
7. Model Performance  
8. Model Interpretation  
9. Business Rules  
10. Technical Insights  
11. Outputs  
12. Reproducibility  
13. License & Credits  

---

## 📋 Overview
This directory contains all machine learning modeling work for the **Satellite Pass Prediction & Observation Success Rate** capstone project under the **MIT Emerging Talent Program**.

The objective is to predict whether a satellite observation will succeed, enabling ground station operators to optimize scheduling and reduce wasted resources.

---

## 🎯 Business Impact Achieved
- **Success Rate**: 49.5% → **88.3%**
- **Failed Observations Reduced**: **76.8%**
- **Operational Efficiency**: Major reduction in wasted observation time

---

## 📁 Project Structure

```text
4_data_analysis/
├── 01_baseline_models.ipynb
├── 02_advanced_modeling.ipynb
├── 03_model_interpretation.ipynb
├── ml_results/
│   ├── baseline/
│   ├── advanced/
│   │   ├── randomforest_tuned_model.pkl
│   │   ├── final_test_metrics.json
│   │   └── final_summary_visualization.png
│   └── interpretation/
│       ├── model_interpretation_report.md
│       ├── executive_summary.md
│       └── permutation_importance_plot.png
```

---

## 📊 Dataset Information
- **Source**: SatNOGS Database  
- **Observations**: 578,010 (2021–2025)  
- **Features**: 39 → 17 clean features  
- **Target**: `target_success` (binary)

### Temporal Split Strategy
- Train: 70%  
- Validation: 15%  
- Test: 15%  
- Leakage prevention via year-based splitting

---

## 🚨 Critical Discovery: Data Leakage

```mermaid
flowchart LR
A[Raw Features] --> B[Status Included ❌]
B --> C[100% Accuracy]
A --> D[Status Removed ✅]
D --> E[Realistic Performance]
```

### Fix Applied
- Removed `status`
- Removed `waterfall_status`
- Accuracy corrected to realistic values

---

## 🤖 Modeling Pipeline

```mermaid
flowchart TD
A[Clean Dataset] --> B[Baseline Models]
B --> C[Feature Engineering]
C --> D[Advanced Models]
D --> E[Model Interpretation]
E --> F[Business Rules]
```

---

## 📈 Model Performance (Test Set)

| Model | Accuracy | F1 | ROC-AUC |
|------|---------|----|--------|
| Logistic Regression | 56.9% | 58.1% | 59.8% |
| Decision Tree | 69.6% | 68.3% | 77.4% |
| Random Forest | 82.7% | 82.6% | 90.8% |
| XGBoost | 85.0% | 85.2% | 92.4% |
| **Random Forest (Tuned)** | **88.3%** | **88.4%** | **94.6%** |

🏆 **Final Selected Model**: Tuned Random Forest

---

## 🔍 Model Interpretation Highlights
### Top Predictive Features
- archived – 19.0%
- year – 18.3%
- station_lat
- station_alt
- station_lng

### Key Insights
- Archived observations are **19.4%** more successful
- Optimal latitude: **40.2° – 52.7°**
- Performance improves in recent years

---

## 🎯 Actionable Business Rules

```python
# Priority scheduling
if archived == 1 and year >= 2023:
    priority = "HIGH"

# Station selection
if 40.2 <= station_lat <= 52.7 and station_alt > 30:
    select_station = True

# Confidence threshold
if prediction_probability > 0.90:
    proceed = True
```

---

## 📦 Outputs Generated
- Tuned Random Forest model (`.pkl`)
- Full test metrics (`final_test_metrics.json`)
- Executive summary for stakeholders
- Feature importance & error analysis plots

---

## 🔄 Reproducibility
1. Load processed dataset  
2. Run notebooks sequentially:
   - `01_baseline_models.ipynb`
   - `02_advanced_modeling.ipynb`
   - `03_model_interpretation.ipynb`
3. Review outputs in `ml_results/`

---

## 📄 License & Credits
- **Code**: MIT License  
- **Reports & Visuals**: CC BY 4.0  
- **Data**: SatNOGS Open Database License  

**Author**: [Your Name]  
**Program**: MIT Emerging Talent – Computer & Data Science
