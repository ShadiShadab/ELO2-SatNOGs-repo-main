# Technical Information – SatNOGS Dataset

## 🗄️ Database Information

### Connection Details
```python
DB_USER = "root"
DB_PASSWORD = "123456789"
DB_HOST = "127.0.0.1"
DB_PORT = "3306"
DB_NAME = "newdata"  # Original: "satnogs"
```

### Tables in Database (16 total)
| Table | Rows | Description |
|-------|------|-------------|
| base_observation | 12,546,241 | Main observation records |
| base_station | 3,912 | Ground station information |
| base_satellite | 2,903 | Satellite metadata |
| base_satelliteentry | 9,759 | Detailed satellite info |
| base_transmitterentry | 9,869 | Transmitter configurations |
| base_antenna | 4,437 | Station antenna configurations |
| base_frequencyrange | 5,311 | Frequency ranges |
| ... | ... | 9 additional tables |

---

## 🔄 Data Relationships

**Main joins used for data preparation:**
```sql
FROM base_observation obs
LEFT JOIN base_station sta ON obs.ground_station_id = sta.id
LEFT JOIN base_satelliteidentifier sat_ident ON obs.sat_id = sat_ident.sat_id
LEFT JOIN base_satellite sat ON sat_ident.id = sat.satellite_identifier_id
LEFT JOIN base_satelliteentry sat_entry ON sat.satellite_entry_id = sat_entry.id
```

**Key foreign keys:**  
- observation.ground_station_id → station.id  
- observation.sat_id → satelliteidentifier.sat_id  
- satellite.satellite_identifier_id → satelliteidentifier.id  
- satellite.satellite_entry_id → satelliteentry.id  

---

## 📊 Data Quality Assessment
- Missing station data: 1,942 rows (1.0%)  
- Missing satellite data: 0 rows  
- Missing coordinates: 1,942 rows (1.0%)  

**Data Cleaning Applied:**  
- Removed rows with missing essential data  
- Validated durations (end ≥ start)  
- Filled `waterfall_status` with median (1.00)  
- Filled `elevation_category` with mode ("High")  
- Created binary target `success` (1=good, 0=bad)  

---

## 🗺️ Geographic Coverage
- Total Stations: 1,072  
- Northern Hemisphere: Majority of stations  
- Southern Hemisphere: Limited  
- Equatorial region (|lat|<5): 5,511 observations  

---

## 📊 Statistical Summary

**Numerical Features**
| Feature | Mean | Std | Min | 25% | 50% | 75% | Max |
|---------|------|-----|-----|-----|-----|-----|-----|
| max_altitude | 49.0° | 24.4° | 0° | 29° | 48° | 71° | 90° |
| duration_minutes | 7.8 | 3.7 | 3.0 | 4.8 | 7.2 | 10.6 | 75.5 |
| station_lat | 43.2 | 18.5 | -90.0 | 47.1 | 48.0 | 54.5 | 90.0 |
| station_alt | 247m | 334m | -60m | 100m | 150m | 280m | 3600m |
| station_horizon | 11.5° | 9.2° | 0° | 5° | 10° | 16° | 90° |

**Categorical Features**
| Feature | Unique Values | Most Common |
|---------|---------------|-------------|
| satellite_status | 4 | "alive" |
| station_hemisphere | 2 | "Northern" (93%) |
| qthlocator | 826 | Various grid squares |
| satellite_name | 1,769 | Various satellite names |

---

## 🛠️ Technical Details

**File Formats:** Parquet (primary), CSV (samples), SQL (raw)  
**Compression:** Snappy (50–70% reduction vs CSV)  
**Memory Usage:** Full dataset ~215 MB, Sample ~10 MB  

**Data Sampling:** Stratified sampling to maintain 75/25 success/failure ratio  

---

## 🔄 Update Procedure
1. Run `02_recent_data_preparation.ipynb`  
2. Update date filters to include new period  
3. Re-run `03_feature_engineering.ipynb`  
4. Validate new data matches schema  
5. Update documentation if schema changes  

---

## 📚 References
- SatNOGS Database Documentation  
- SatNOGS API Documentation  
- Observation Quality Metrics  
- MIT Capstone Project Dataset Context
