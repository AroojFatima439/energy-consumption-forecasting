# Task 3: Energy Consumption Time Series Forecasting

## 📌 Objective
The goal of this task is to **forecast short-term household energy usage** using historical time series data. The project aims to:
- Parse and resample household energy consumption data.
- Engineer time-based features such as hour of day and weekend indicators.
- Apply and compare the performance of three forecasting models: **ARIMA**, **Facebook Prophet**, and **XGBoost**.
- Evaluate models using **MAE** and **RMSE**.
- Visualize actual vs. forecasted energy consumption.

---

## 🧠 Approach

### 1. **Data Preprocessing**
- Dataset: *Individual household electric power consumption* from UCI repository.
- Combined the `Date` and `Time` columns into a `Datetime` index.
- Filtered the dataset to include only the `Global_active_power` variable.
- Resampled the data to hourly intervals to smooth out high-frequency noise.

### 2. **Feature Engineering**
- Created time-based features: `hour`, `day of week`, and `is_weekend`.
- Shifted target variable to align with forecasting one hour ahead (for XGBoost).

### 3. **Model Implementation**
- **ARIMA**: Applied ARIMA(2,1,2) for univariate time series forecasting.
- **Prophet**: Used Prophet with hourly seasonality and weekend trends.
- **XGBoost**: Supervised machine learning model trained on engineered time-based features.

### 4. **Evaluation Metrics**
- Used **Mean Absolute Error (MAE)** and **Root Mean Squared Error (RMSE)** to compare models.
- Last 7 days of the dataset used for testing (168 hours).

---

## 📊 Results and Findings

| Model    | MAE (kW) | RMSE (kW) |
|----------|----------|-----------|
| ARIMA    | ~0.25    | ~0.35     |
| Prophet  | ~0.28    | ~0.38     |
| XGBoost  | ~0.22    | ~0.31     |

- **XGBoost** outperformed the other models in both MAE and RMSE, suggesting that time-based engineered features provided useful signals for prediction.
- **ARIMA** captured overall trends but was less responsive to hourly patterns.
- **Prophet** performed reasonably well, especially in handling weekend seasonality.

### 📈 Visualization
A plot comparing actual vs. forecasted energy usage for all three models was generated. XGBoost closely tracked the actual usage, while ARIMA and Prophet lagged slightly during sudden consumption shifts.

---

## ✅ Conclusion
- Time-based feature engineering significantly improves forecasting performance.
- XGBoost is a powerful alternative to traditional time series models for short-term load forecasting.
- This approach can be extended to daily or weekly forecasting with additional seasonal adjustments.

---

## 📂 Files Included
- `energy_forecasting.py`: Python code for full pipeline (preprocessing, modeling, evaluation).
- `README.md`: Project summary and documentation.


