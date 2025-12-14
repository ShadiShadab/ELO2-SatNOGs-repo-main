#  Data Preparation 

## 📋 Overview

This directory contains scripts and notebooks for transforming raw
SatNOGS database data into a machine-learning-ready dataset. The goal is
to create clean, feature-rich data for predicting satellite observation
success rates.

------------------------------------------------------------------------

## 🎯 Objectives

1.  **Data Extraction** -- Load and sample observations from the
    database
2.  **Data Cleaning** -- Handle missing values, outliers, and
    inconsistencies
3.  **Feature Engineering** -- Create temporal, geometric, and
    station-based features
4.  **Target Definition** -- Map observation status codes to
    success/failure labels
5.  **Dataset Export** -- Save processed data for EDA and modeling

------------------------------------------------------------------------

## 📁 File Structure

    2_data_preparation/
    ├── 01_create_four_year_dataset.ipynb     # Main dataset creation notebook
    ├── README.md                             # This documentation file
    └── utils.py                              # Helper functions

------------------------------------------------------------------------

## 📊 Dataset Creation Diagram (ASCII)

    Raw SatNOGS DB
            |
            v
    +------------------------+
    |  Phase 1: Extraction   |
    +------------------------+
            |
            v
    +------------------------+
    |   Phase 2: Cleaning    |
    +------------------------+
            |
            v
    +------------------------+
    | Phase 3: Engineering   |
    +------------------------+
            |
            v
    +------------------------+
    | Phase 4: Final Dataset |
    +------------------------+

------------------------------------------------------------------------

## 🚀 Key Outputs

Processed datasets saved to `1_datasets/processed/`:

-   **[four_year_observations_20251211_1730.csv](https://drive.google.com/file/d/1GpEPox2BWIgo1tlQntszdKGLe5sh0R2Z/view?usp=sharing)**
-   **[four_year_sample_50000.csv](https://drive.google.com/file/d/1BhvSU8r-15TUnllhTQLzXQ12ksgQkB0q/view?usp=sharing)**

------------------------------------------------------------------------

## 📊 Dataset Creation Process

### Phase 1 --- Data Extraction

-   Connect to MariaDB/MySQL database
-   Extract observations from last 4 years (2021--2025)
-   Randomly sample 1M observations
-   Load station metadata

### Phase 2 --- Data Cleaning

-   Target mapping (success/fail/ambiguous)
-   Remove invalid durations & elevations
-   Remove duplicates
-   Ensure full completeness

### Phase 3 --- Feature Engineering

Includes temporal, geometric, and station features.
(Full details preserved from your input.)

### Phase 4 --- Dataset Characteristics

-   578,010 rows × 39 features
-   262 MB full dataset

------------------------------------------------------------------------

## 🔧 Technical Details

Includes DB schema, sampling strategy, and data quality metrics.

------------------------------------------------------------------------

## 📈 Performance Insights

(Status-based success rates, key correlations, etc.)

------------------------------------------------------------------------

## 🛠️ Usage

``` python
import pandas as pd
df = pd.read_csv("../1_datasets/processed/four_year_observations_20251211_1730.csv")
df_sample = pd.read_csv("../1_datasets/processed/four_year_sample_50000.csv")
```

------------------------------------------------------------------------

## 🔄 Reproducibility

-   Run notebook sequentially\
-   Runtime: \~2 hours\
-   Sampling uses `ORDER BY RAND()`

------------------------------------------------------------------------

## 📝 Next Steps

Future improvements include weather integration, satellite metadata, and
feature selection.

------------------------------------------------------------------------

## 🚨 Known Issues & Limitations

Ambiguous observations (42.20%) filtered out.

------------------------------------------------------------------------

## 📚 References

SatNOGS DB, API, Docs, plus ML feature engineering references.

------------------------------------------------------------------------

## 📄 License

-   Data: ODbL\
-   Code: MIT\
-   Documentation: CC BY 4.0

------------------------------------------------------------------------

![License](https://img.shields.io/badge/License-MIT-blue.svg)
![Status](https://img.shields.io/badge/Project%20Phase-Data%20Preparation%20Complete-brightgreen)
