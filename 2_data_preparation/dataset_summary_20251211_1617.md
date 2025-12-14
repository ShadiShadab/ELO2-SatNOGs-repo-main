
# RECENT OBSERVATION DATASET SUMMARY
Generated: 2025-12-11 16:18:11
Filename: recent_observations_20251211_1617.csv

## DATA EXTRACTION
- Time period: Last 4 years (from 2021-11-12)
- Latest observation: 2025-11-12 09:59:41
- Initial observations queried: 1,000,000
- Final cleaned observations: 682,250

## TARGET VARIABLE
- Success (1): 411,001.0 observations
- Failure (0): 271,249.0 observations
- Success rate: 60.24%

## STATUS CODE DISTRIBUTION (Original)
status
 0       411001
 100     317750
-100     167486
-1000    103763

## FEATURE CATEGORIES
### Temporal Features (8)
- Hour of day, day of week, month, year
- Season, time of day categories
- Duration in seconds and categories

### Geometric Features (5)
- Maximum altitude (degrees) and elevation categories
- Rise and set azimuth angles
- Azimuth range

### Station Features (6)
- Latitude, longitude, altitude
- Horizon minimum elevation
- Grid square location
- Station status

## DATA QUALITY
- Observations with station data: 125,973 (18.5%)
- Invalid durations removed: 0
- Invalid elevations removed: 0

## FILES CREATED
1. `recent_observations_20251211_1617.csv` - Full cleaned dataset (682,250 rows)
2. `recent_observations_sample_50000.csv` - EDA sample (50,000 rows)

## NEXT STEPS
1. Explore dataset in `3_data_exploration/`
2. Engineer additional features (satellite types, station capabilities)
3. Create train/test splits for modeling
4. Begin model development in `4_data_analysis/`
