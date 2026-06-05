# 🚦 TrafficFlow AI

### Intelligent Traffic Demand Forecasting using Machine Learning and CatBoost

![Python](https://img.shields.io/badge/Python-3.13-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-CatBoost-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

# 📌 Project Overview

Traffic congestion is one of the most significant challenges faced by modern cities. Accurate traffic demand prediction enables transportation authorities to optimize traffic flow, improve road utilization, and reduce congestion.

TrafficFlow AI is a machine learning-based traffic demand forecasting system developed to predict traffic demand using location, road characteristics, weather conditions, and temporal information.

The project was built using CatBoost Regression and advanced feature engineering techniques on a real-world traffic dataset containing over 77,000 observations.

---

# 🎯 Problem Statement

Predict traffic demand for unseen locations and time intervals using:

* Road Type
* Weather Conditions
* Geographical Location (Geohash)
* Number of Lanes
* Presence of Large Vehicles
* Nearby Landmarks
* Temperature
* Time Information

---

# 📊 Dataset Information

| Metric           | Value  |
| ---------------- | ------ |
| Training Samples | 77,299 |
| Testing Samples  | 41,778 |
| Features         | 10     |
| Target Variable  | demand |

### Dataset Features

| Feature       | Description                 |
| ------------- | --------------------------- |
| Index         | Unique Identifier           |
| geohash       | Encoded Geographic Location |
| day           | Day of Observation          |
| timestamp     | Time of Observation         |
| RoadType      | Type of Road                |
| NumberofLanes | Number of Lanes             |
| LargeVehicles | Heavy Vehicle Presence      |
| Landmarks     | Nearby Landmarks            |
| Temperature   | Environmental Temperature   |
| Weather       | Weather Condition           |
| demand        | Traffic Demand              |

---

# 🛠 Technology Stack

### Programming Language

* Python

### Libraries

* Pandas
* NumPy
* Matplotlib
* Seaborn
* CatBoost
* Scikit-Learn
* Folium
* PyGeoHash

### Machine Learning Techniques

* Regression Modeling
* Feature Engineering
* Target Encoding
* Missing Value Handling
* Exploratory Data Analysis

---

# ⚙️ Data Preprocessing

### Missing Value Treatment

| Feature     | Missing Values |
| ----------- | -------------- |
| Temperature | 2495           |
| Weather     | 797            |
| RoadType    | 600            |

Strategies Used:

* Median Imputation for Temperature
* Missing Category Creation for Weather
* Missing Category Creation for RoadType

---

# 🔥 Feature Engineering

The following features were created to improve predictive performance:

### Time-Based Features

* Hour
* Minute
* Time Slot
* Peak Hour Indicator
* Hour Sin Transformation
* Hour Cos Transformation
* Minute Sin Transformation
* Minute Cos Transformation

### Target Encoded Features

* Geo Target Encoding
* Road Target Encoding
* Weather Target Encoding

### Interaction Features

* Temperature × Hour
* Number of Lanes × Temperature

---

# 🤖 Machine Learning Model

## CatBoost Regressor

CatBoost was selected because:

* Handles categorical variables natively
* Requires minimal preprocessing
* Strong performance on tabular datasets
* Robust against missing values

### Hyperparameters

```python
CatBoostRegressor(
    iterations=7000,
    depth=12,
    learning_rate=0.02,
    loss_function="RMSE",
    l2_leaf_reg=5,
    bagging_temperature=1,
    random_seed=42
)
```

---

# 📈 Exploratory Data Analysis

## Missing Values Analysis

<img width="811" height="496" alt="Opera Snapshot_2026-06-06_031721_localhost" src="https://github.com/user-attachments/assets/c022c480-861f-431c-8389-a2ec3ba24bfa" />


### Key Insight

Temperature contained the highest number of missing values and required median-based imputation before training.

---

## Traffic Demand Distribution

<img width="935" height="498" alt="distribution" src="https://github.com/user-attachments/assets/06d47ef3-8e42-4ec2-b531-6bebff8187ff" />


### Key Insight

Traffic demand exhibits a highly right-skewed distribution with the majority of observations concentrated at lower demand values.

---

## Weather Impact on Traffic Demand

<img width="1085" height="644" alt="whether impact on traffic" src="https://github.com/user-attachments/assets/b3acbd5f-9ce9-412f-8088-58a3f181c2f9" />


### Key Insight

Weather conditions influence traffic demand, although demand variability remains present across all weather categories.

---

## Road Type Impact on Traffic Demand

<img width="1085" height="648" alt="road type impact" src="https://github.com/user-attachments/assets/80ca01dd-ab0f-4a5d-877f-baae3692408b" />


### Key Insight

Highways consistently demonstrate higher traffic demand compared to streets and residential roads.

---

## Average Traffic Demand by Hour

<img width="895" height="492" alt="avg traffic" src="https://github.com/user-attachments/assets/a8a3f58d-0560-4e67-b660-1c4426b46a39" />


### Key Insight

Traffic demand peaks during late morning and early afternoon periods and decreases significantly during evening hours.

---

# 📊 Model Evaluation

## Actual vs Predicted

<img width="712" height="702" alt="actual vs predicted" src="https://github.com/user-attachments/assets/f3b1b71b-78e9-44bf-a3e5-ca54d4352556" />


### Observation

Predicted values closely follow actual traffic demand values, indicating that the model successfully captures underlying traffic patterns.

---

## Feature Importance Analysis

<img width="985" height="649" alt="top 15 important target" src="https://github.com/user-attachments/assets/302f9927-b868-4bf6-9110-dbea334b0de9" />


### Top Predictive Features

1. geo_target
2. road_target
3. geohash
4. RoadType
5. hour_cos
6. timestamp
7. hour_sin

### Observation

Location-based features contribute most significantly to traffic demand prediction, highlighting the importance of geographical information.

---

# 🏆 Results

| Metric            | Value              |
| ----------------- | ------------------ |
| Model             | CatBoost Regressor |
| Hackathon Score   | 89+                |
| Evaluation Metric | R² Based Scoring   |

### Achievements

* Built an end-to-end machine learning pipeline.
* Performed advanced feature engineering.
* Achieved competitive leaderboard performance.
* Generated accurate traffic demand forecasts.

---

# 📁 Project Structure

```text
TrafficFlowAI/
│
├── data/
│   ├── train.csv
│   └── test.csv
│
├── notebooks/
│   └── TrafficFlowAI_Analysis.ipynb
│
├── src/
│   └── catboost_model.py
│
├── models/
│   └── trafficflow_ai_model.cbm
│
├── outputs/
│   ├── actual_vs_predicted.png
│   ├── feature_importance.png
│   ├── hourly_traffic_pattern.png
│   ├── weather_impact.png
│   ├── roadtype_impact.png
│   ├── demand_distribution.png
│   └── missing_values.png
│
├── submission.csv
├── requirements.txt
└── README.md
```

---

# 🚀 Future Enhancements

* Ensemble Learning (CatBoost + XGBoost + LightGBM)
* Real-Time Traffic Forecasting Dashboard
* Geospatial Heatmap Visualization
* Deep Learning-Based Traffic Prediction
* Live Traffic API Integration

---

# 💡 Skills Demonstrated

* Machine Learning
* Feature Engineering
* Regression Modeling
* Data Visualization
* Exploratory Data Analysis
* CatBoost
* Python
* Pandas
* NumPy
* Git & GitHub

---

# 👨‍💻 Author

**Jabez Bodkhe**

B.Tech Computer Science

Machine Learning | Computer Vision | AI Enthusiast

---

⭐ If you found this project interesting, consider giving it a star.
