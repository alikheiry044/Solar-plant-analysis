# Solar-plant-analysis
Description: Solar Power Plant Data Analysis — EDA &amp; Anomaly Detection
# ☀️ Solar Power Plant — Data Analysis Project

![Python](https://img.shields.io/badge/Python-3.8+-3776AB?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7-11557c)
![Scikit--learn](https://img.shields.io/badge/Scikit--learn-1.3-F7931E?logo=scikit-learn&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-2ecc71)

> **End-to-end data analysis on real-world solar energy data** — uncovering generation patterns, weather impacts, inverter anomalies, and predictive modeling across two photovoltaic plants.

---

## 🎯 Project Highlights

| | Result |
|--|--|
| Dataset | 136,476 records across 4 CSV files |
| Time Period | 34 days of continuous operation |
| Key Finding | Plant 2 produces **23% less** power despite receiving **more irradiation** |
| ML Accuracy | **99.18% R²** with Random Forest |
| Anomalies Found | **5 underperforming inverters** identified |

---

## 📁 Dataset

**Source:** [Kaggle — Solar Power Generation Data](https://www.kaggle.com/datasets/anikannal/solar-power-generation-data)

| File | Description | Records |
|------|-------------|---------|
| Plant_1_Generation_Data.csv | DC/AC power per inverter — Plant 1 | 68,778 |
| Plant_1_Weather_Sensor_Data.csv | Temperature & irradiation — Plant 1 | 3,182 |
| Plant_2_Generation_Data.csv | DC/AC power per inverter — Plant 2 | 67,698 |
| Plant_2_Weather_Sensor_Data.csv | Temperature & irradiation — Plant 2 | 3,259 |

---

## 🔬 Methodology

### 1. Data Loading & Inspection
- Loaded 4 CSV files — **zero missing values** across all files
- Verified data types, shape, and null values

### 2. Data Cleaning & Feature Engineering
- Converted DATE_TIME to datetime format
- Extracted: date, hour, day, day_of_week
- **Data quality fix:** Plant 1 DC_POWER was in Watts not kW — divided by 1000
- Created temp_diff feature (module minus ambient temperature)

### 3. Exploratory Data Analysis
- Descriptive statistics and correlation matrix
- Daily and hourly generation patterns
- Weather sensor analysis
- 10+ visualization types

### 4. Machine Learning
- Train/Test Split: 80% / 20%
- StandardScaler for Linear Regression
- Trained: Linear Regression + Random Forest
- Evaluated with MAE, RMSE, R²

### 5. Anomaly Detection
- IQR method: Threshold = Q1 minus 1.5 times IQR
- Identified 5 underperforming inverters

---

## 📊 Key Findings

### Plant 2 underperforms despite better irradiation

Plant 1: 622.6 MWh/day | Irradiation: 0.2283 | Temp: 25.5°C
Plant 2: 480.4 MWh/day | Irradiation: 0.2327 | Temp: 28.1°C

Plant 2 receives 2% more irradiation but produces 23% less power.
Root cause: Higher operating temperature reduces panel efficiency.

### Irradiation dominates power output

| Variable | Correlation Plant 1 | Correlation Plant 2 |
|----------|---------------------|---------------------|
| IRRADIATION | 0.992 | 0.831 |
| MODULE_TEMP | 0.924 | 0.764 |
| AMBIENT_TEMP | 0.537 | 0.482 |

Plant 2 weaker correlation (0.831 vs 0.992) reveals faulty inverters disrupting the pattern.

### 5 weak inverters identified

| Plant | Inverter | Mean Power | Status |
|-------|----------|------------|--------|
| Plant 1 | 1BY6WEcL... | 527 kW | Below 559 kW threshold |
| Plant 1 | bvBOhCH3... | 534 kW | Below 559 kW threshold |
| Plant 2 | Quc1TzYx... | 385 kW | 24% below average |
| Plant 2 | Et9kgGMD... | 425 kW | Below 456 kW threshold |
| Plant 2 | LYwnQax7... | 445 kW | Below 456 kW threshold |

---

## 🤖 Machine Learning Results

| Model | MAE | RMSE | R2 |
|-------|-----|------|----|
| Linear Regression | 648.78 kW | 840.83 kW | 0.9888 |
| Random Forest | 483.92 kW | 719.47 kW | 0.9918 |

Random Forest wins with 99.18% accuracy and 165 kW less mean error.

Feature Importance:
- IRRADIATION: 95.2% — dominant driver
- day: 2.1%
- temp_diff: 1.1%
- MODULE_TEMPERATURE: 0.8%
- AMBIENT_TEMPERATURE: 0.5%

---

## 🛠️ Tech Stack

| Library | Usage |
|---------|-------|
| Pandas | Data loading, cleaning, groupby, merge |
| NumPy | Numerical operations |
| Matplotlib | 10+ chart types |
| Scikit-learn | ML models, scaling, evaluation |

---

## ▶️ How to Run

git clone https://github.com/YOUR_USERNAME/solar-plant-analysis.git
cd solar-plant-analysis
pip install -r requirements.txt
jupyter notebook SolarCell.ipynb

---

## 📦 Requirements

pandas>=2.0
numpy>=1.24
matplotlib>=3.7
scikit-learn>=1.3
jupyter

---

## 💡 Skills Demonstrated

- Data Loading and Inspection
- Data Cleaning and Preprocessing
- Data Quality Analysis — discovered DC_POWER unit mismatch
- Exploratory Data Analysis — 10+ chart types
- Correlation Analysis
- Machine Learning — Linear Regression, Random Forest
- Model Evaluation — MAE, RMSE, R2, Feature Importance
- Anomaly Detection — IQR method

---

## 🔭 Next Steps

- Isolation Forest for anomaly detection
- Time series forecasting with Prophet or LSTM
- Interactive dashboard with Streamlit
- Deploy on Streamlit Cloud

---

## 👤 Author

Your Name Here
- GitHub: https://github.com/YOUR_USERNAME
- LinkedIn: https://linkedin.com/in/YOUR_LINKEDIN

---

Dataset source: Kaggle — Solar Power Generation Data
https://www.kaggle.com/datasets/anikannal/solar-power-generation-data
