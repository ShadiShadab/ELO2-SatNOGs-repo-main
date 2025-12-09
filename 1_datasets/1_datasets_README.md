# 1_datasets – Data Collection and Management

## 📊 Overview
This directory contains all the raw and processed data from the SatNOGS network used in our machine learning pipeline. The data spans **November 2022 to November 2025** and includes **198,058 satellite observations** after preprocessing.

---

## 📁 Directory Structure
```
1_datasets/
├── raw/          # Original database extracts and SQL dumps
├── processed/    # Cleaned, feature-engineered datasets
├── samples/      # Subsets for testing and development
├── metadata/     # Schema documentation and data dictionaries
└── README.md     # This file
```

---

## 📊 Key Dataset: Recent 3 Years (2022–2025)

- **Total Observations:** 198,058  
- **Time Period:** 2022-11-12 to 2025-11-10  
- **Success Rate:** 75.1%  
- **Unique Stations:** 1,072  
- **Unique Satellites:** 1,801  
- **Average Duration:** 7.8 minutes  
- **Average Altitude:** 49.0°  

### Observation Distribution
- Good Observations (status=100): 150,000 samples (75.1%)  
- Bad Observations (status=-100): 50,000 samples (24.9%)  
- Northern Hemisphere Stations: 183,856 observations  
- Southern Hemisphere Stations: 14,202 observations  
- Near Equator Stations (|lat| < 5): 5,511 observations  

---

## 📄 Main Data Files

| File | Format | Rows | Columns | Size |
|------|--------|------|---------|------|
| processed/recent_3years_clean.parquet | Parquet | 198,058 | 23 | ~153 MB |
| processed/recent_3years_features.parquet | Parquet | 198,058 | 44 | ~215 MB |
| processed/recent_3years_clean_sample.csv | CSV | 10,000 | 23 | - |
| processed/recent_3years_features_sample.csv | CSV | 10,000 | 44 | - |

---

## 🎯 Target Variable
**Binary Classification**  
- Success = 1 (observation_status = 100)  
- Failure = 0 (observation_status = -100)  

Original Status Codes:  
- 100: Good observation  
- -100: Bad observation  
- 0: Unknown status  
- -1000: Future observation (scheduled)  

---

## 🚀 Usage Instructions

### 1. Load Processed Data
```python
import pandas as pd

df = pd.read_parquet('1_datasets/processed/recent_3years_features.parquet')
print(f"Dataset shape: {df.shape}")
print(f"Success rate: {df['success'].mean():.1%}")
```

### 2. Load Sample Data (for testing)
```python
df_sample = pd.read_csv('1_datasets/processed/recent_3years_features_sample.csv')
```

### 3. Access Specific Features
```python
# Core observation features
obs_features = ['max_altitude', 'duration_minutes', 'rise_azimuth', 'set_azimuth']

# Station features
station_features = ['station_lat', 'station_lng', 'station_alt', 'station_horizon']

# Target variable
target = 'success'
```

---

## 🎯 Data Preparation Pipeline
**Steps Executed (in order):**
1. `02_recent_data_preparation.ipynb`: Data extraction and cleaning  
2. `03_feature_engineering.ipynb`: Feature creation and transformation  

**Output Validation:**  
- No missing essential data  
- Valid time ranges (end ≥ start)  
- Consistent data types  
- Proper encoding of categorical variables  
- Correct target variable mapping  

---

## 📊 Data Visualization Insights
- **Success Rate by Hemisphere:** ~75% both hemispheres  
- **Temporal Patterns:** Afternoon passes higher success; summer months slightly better  
- **Geographic Patterns:** High density in North America and Europe; higher altitudes → better success  

---

## ⚠️ Data Limitations
- Missing station metadata (1%)  
- Northern hemisphere stations dominate  
- Binary success labels may oversimplify quality  
- No weather, operator, or real-time RF data  

---

### ➡️ Next Step
Proceed to **`2_data_preparation/`** for detailed data cleaning and feature engineering processes.
