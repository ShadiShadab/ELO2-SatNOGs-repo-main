
# FOUR-YEAR OBSERVATION DATASET SUMMARY (2021-2025)
Generated: 2025-12-11 17:31:01
Filename: four_year_observations_20251211_1730.csv

## DATA EXTRACTION
- Time period requested: Last 4 years (from 2021-11-12)
- Latest observation in DB: 2025-11-12 09:59:41
- Observations in 4-year period: 7,560,410
- Sample size extracted: 1,000,000
- Final cleaned observations: 578,010

## TEMPORAL COVERAGE
- Date range: 2021-11-12 to 2025-11-12
- Years represented: [np.int32(2021), np.int32(2022), np.int32(2023), np.int32(2024), np.int32(2025)] (5 years)
- Months represented: [np.int32(1), np.int32(2), np.int32(3), np.int32(4), np.int32(5), np.int32(6), np.int32(7), np.int32(8), np.int32(9), np.int32(10), np.int32(11), np.int32(12)] (12 months)
- Seasons represented: ['fall', 'spring', 'summer', 'winter'] (4 seasons)
- Total time span: 1461 days

## TARGET VARIABLE
- Success (1): 285,875.0 observations
- Failure (0): 292,135.0 observations
- Success rate: 49.46%
- Ambiguous observations removed: 421,988

## STATUS CODE DISTRIBUTION (Original)
status
 100     421988
 0       285876
-100     202384
-1000     89752

## STATION DATA COVERAGE
- Observations with station coordinates: 578,010
- Station coverage: 100.0%
- Unique stations: 1,526
- Unique stations with location data: 1,526

## FEATURE CATEGORIES
### Temporal Features (10)
- Hour, day, week, month, year
- Season, time of day categories
- Duration in seconds and categories

### Geometric Features (5)
- Maximum altitude: 0.0 to 90.0 degrees
- Elevation categories: ['high', 'low', 'medium', 'very_high', 'very_low']
- Duration range: 180 to 6086 seconds

### Station Features (7)
- Latitude, longitude, altitude
- Horizon minimum elevation
- Grid square location
- Station status

## DATA QUALITY
- Invalid durations removed: 2
- Invalid elevations removed: 0
- Duplicates removed: 0
- Missing station coordinates: 0

## FEATURE CORRELATIONS WITH SUCCESS
Top correlations:
- status: 0.538
- archived: 0.117
- experimental: -0.099
- year: 0.083
- max_altitude: 0.071

## FILES CREATED
1. `four_year_observations_20251211_1730.csv` - Full cleaned dataset (578,010 rows, 261.6 MB)
2. `four_year_sample_50000.csv` - EDA sample (50,000 rows)

## NEXT STEPS
1. Explore dataset in `3_data_exploration/` 
2. Engineer additional features (satellite metadata, weather, etc.)
3. Address missing station data (imputation or feature engineering)
4. Create train/test splits for modeling
5. Begin model development in `4_data_analysis/`
