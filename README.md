# 🛰️ Satellite Pass Prediction & Observation Success Rate

## MIT Emerging Talent Program – Capstone Project

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
![Status](https://img.shields.io/badge/Project%20Status-Complete%20✅-brightgreen)
![Last Updated](https://img.shields.io/badge/Last%20Updated-December%202025-blue)

---

## 🎯 Project Overview

**Increasing satellite observation success rates from 49.5% to 88.3% using Machine Learning**

This repository contains the complete MIT Emerging Talent Program capstone project focused on improving satellite observation success for the **SatNOGS (Satellite Networked Open Ground Station)** network. Using 578,000 historical observations, a machine learning system was developed to predict observation success probabilities and support data-driven scheduling decisions.

### 📊 Key Results
- **Success Rate Improvement:** 49.5% → 88.3% (+38.8 pp)
- **Failed Observations Reduced:** 76.8%
- **Best Model:** Tuned Random Forest
- **Model Performance:** 94.6% ROC-AUC
- **Impact:** Nearly double successful observations with the same infrastructure

---

## 📁 Repository Structure

```text
satellite-pass-prediction/
├── 0_domain_study/              # Background research and literature
├── 1_datasets/                  # Raw and processed SatNOGS data
├── 2_data_preparation/          # Cleaning and feature engineering
├── 3_data_exploration/          # EDA notebooks and visual analysis
├── 4_data_analysis/             # ML modeling and interpretation
│   └── ml_results/              # Trained models, metrics, plots
├── 5_communication_strategy/
│   ├── dashboard/               # Streamlit interactive dashboard
│   ├── medium_blog_post.md      # Public technical article
│   └── stakeholder_materials/
├── 6_final_presentation/        # Final report and presentation slides
├── requirements.txt             # Python dependencies
└── README.md                    # Main documentation (this file)
```
## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- Git
- (Optional) MariaDB / MySQL (for access to original data)

### Installation
```bash
git clone https://github.com/ShadiShadab/ELO2-SatNOGs-repo-main.git
cd ELO2-SatNOGs-repo-main
pip install -r requirements.txt
```

### Run the Interactive Dashboard
```bash
cd 5_communication_strategy/dashboard/dashboard_prototype
streamlit run app.py
```
Open: http://localhost:8501

---

## 🔬 Technical Journey

### Phase 1 — Domain Study & Data Collection
- Studied SatNOGS architecture and satellite communication fundamentals  
- Collected 12.5M+ raw observations from the SatNOGS database  
- Final cleaned dataset: 578,010 observations (2021–2025)

### Phase 2 — Data Preparation & Exploration
- Removed invalid durations and handled missing values  
- Engineered 24 features (temporal, geographic, geometric)  
- Baseline success rate identified: 49.5%  
- Optimal latitude band discovered: 40.2°–52.7°

### Phase 3 — Machine Learning Modeling
- Resolved a critical data-leakage issue  
- Evaluated models: Logistic Regression, Decision Tree, Random Forest, XGBoost, LightGBM  
- Best model: Tuned Random Forest — 94.6% ROC-AUC

### Phase 4 — Interpretation & Business Rules
- Top predictive factors:
  - Archived status (+19.4% success)
  - Observation year
  - Station latitude & altitude
- Four actionable rules for operators:
  1. Priority scheduling for archived & recent observations  
  2. Optimal station selection by geography  
  3. Confidence-based decision thresholds  
  4. Daytime scheduling optimization

---

## 📊 Interactive Dashboard
The Streamlit dashboard provides:
- Model performance overview  
- Feature importance & interpretation  
- Business rule explorer  
- Live success-probability predictor  
- Sample prediction inspection

---

## 📈 Business Impact
- Success Rate improved: 49.5% → 88.3%  
- Failed Observations reduced: −76.8%  
- Operational Gain: ~88 successes per 100 observations (vs ~50 baseline)  
- Community Value: reduced waste, increased science output, improved scheduling

---

## 🛠️ Technical Stack
- Languages: Python  
- ML: scikit-learn, XGBoost, LightGBM  
- Data: pandas, NumPy  
- Visualization: Plotly, Matplotlib  
- Deployment: Streamlit  
- Version Control: Git & GitHub

---

## 🤝 Contributing
Contributions welcome:
- API integration with SatNOGS  
- Additional features or models  
- Dashboard improvements  
- Documentation enhancements

Workflow:
1. Fork the repository  
2. Create a feature branch  
3. Commit changes (include tests where appropriate)  
4. Open a pull request

---

## 📄 License
- Code: MIT License  
- Data: SatNOGS Open Database License (ODbL) CC BY SA
- Documentation: CC BY SA

---

## 📬 Contact & Resources
- Author: [Shadi Shadabshoar](https://www.linkedin.com/in/shadi-shadabshoar/)  
- MIT Emerging Talent Program – Computer & Data Science  
- Project Repo: https://github.com/ShadiShadab/ELO2-SatNOGs-repo-main  
- SatNOGS: https://network.satnogs.org/

“Machine learning isn’t just about accuracy; it’s about measurable real-world impact.”
  
*Developed as part of the Emerging Talent Program in Computer and Data Science at MIT University.*
*December 2025*



