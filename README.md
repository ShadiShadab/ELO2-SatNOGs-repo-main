# 🛰️ Satellite Pass Prediction & Observation Success Rate

## Overview  
This project builds a machine learning pipeline to predict the likelihood of successful satellite observations based on pass parameters such as elevation, duration, and time of day. Using real SatNOGs data, it applies classification models to forecast outcomes and supports ground-station operators in optimizing their tracking schedules.

## Project Structure  
├── 0_domain_study/              # Background research on satellite tracking and signal quality  
├── 1_datasets/                  # Raw and cleaned SatNOGs pass data and observation logs  
├── 2_data_preparation/          # Scripts for data cleaning, formatting, and feature engineering  
├── 3_data_exploration/          # EDA notebooks: distributions, correlations, and visual insights  
├── 4_data_analysis/             # ML modeling: training, evaluation, and performance metrics  
├── 5_communication_strategy/    # Dashboard design, user interface planning, and stakeholder messaging  
├── 6_final_presentation/        # Slide decks, demo videos, and summary reports  
├── collaboration/               # Notes and contributions from collaborators or mentors  
└── notes/                       # Personal reflections, meeting logs, and learning journal  

## Goals  
- Predict observation success using satellite pass metadata  
- Apply classification models to real-world data  
- Build an interactive dashboard for ground-station operators  
- Document and present findings in a clear, professional format  

## Tools & Technologies  
- **Languages**: Python  
- **Libraries**: Pandas, NumPy, scikit-learn, Matplotlib, Seaborn, Streamlit  
- **APIs**: SatNOGs API, optional weather APIs  
- **Deployment**: Docker, Heroku or AWS  
- **Version Control**: GitHub, GitHub Actions  

## How to Run  
1. Clone the repository  
2. Install dependencies:  
   ```bash  
   pip install -r requirements.txt

---

## Learning Outcomes
- End-to-end ML pipeline development  
- Feature engineering with satellite data  
- Model evaluation and tuning  
- Dashboarding and stakeholder communication  
- Capstone-level documentation and presentation  

---

## Acknowledgments
Thanks to the [SatNOGs community](https://satnogs.org/) for providing open access to satellite observation data and tools that make this project possible.

---

## 📄 License  
This project is licensed under the [MIT License](https://opensource.org/licenses/MIT). You are free to use, modify, and distribute this software with proper attribution.

---
*Developed as part of the Emerging Talent Program in Computer and Data Science at MIT University.*
