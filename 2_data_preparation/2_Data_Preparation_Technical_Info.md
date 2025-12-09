# 2_data_preparation – Technical Documentation

## 🔧 Data Processing and Feature Engineering Pipeline

### 1. Database Connection Setup

```python
def get_engine():
    """Create SQLAlchemy engine for MariaDB connection"""
    DB_USER = "root"
    DB_PASSWORD = "123456789"
    DB_HOST = "127.0.0.1"
    DB_PORT = "3306"
    DB_NAME = "newdata"
    
    conn_str = f"mysql+pymysql://{DB_USER}:{DB_PASSWORD}@{DB_HOST}:{DB_PORT}/{DB_NAME}?charset=utf8mb4"
    return create_engine(conn_str, pool_recycle=3600)
```

### 2. Data Extraction Strategy

* **Date Range:** 2022-11-12 to 2025-11-12 (3 years)
* **Stratified Sampling:** 150,000 good / 50,000 bad observations
* **SQL Joins:** Combine `base_observation`, `base_station`, `base_satelliteidentifier`, `base_satellite`, `base_satelliteentry`

### 3. Data Cleaning

* Removed rows with missing essential data: `station_lat`, `station_lng`, `start`, `end` (1,942 rows)
* Converted datetime columns and calculated `duration_minutes`
* Created binary target `success` mapping: 100 → 1, -100 → 0

### 4. Feature Engineering

#### Temporal Features (8)

* `hour`, `day_of_week`, `month`, `year`
* `time_of_day` (Night/Morning/Afternoon/Evening)
* `season` (Winter/Spring/Summer/Autumn)
* `is_weekend` (0/1)
* `is_night` (0/1)

#### Geometric Features (6)

* `azimuth_range` (shortest angular distance)
* `pass_direction` (East_to_West / West_to_East)
* `elevation_category` (Low/Medium/High)
* `zenith_distance` (90 - max_altitude)
* `pass_completeness` (0-1 normalized)
* `max_altitude`

#### Station & Satellite Features (5)

* `station_hemisphere` (Northern/Southern/Equator)
* `station_alt_category` (Below_Sea / Low / Medium / High / Very_High)
* `satellite_alive` (0/1)
* `station_lat_abs`, `station_lng_abs`

#### Derived Features (3)

* `pass_quality_score` (heuristic combining altitude, duration, completeness)
* `winter_night_factor` (interaction latitude × season)
* `altitude_duration_product` (max_altitude × duration_minutes)

### 5. Missing Value Imputation

* Categorical: filled with mode
* Numerical: filled with median

### 6. Feature Analysis

* **Categorical Features:** 12
* **Numerical Features:** 20
* **Top correlations with success:**

  * `norad_cat_id` (-0.128), `station_horizon` (-0.083), `set_azimuth` (0.082), `max_altitude` (0.077), `zenith_distance` (-0.077)
* **Data Leakage Removal:** Dropped `observation_status` and `waterfall_status`

### 7. Output Dataset Details

* Rows: 198,058
* Columns: 44 total (32 predictive features)
* Target: `success` (binary)
* Success rate: 75.1%

### 8. Performance Metrics

* Processing Time: 21 min total
* Memory Usage: ~500 MB peak
* Feature-engineered dataset size: 215 MB

### 9. Key Insights

* Temporal patterns capture daily/weekly/seasonal trends
* Geometric transformations improve altitude and pass analysis
* Station characteristics and derived metrics support predictive modeling

### 10. Important Considerations

* Prevented data leakage using temporal splits
* Kept only predictive features
* Limitations: No weather data, limited equipment details, operator skill not quantified, real-time conditions not captured

### 11. Next Steps

* Model Training (`4_data_analysis/`)
* Feature Importance Analysis
* Model Evaluation
* Dashboard Integration

### 12. Maintenance & Updates

* Add new features in `03_feature_engineering.ipynb` and validate
* Refresh dataset by updating date range and rerunning both notebooks
* Validate schema and update documentation

### 13. References

* Feature Engineering Principles
* Satellite Communication Parameters
* SatNOGS Observation Quality Factors
* Pandas & SQLAlchemy Documentation

**Pipeline Version:** 1.0
**Observations Processed:** 198,058
**Features Created:** 44
**Target Variable:** `success` (75.1% positive)


