# 🛰️ SatNOGS Success Predictor Dashboard

## Overview
Interactive dashboard showcasing the **Satellite Pass Prediction & Observation Success Rate** capstone project for the **MIT Emerging Talent Program**. The dashboard provides ground station operators with actionable insights and predictions to optimize satellite observation scheduling.

![Dashboard Screenshot](https://github.com/ShadiShadab/ELO2-SatNOGs-repo-main/blob/f408dd79f069878b33f0c9e52d243a0026d61038/5_communication_strategy/dashboard/dashboard_prototype/14.12.2025_22.48.57_REC.mp4)

---

## ✨ Features

### 📊 Performance Overview
- Real-time display of model performance metrics
- Business impact visualization (success rate improvement)
- Confusion matrix and error analysis

### 🔍 Feature Analysis
- Interactive feature importance charts
- Permutation importance visualization
- Key insights from model interpretation

### 🎯 Business Rules
- Four implementable rules for operators
- Code examples for integration
- Clear implementation roadmap

### 🔮 Interactive Success Predictor
- Live success probability estimation
- Parameter adjustment with real-time updates
- Rule-based recommendations

### 📈 Model Insights
- Technical specifications
- Error analysis
- Sample predictions viewer

---

## 🚀 Quick Start

### Prerequisites
- Python 3.8 or higher
- pip package manager

### Installation
```bash
cd satellite-pass-prediction/5_communication_strategy/dashboard/dashboard_prototype
pip install -r requirements.txt
streamlit run app.py
Open your browser at:
http://localhost:8501

🧠 Technical Architecture
Data Flow
mathematica
Copy code
SatNOGS Database → Pre-processed Data → Trained Model → Dashboard
      ↓                    ↓                   ↓           ↓
  12.5M+ obs         578K samples        Random Forest   Streamlit
                                          94.6% ROC-AUC   UI
Key Components
Data Loading: Cached metrics and feature importance

Visualization Engine: Plotly

Prediction Logic: Rule-based estimation

UI Framework: Streamlit with custom CSS

📂 File Structure
kotlin
Copy code
dashboard_prototype/
├── app.py
├── requirements.txt
├── README.md
├── assets/
└── data/
📊 Data & Model Sources
Metrics: final_test_metrics.json

Feature importance: feature_importance_final.csv

Sample predictions: test_set_predictions.csv

Model: randomforest_tuned_model.pkl (loaded on demand)

⚡ Performance Optimization
Caching Strategy
python
Copy code
@st.cache_data(ttl=3600)
def load_metrics():
    pass

@st.cache_resource
def load_model():
    pass
Lazy Loading
Metrics load immediately

Large model loads only when needed

Predictions load in chunks

👥 User Guide
For Operators
Review performance overview

Apply business rules

Test scenarios with predictor

Understand key features

For Developers
Inspect model insights

Review error analysis

Extend visualizations

🚢 Deployment Options
Local
bash
Copy code
streamlit run app.py --server.port 8501
Streamlit Cloud
Push to GitHub

Connect at https://streamlit.io/cloud

Set app.py as entry file

Docker
dockerfile
Copy code
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt.
RUN pip install -r requirements.txt
COPY . .
EXPOSE 8501
CMD ["streamlit", "run", "app.py"]
📜 License
Code: MIT License

Data: SatNOGS Open Database License (ODbL)

Documentation: CC BY 4.0

🙏 Acknowledgments
MIT Emerging Talent Program

Libre Space Foundation

SatNOGS volunteer community

📬 Contact
Project Lead: Shadi Shadabshoar
GitHub: https://github.com/ShadiShadab/ELO2-SatNOGs-repo-main
