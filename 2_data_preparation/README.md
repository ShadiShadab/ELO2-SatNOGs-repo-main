# 2_data_preparation – Data Processing and Feature Engineering Pipeline

## 🔧 Overview

This directory contains the complete data preparation pipeline that transforms raw SatNOGS database records into a machine learning-ready dataset. The pipeline processes **198,058 observations** and creates **44 features** for predictive modeling.

---

## 📁 Directory Contents

```
2_data_preparation/
├── 02_recent_data_preparation.ipynb      # Data extraction & cleaning
├── 03_feature_engineering.ipynb          # Feature creation & transformation
├── database_queries/                     # SQL queries for data extraction
│   └── extraction_queries.sql
├── config/                               # Configuration files
│   └── database_config.py
└── README.md                             # This file
```

---

## 🚀 Pipeline Overview

### Step 1: Data Extraction (02_recent_data_preparation.ipynb)

* **Objective:** Extract and clean 3 years of recent observation data (2022-2025)
* **Key Processes:**

  * Connect to SatNOGS MariaDB database
  * Identify latest 3 years of data
  * Stratified sampling: 150K good / 50K bad observations
  * Table joins: Combine observation, station, and satellite data
  * Handle missing values and validate data
* **Output:**

  * `recent_3years_clean.parquet`: 198,058 rows × 23 columns
  * `recent_3years_clean_sample.csv`: 10,000 row sample

### Step 2: Feature Engineering (03_feature_engineering.ipynb)

* **Objective:** Create predictive features from raw observation data
* **Feature Categories Created:**

  * Temporal Features (8)
  * Geometric Features (6)
  * Station/Satellite Features (5)
  * Derived/Interaction Features (3)
* **Output:**

  * `recent_3years_features.parquet`: 198,058 rows × 44 columns
  * `recent_3years_features_sample.csv`: 10,000 row sample
  * `feature_list.txt`: Complete feature documentation

---

## 🛠️ Usage Instructions

### Run Complete Pipeline

```bash
jupyter notebook 02_recent_data_preparation.ipynb
jupyter notebook 03_feature_engineering.ipynb
```

### Load Processed Dataset

```python
import pandas as pd

df = pd.read_parquet('../1_datasets/processed/recent_3years_features.parquet')

# Separate features and target for ML modeling
X = df.drop(columns=['observation_id', 'start', 'end', 'ground_station_id',
                     'sat_id', 'station_name', 'qthlocator', 'satellite_name',
                     'satellite_description', 'success'])
y = df['success']

print(f"Features shape: {X.shape}")
print(f"Target shape: {y.shape}")
print(f"Success rate: {y.mean():.1%}")
```

### Quick Data Inspection

```python
categorical = X.select_dtypes(include=['object', 'category']).columns.tolist()
numerical = X.select_dtypes(include=['int64', 'float64']).columns.tolist()
print(f"Categorical features: {len(categorical)}")
print(f"Numerical features: {len(numerical)}")
```

---

## 📈 Pipeline Metrics

* **Processing Time:** ~21 minutes total (19 min extraction + 2 min feature engineering)
* **Memory Usage:** ~500 MB peak
* **Observations Processed:** 198,058
* **Features Created:** 44
* **Target Variable:** `success` (75.1% positive)

---

## 🎯 Next Steps

Proceed to **`3_data_exploration/`** for exploratory data analysis and visualization of these features.

