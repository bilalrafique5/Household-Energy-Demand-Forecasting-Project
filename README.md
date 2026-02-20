🏠 Household Energy Demand Forecasting Project
Overview

This project analyzes household electricity consumption data and builds predictive models to forecast energy demand. The goal is to provide insights for energy efficiency, load shifting, and real-time demand management.

The dataset contains hourly measurements of active and reactive power, voltage, and sub-metered appliance loads.

1. Problem Definition

Engineering context:

Predict household electricity demand for 24 hours ahead.

Optimize load shifting, time-of-use tariffs, and energy efficiency measures.

Key analytical questions:

Does energy demand differ significantly between weekdays and weekends?

What are the peak consumption hours and their impact on total load?

Can advanced machine learning models accurately forecast next-day electricity demand?

2. Data Understanding & Cleaning

Raw dataset: 2,075,259 records × 7 features

Features include: Date, Time, Global_active_power, Global_reactive_power, Voltage, and 3 sub-metering measurements.

Cleaning steps:

Handle missing values using forward-fill and interpolation.

Remove corrupted or duplicate records.

Aggregate data to hourly intervals for smoother analysis.

Detect and filter outliers.

Saved cleaned data: cleaned_data.csv

3. Exploratory Data Analysis (EDA)

Visualizations included:

Time-series plots of power consumption.

Histograms and boxplots for sub-metered appliances.

Correlation heatmaps for active/reactive power, voltage, and sub-metering.

Peak vs off-peak analysis.

Insights from EDA:

Weekdays show structured usage patterns; weekends are flatter.

Morning (7-9 AM) and evening (7-10 PM) peaks.

Sub-metering breakdown: Kitchen (~42%), Laundry (~18%), HVAC/Water Heater (~40%).

4. Statistical Inference

Hypothesis tested: Weekday energy consumption is higher than weekend consumption.

Result: p < 0.001 → statistically significant difference.

Implication: Validates time-of-use tariff strategy.

5. Feature Engineering

Temporal features: hour-of-day, day-of-week, cyclical encoding.

Lag features: 24-hour prior consumption.

Sub-meter ratios: kitchen, laundry, HVAC.

Power quality: reactive power, apparent power.

Purpose: Improve prediction accuracy by capturing daily, weekly, and appliance-specific patterns.

6. Machine Learning Models

Top 5 models (based on RMSE, R², and overfitting ratio):

Ridge Regression

Gradient Boosting Regressor (Regularized)

Random Forest (Regularized)

Extra Trees Regressor

XGBoost with Early Stopping

Performance (Best Model: Gradient Boosting Regressor):

R²: 0.9999 → explains ~99.99% variance

RMSE: 0.0065 kW

MAE: 0.0048 kW

Overfitting ratio: 0.789 → minimal overfitting

Cross-validation R²: 0.9999 → robust generalization

7. Engineering Interpretation & Limitations

Insights:

Peak load management: Morning and evening spikes.

Kitchen loads are flexible → suitable for demand response.

Continuous loads (HVAC/Water Heater) are efficiency priorities.

Limitations:

Limitation	Impact	Mitigation
Historical dependency	Weather/events not captured	Add external regressors (temperature, holidays)
Behavioral changes	Appliance replacement	Retrain model monthly
Sampling gap	Small missing data periods	Minor effect on seasonal extremes
Single household	Not generalizable	Ensemble across multiple households
Extreme weather	HVAC spikes not captured	Include weather sensors
8. Practical Applications

Energy auditors: Target high-usage appliances for efficiency upgrades.

Utilities: Implement time-of-use pricing and peak shaving strategies.

Smart grids: Real-time load forecasting ±0.0065 kW enables better grid balancing.

9. Deployment & Usage

Prediction horizon: 24 hours ahead.

Retraining frequency: Monthly.

Recommended model: Gradient Boosting Regressor (100 trees).

Input: Cleaned hourly data with engineered features.

Output: Forecasted next-day active power demand.

10. How to Run
# Install dependencies
pip install -r requirements.txt

# Load cleaned data
python load_data.py

# Train models
python train_models.py

# Generate forecasts
python forecast.py

# Visualize results
python visualization.py

11. File Structure
project/
│
├─ data/
│   ├─ raw_data.csv
│   └─ cleaned_data.csv
│
├─ notebooks/
│   └─ EDA_and_Modeling.ipynb
│
├─ scripts/
│   ├─ load_data.py
│   ├─ train_models.py
│   ├─ forecast.py
│   └─ visualization.py
│
├─ requirements.txt
└─ README.md

12. Conclusion

The project successfully:

Cleansed and prepared a large household energy dataset.

Performed detailed EDA and statistical testing.

Built and evaluated multiple ML models.

Recommended Gradient Boosting Regressor for real-time forecasting.

Provided actionable engineering insights for energy efficiency and load management.