
# Domain Study: Predicting Satellite Observation Success using SatNOGs Data



## Overview

This folder contains the domain research and contextual background for the
machine learning pipeline project that predicts the likelihood of successful
satellite observations using real-world SatNOGs data. It provides foundational
knowledge on satellite tracking, pass parameters, signal quality, and how
SatNOGs data can be used for predictive modeling.


## About SatNOGs

[SatNOGs](https://satnogs.org/) (Satellite Networked Open Ground Station) is a
global open-source network that enables anyone to track, receive, and share data
from satellites. Managed by the Libre Space Foundation, SatNOGs provides a
distributed ground-station infrastructure that automates satellite observation
scheduling, data collection, and signal decoding. It is part of the broader
Libre Space ecosystem dedicated to open access to space technology and data.

The SatNOGs network is composed of hundreds of ground stations worldwide,
connected through a centralized database and API infrastructure. Each ground
station consists of an antenna, rotor, radio receiver, and software client that
communicates with the SatNOGs Network API.


## Satellite Passes and Signal Quality

A *satellite pass* refers to the period when a satellite is visible from a
ground station’s horizon and can transmit signals. The success of a satellite
observation depends on parameters such as:

- **Elevation**: The maximum angle above the horizon during a pass. Higher
elevation usually increases the likelihood of strong, interference-free signals.
- **Duration**: The total time the satellite remains visible and within
communication range. Longer durations often result in higher-quality
observations.
- **Time of Day**: Environmental conditions and satellite position relative to
the Sun can affect signal propagation.
- **Frequency and Bandwidth**: Different satellite missions transmit on various
frequency bands, impacting reception reliability.
- **Signal-to-Noise Ratio (SNR)**: A key quality metric that influences the
ability to decode telemetry or payload data.

Observation quality may be affected by antenna design, polarization alignment,
radio frequency interference (RFI), and local weather conditions. Understanding
these variables is essential when designing models that predict observation
outcomes.


## Observation Metadata and Labeling

Each SatNOGs observation includes metadata such as satellite ID, observer
location, observation ID, start and end time, and frequency. Observations are
labeled based on their *success status*, for example:

- **Good**: Decodable or visually confirmed signal.  
- **Bad/Failed**: No signal detected or low-quality reception.  

These labels, while useful, may contain noise due to human review variability or
incomplete reception logs. When used in machine learning, these labels serve as
classification targets, enabling supervised learning for success prediction.


## Use of SatNOGs APIs

The [SatNOGs API](https://db.satnogs.org/api/) provides programmatic access to
observation metadata, satellite information, and network data. Developers can
query for specific satellites, observation results, or ground-station
performance.

For example, the following endpoint retrieves observation data:  
```
https://network.satnogs.org/api/observations/
```
The API supports pagination and filtering by parameters such as satellite,
observer, date range, and success status—making it an ideal data source for
reproducible ML experiments.


## Relevance to Machine Learning

The SatNOGs dataset enables researchers to explore classification tasks that
predict whether a satellite observation will succeed or fail based on metadata.
The general pipeline includes:

1. **Data Collection**: Retrieve metadata from the SatNOGs API or downloaded
datasets.
2. **Preprocessing**: Clean, normalize, and select relevant features such as
elevation, duration, azimuth, and SNR.
3. **Feature Engineering**: Derive new attributes such as day/night indicator,
average elevation rate, or normalized SNR.
4. **Model Training**: Apply classification models (e.g., Logistic Regression,
Random Forest, Gradient Boosting) to predict observation success.
5. **Evaluation**: Use accuracy, precision, recall, and ROC-AUC to assess model
performance.

Integrating the model into a Streamlit dashboard allows ground-station operators
to interactively explore pass predictions and optimize observation scheduling.


## Tools and Technologies

- **Languages**: Python  
- **Libraries**: Pandas, NumPy, scikit-learn, Matplotlib, Seaborn, Streamlit  
- **APIs**: SatNOGs API  
- **Version Control**: GitHub, GitHub Actions  


## References

- SatNOGs official website: [https://satnogs.org/](https://satnogs.org/)  
- SatNOGs DB API documentation:
[https://db.satnogs.org/api/](https://db.satnogs.org/api/)
- Libre Space Foundation:
[https://librespacefoundation.org/](https://librespacefoundation.org/)
- Example studies on satellite signal quality prediction and RF analysis in
open-source datasets.
