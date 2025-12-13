# 3_data_exploration/ — Exploratory Data Analysis (EDA)

![License](https://img.shields.io/badge/License-MIT-blue.svg)
![Status](https://img.shields.io/badge/EDA-Complete-brightgreen)
![Last Updated](https://img.shields.io/badge/Last%20Updated-2024--12--12-lightgrey)

## 📋 Overview
This directory contains notebooks for exploratory data analysis of satellite observation success patterns. The EDA phase identifies patterns, relationships, and insights that inform feature engineering and modeling decisions.

## 🎯 Objectives Achieved
1. **Data Understanding**
2. **Pattern Discovery**
3. **Insight Generation**
4. **Visual Communication**
5. **Hypothesis Testing**

## 📁 File Structure
```
3_data_exploration/
├── 01_initial_eda.ipynb
├── 02_geographic_analysis.ipynb
├── plots/
│   ├── 01_target_distribution.png
│   ├── 02_temporal_patterns.png
│   ├── 03_geometric_patterns.png
│   ├── 04_correlation_heatmap.png
│   └── ...
├── geo_plots/
│   ├── 01_geographic_distribution.png
│   ├── 02_altitude_analysis.png
│   ├── 03_horizon_analysis.png
│   ├── 04_regional_analysis.png
│   └── 05_geographic_correlations.png
├── initial_eda_report.md
├── geographic_analysis_report.md
└── README.md
```

## 📊 Workflow Diagram (ASCII)
```
Sample Dataset (50,000 rows)
          |
          v
+------------------------+
|  Temporal Exploration  |
+------------------------+
          |
          v
+------------------------+
|  Geometric Analysis    |
+------------------------+
          |
          v
+------------------------+
| Geographic Exploration |
+------------------------+
          |
          v
+------------------------+
|     Insight Reports    |
+------------------------+
```

## 🚀 Key Notebooks

### `01_initial_eda.ipynb`
- Temporal & geometric patterns
- Correlation analysis

### `02_geographic_analysis.ipynb`
- Hemisphere, region, and station-based patterns
- Geographic clustering

## 📊 Key Findings Summary
- **Success Rate**: 49.33%
- **Best Hour**: 22:00
- **Best Season**: Fall
- **Altitude Effect**: Strong monotonic increase
- **Geographic Extremes**: KP03 = 74.7% success; KM18 = 9.7%

## 📈 Visualizations
Located in `plots/` and `geo_plots/`.

## 🔍 Methodological Approach
- Random 50K sample
- Descriptive statistics
- Correlation analysis
- Visualization-driven insights

## 🎯 Implications for ML Modeling
- Cyclic encodings for temporal features
- Altitude & geographic features highly predictive
- Interaction terms recommended

## 📋 Reports Generated
- `initial_eda_report.md`
- `geographic_analysis_report.md`

## 🛠️ Technical Tools
- pandas, numpy
- matplotlib, seaborn
- scipy
- Jupyter Notebook

## 🚨 Limitations
- Northern-hemisphere biased sample
- 50K sample (full dataset available)
- Basic success definition

## 🔄 Reproducibility
Run both notebooks sequentially with the sample dataset.

## 👥 Contributors
Primary Analyst: Your Name  
MIT Emerging Talent Program

## 📄 License
MIT License (Code)  
CC BY 4.0 (Visualizations & Reports)

---

*Last Updated: 2024-12-12*  
*Version: 1.0*  
*EDA Phase: Complete*
