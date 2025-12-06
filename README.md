## 📌 1. Project Overview

This repository contains the implementation of the study:

**“Forecasting Flight Delays From Operational and Weather Data:  
A Regression-Based Machine Learning Application”**  
:contentReference[oaicite:0]{index=0}

The project aims to predict **arrival delay durations** of domestic U.S. flights using:

- ✔️ Large-scale operational flight records  
- ✔️ Weather parameters obtained via the Meteostat API  
- ✔️ Advanced preprocessing and feature engineering  
- ✔️ Multiple machine learning regression models  
- ✔️ Flask-based local web application for real-time predictions  

The system provides **minute-level delay estimation** and can support airline operations, planning, and customer notification processes.

---

## 🌦️ 2. Dataset Description

### **Flight Data (BTS – U.S. Department of Transportation)**  
- 454,414 records  
- 40 columns  
- Includes timestamps, airports, carriers, distance, and delay durations  
- Cancelled/diverted flights removed  
- Missing values handled and anomalies corrected (IQR)

### **Weather Data (Meteostat API)**  
Collected synchronously for each flight date & airport:
- Temperature  
- Humidity  
- Wind speed  
- Precipitation  

### **Combined Dataset**  
After merging flight and weather features:
- 22 numerical features  
- 18 categorical features (one-hot encoded)  
- Scaled using MinMaxScaler  
- Time features extracted (weekday, month, time slot)

---

## 🧪 3. Feature Engineering

Applied transformations include:

- Outlier removal (IQR method)  
- One-hot encoding for categorical features  
- Date-time decomposition (day, month, weekday)  
- Weather–interaction features  
- Normalization of continuous variables  
- Removal of inconsistent flight codes & duplicates

---

## 🤖 4. Models Implemented

Five different regression models were trained and compared:

| Model | Type | Performance |
|-------|-------|-------------|
| **XGBoost** | Ensemble | ⭐ Highest R² (0.919) |
| **Random Forest** | Ensemble | Strong & stable |
| LightGBM | Gradient boosting | Moderate |
| CatBoost | Categorical boosting | Lower performance |
| LSTM | Deep Learning | Underperformed on this dataset |

### Evaluation Metrics:
- **R² (Explained Variance)**  
- **MAE (Mean Absolute Error)**  
- **RMSE (Root Mean Squared Error)**  

---

## 🏆 5. Key Findings

- **XGBoost achieved the best performance**:  
  - R² = 0.919  
  - MAE = 4.56  
  - RMSE = 6.71  

- **Weather integration significantly improved accuracy.**

- **Random Forest** produced similar performance but slightly weaker error metrics.

- **CatBoost and LSTM** had limited generalization capability due to dataset characteristics.

- Ensemble methods were more robust due to their ability to model complex nonlinear relationships.
