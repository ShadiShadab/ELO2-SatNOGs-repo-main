# Satellite Observation Success Prediction (SatNOGS Domain Study)

This document reviews the SatNOGS satellite ground-station project and relevant factors affecting observation success. SatNOGS (Satellite Networked Open Ground Station) is a global, open-source network of modular ground stations for tracking satellites. Operators worldwide can use its web interface to schedule observations on any station and share results openly. The SatNOGS DB provides a crowdsourced transmitter database (with free CC-BY-SA licensing) and a REST API for satellite/transmitter metadata. Similarly, the SatNOGS Network API allows retrieving scheduled passes and observation results (also CC-BY-SA). Together, these resources let us fetch real pass parameters (e.g. elevation, duration, time) and observation outcomes for machine learning.

- **Project Goals:** Build a Python pipeline that uses SatNOGS pass metadata to predict whether a satellite observation will be successful. Apply classification models (e.g. logistic regression, random forests) to labeled SatNOGS data, and visualize results in an interactive Streamlit dashboard. Maintain code with GitHub/GitHub Actions and present findings clearly for SatNOGS contributors and academics.  

## Satellite Pass Characteristics

A **satellite pass** is the interval when a satellite rises above the local horizon and is within line-of-sight of a ground station. Pass parameters include start/end times, duration, maximum elevation angle, and azimuth. In Low-Earth Orbit (LEO) scenarios, passes are short (often minutes) and rapidly changing. Key pass features influencing reception include:

- **Elevation angle:** the vertical angle above the horizon. Higher elevation means the satellite is more overhead. High-elevation passes yield stronger signals and more favorable geometry because the path is more direct and has fewer obstructions. By contrast, at low elevations (satellite near horizon) path loss is much greater.
- **Duration:** how long the satellite remains above the horizon. Longer passes give more time to capture data and integrate weak signals. Pass duration depends on orbital inclination and station latitude; it peaks when the station lies directly under the satellite’s ground track.
- **Time-of-day:** (Local time or sun angle) can affect noise and visibility. For example, passes during daylight may have more solar radio interference on some bands, while night passes might see different ionospheric noise. We include time-of-day as a feature, although its impact is generally context-dependent.

In summary, passes that are longer and reach higher elevation generally produce better link quality, because path loss is minimized and antennas have clearer views.

## Observation Success Criteria

SatNOGS observations are automatically labeled based on whether the satellite’s signal was detected. A **“Good”** observation means the system identified the expected satellite signal (waterfall pattern, beacon, or data) in the recorded data. A **“Bad”** observation means no signal was found in the data despite a functioning station. (SatNOGS also uses “Failed” for cases where the station had a clear error or did not return data.)

In practice, SatNOGS contributors equate “Good” with *observed signal from target* and “Bad” with *no signal from target while station was operational*. These labels come from vetting algorithms and user feedback, but for our purposes they serve as the ground-truth classes. Our ML pipeline will treat **Success = Good** (satellite heard) and **Failure = Bad** (no signal) when training classifiers.

## Data Sources and Feature Engineering

We will gather data via the SatNOGS APIs and database:  

- **SatNOGS Network API:** provides scheduled observation records including pass metadata (start/end UTC, duration, max elevation, station ID, satellite/transmitter ID, etc.) and the final automated/vetted status.  
- **SatNOGS DB API:** provides reference details about satellites and transmitters (frequency, mode, which can be cross-referenced with passes).  

All these APIs are open and CC-BY-SA licensed, allowing free data collection. Using Python (with `requests` or `pysatnogs` packages), we will download historical observations. Each record will include features like **max elevation**, **pass duration**, **start time of day**, plus details of the transmitter (frequency, encoding mode) and ground station (antenna gain patterns or site location if available). Categorical features (e.g. mode, station) can be one-hot encoded or similarly processed. Numerical features may be scaled or binned as needed.  

Data will be cleaned to remove obvious anomalies (e.g. zero-duration passes or “Failed” cases). We will then split the dataset into training and test sets (e.g. 80/20), ensuring the class balance is maintained. Since “Good/Bad” rates may be imbalanced (many passes yield no signal), we may apply techniques like class weighting or SMOTE.

## Classification Pipeline

We will experiment with several supervised classifiers using scikit-learn and related libraries. The pipeline steps include:

1. **Training/Test Split:** Partition the processed dataset into train and test subsets, preserving class proportions.  
2. **Model Selection:** Evaluate multiple algorithms (e.g. logistic regression, random forest, gradient-boosted trees) to find the best predictor.  
3. **Training:** Fit models on the training data. Use cross-validation and hyperparameter tuning (e.g. grid search) to optimize performance.  
4. **Evaluation:** Measure accuracy, precision, recall, F1-score, and ROC-AUC on the test set. A confusion matrix will show how well “Good” vs “Bad” passes are separated. Feature importance (from trees or coefficients) will reveal which pass parameters most influence success.  
5. **Iterate and Refine:** Based on results, we may engineer additional features (e.g. antenna elevation restrictions, horizon mask, seasonal effects) or try ensemble methods to improve accuracy.

## Interactive Dashboard and Tools

To make the results accessible to ground-station operators, we will build a Streamlit-based dashboard. This app will allow users to input or select upcoming passes (with parameters) and view the predicted success probability. It may also display visual summaries (charts of feature vs success rates, histograms, or model ROC curves) to help operators understand the predictions.

**Languages & Libraries:** Implementation will be in Python. Core libraries include Pandas and NumPy for data handling, scikit-learn for modeling, and Matplotlib/Seaborn for plots. The dashboard uses Streamlit. We will version-control the code on GitHub, using GitHub Actions for continuous integration (e.g. running tests or linting on push). Documentation (this README and any Jupyter notebooks) will be maintained in the repo.

**Reproducibility:** All data processing and model steps will be documented. The SatNOGS data API access requires an API key (obtainable via a SatNOGS account), and our code will include instructions to fetch data. Any computed results (trained model, plots) will be generated automatically by scripts or notebooks.

## Expected Outcomes

By correlating historical pass metadata with observation outcomes, we expect to identify patterns and build a reliable predictor of success. The final model can help planners decide which passes to schedule (e.g. prioritizing high-probability opportunities) and may guide station operators on improvements (e.g. antenna upgrades for low-elevation coverage). All results will be presented in a clear, professional manner with figures and tables. The code and findings, targeted at both SatNOGS contributors and academic readers, will be fully referenced and open-sourced along with the project.
