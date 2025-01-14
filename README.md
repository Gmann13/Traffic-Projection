
# Traffic Volume Prediction

## Overview
Traffic congestion is one of the most significant challenges faced by urban areas worldwide. It leads to delays, increased pollution, and economic losses. Predicting traffic volume can help city planners and traffic managers make data-driven decisions to optimize traffic flow, reduce congestion, and enhance overall transportation efficiency.

This project focuses on predicting traffic volume using a machine learning approach. The dataset utilized is the **Metro Interstate Traffic Volume dataset**, sourced from the **UCI Machine Learning Repository**, which contains data from a highway in the Twin Cities area, Minnesota. 

## Importance of Traffic Volume Prediction
- **Urban Planning**: Accurate traffic predictions support infrastructure development and transportation planning.
- **Real-Time Traffic Management**: Forecasts can be used to adjust traffic lights, reroute vehicles, and issue alerts.
- **Environmental Impact**: Reducing traffic congestion lowers greenhouse gas emissions and fuel consumption.
- **Commuter Experience**: Improves travel time predictions and reliability for commuters.

---

## Dataset Description
The dataset includes traffic and weather data recorded from a highway in the Twin Cities. Key features include:
- **date_time**: Timestamp of the data point.
- **temp**: Temperature in Kelvin.
- **rain_1h**: Amount of rainfall in the last hour (mm).
- **snow_1h**: Amount of snowfall in the last hour (mm).
- **clouds_all**: Percentage of cloud cover.
- **weather_main**: Main weather category (e.g., Clear, Rain).
- **weather_description**: Detailed weather description.
- **traffic_volume**: Target variable representing the traffic volume.

---

## Methods and Workflow

### **1. Data Preprocessing**
To ensure the dataset is ready for modeling, the following preprocessing steps were applied:
- **Handling Missing Values**: Missing data in features like `holiday` was replaced with binary indicators (0: No Holiday, 1: Holiday).
- **Datetime Conversion**: The `date_time` column was converted to a datetime object, and new features like `hour`, `day`, `month`, and `year` were extracted.
- **Lag Features**: Created lagged traffic volume features to capture temporal dependencies.
- **One-Hot Encoding**: Categorical features like `weather_main` and `weather_description` were transformed into numerical features.

### **2. Exploratory Data Analysis (EDA)**
EDA was conducted to uncover relationships between features and traffic volume:
- **Temporal Patterns**:
  - Higher traffic volume during weekdays compared to weekends.
  - Peak traffic observed during morning (7–9 AM) and evening (4–6 PM) rush hours.
- **Weather Impact**:
  - Clear weather correlates with higher traffic, while extreme weather conditions (rain, snow) tend to reduce traffic volume.
- **Seasonal Trends**:
  - Increased traffic during summer months and holidays.
  - Decreased traffic in winter due to adverse weather.

### **3. Insights Derived**
- **Correlation Analysis**: Temperature and cloud cover showed a moderate correlation with traffic volume. Weather conditions significantly influence traffic.
- **Lag Effects**: Traffic volume in previous hours strongly impacts current traffic volume.
- **Holidays and Weekends**: Traffic is considerably lower on holidays and weekends compared to weekdays.

---

## Machine Learning Approach

### Model Used: **RandomForestRegressor**
The RandomForestRegressor was chosen due to its:
- Robustness to outliers and noise.
- Ability to handle non-linear relationships.
- Feature importance capabilities for interpretability.

### **Model Training and Evaluation**
- The dataset was split into **80% training** and **20% testing**.
- Model performance metrics:
  - **Mean Absolute Error (MAE)**: 159.72
  - **Mean Squared Error (MSE)**: 68,101.92
  - **Root Mean Squared Error (RMSE)**: 260.96
  - **R² Score**: 0.9824
  - **Accuracy**: 98.24%

---

## Key Findings
1. **Rush Hour Traffic**: Morning and evening rush hours exhibit the highest traffic volumes, emphasizing the need for traffic management during these periods.
2. **Weather Impacts**: Adverse weather conditions such as rain and snow reduce traffic volumes, suggesting potential delays for commuters.
3. **Seasonal Variations**: Summer months and holidays are associated with distinct traffic patterns, valuable for infrastructure planning.
4. **Lag Feature Importance**: The strongest predictor of current traffic volume is traffic volume from previous hours.

---

## Conclusion
This project demonstrated the successful use of a **RandomForestRegressor** model to predict traffic volume with an accuracy of **98.24%**. The insights and predictions derived can be applied to traffic management, urban planning, and enhancing commuter experiences.

---

## Future Enhancements
1. **Incorporate Real-Time Data**: Utilize streaming data to enable real-time traffic prediction.
2. **Test Other Algorithms**: Explore Gradient Boosting, Neural Networks, or hybrid models for performance comparison.
3. **Geographic Expansion**: Apply the model to data from other urban areas to improve generalizability.
4. **Additional Features**: Include more factors like road construction, accidents, and public events.
