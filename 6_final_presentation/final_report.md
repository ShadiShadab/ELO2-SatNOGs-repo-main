
# Satellite Pass Prediction & Observation Success Rate
## Final Report – MIT Emerging Talent Program Capstone Project

**Author:** Shadi Shadabshoar  
**Program:** MIT Emerging Talent Program in Computer and Data Science  
**Date:** December 2025  
**Project Duration:** October – December 2025  

---

## Executive Summary

### Project Overview
This project developed a machine learning system to predict satellite observation success for the SatNOGS (Satellite Networked Open Ground Station) network. By analyzing 578,000 historical observations, we built a predictive model that increases observation success rates from **49.5% to 88.3%**, representing a **38.8 percentage point improvement** and a **76.8% reduction in failed observations**.

### Key Achievements
- **Model Performance:** 94.6% ROC-AUC, 88.3% accuracy on the test set  
- **Business Impact:** Success rate improved from 49.5% to 88.3%  
- **Operational Efficiency:** Failed observations reduced by 76.8%  
- **Actionable Insights:** Four implementable business rules for operators  
- **Deliverables:** Trained model, interactive dashboard, Medium article, full documentation  

### Value Proposition
For the SatNOGS community of 600+ volunteer ground station operators, this project delivers:
- Nearly doubled successful observations with the same resources  
- Reduced equipment wear and energy consumption  
- Increased scientific data yield per observation hour  
- Data-driven scheduling replacing random allocation  

---

## 1. Introduction

### 1.1 Problem Statement
SatNOGS is the world’s largest open satellite tracking network, yet its random scheduling approach results in only **49.5% successful observations**. This inefficiency leads to wasted equipment time, lost scientific data, and suboptimal use of volunteer-operated infrastructure.

### 1.2 Project Objectives
1. Predict satellite observation success using machine learning  
2. Identify the most influential success factors  
3. Translate insights into actionable business rules  
4. Build an interactive visualization and prediction dashboard  
5. Provide complete, open documentation for community adoption  

### 1.3 Scope
- **Data:** 578,000 observations (2021–2025)  
- **Features:** 24 engineered features (temporal, geometric, geographic, operational)  
- **Task:** Binary classification (success vs failure)  
- **Validation:** Temporal splits to avoid data leakage  
- **Tools:** Python, scikit-learn, Streamlit, Plotly  

---

## 2. Technical Methodology

### 2.1 Data Collection & Preparation

#### 2.1.1 Data Sources
- **Primary Source:** SatNOGS MariaDB database (12.5M+ raw observations)  
- **Time Period:** 2021–2025  
- **Final Sample:** 578,010 cleaned observations  

#### 2.1.2 Data Cleaning Pipeline
- Removed invalid observation durations (<60s or >3600s)  
- Filtered ambiguous status codes  
- Handled missing values via removal or imputation  
- Created binary success target  
- Extracted temporal features from timestamps  

**Critical Discovery – Data Leakage:**  
Initial models achieved 100% accuracy due to leakage from the `status` column. Removing it established a realistic baseline of **56.9% accuracy**.

---

### 2.2 Feature Engineering

Final feature count: **24**, spanning temporal, geometric, geographic, operational, and derived categories.

---

### 2.3 Model Development

The tuned **Random Forest** model achieved the best balance of performance and interpretability with **94.6% ROC-AUC** and **88.3% accuracy**.

---

## 3. Results & Insights

- **Accuracy:** 88.3%  
- **ROC-AUC:** 94.6%  
- **Failed observations reduced:** 76.8%  

For every 100 observations:
- Random scheduling → ~50 successes  
- ML-optimized scheduling → ~88 successes  

---

## 4. Actionable Business Rules

1. Prioritize archived and recent observations  
2. Select stations within optimal latitude and altitude ranges  
3. Apply confidence thresholds before execution  
4. Schedule primarily during daytime windows  

---

## 5. Limitations & Future Work

- Weather data integration  
- Model compression for edge deployment  
- Real-time API and active learning  

---

## 6. Conclusion
This project demonstrates that machine learning can nearly double successful satellite observations by replacing random scheduling with predictive intelligence, delivering measurable operational and scientific value to the SatNOGS community.

---

**GitHub Repository:** https://github.com/ShadiShadab/ELO2-SatNOGs-repo-main  

*Official capstone submission for the MIT Emerging Talent Program in Computer and Data Science.*
