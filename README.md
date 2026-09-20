# Air Quality Index (AQI) Analysis & Forecasting – Indian Cities

## 📌 Project Overview

This project performs exploratory analysis and time-series forecasting of Air Quality Index (AQI) across Indian cities using Python.

The project analyzes historical daily AQI observations from January 2020 to October 2025 and investigates:

- AQI distribution across cities
- Yearly and monthly AQI trends
- Seasonal patterns
- Extreme AQI observations
- Time-series characteristics
- Forecasting performance of different models
- 12-month AQI forecasts for selected Indian cities

The forecasting analysis focuses on five cities:

- Delhi
- Mumbai
- Kolkata
- Bengaluru
- Chennai

---

## 🎯 Objectives

1. Analyze historical AQI patterns across Indian cities.
2. Identify yearly and seasonal variations in AQI.
3. Perform time-series diagnostics using ADF, ACF and PACF.
4. Compare different forecasting approaches.
5. Evaluate forecasting models using MAE, RMSE and MAPE.
6. Select a suitable forecasting model for each city.
7. Generate 12-month AQI forecasts based on historical patterns.

---

## 📊 Dataset

The dataset contains approximately **378,000 daily AQI observations** covering **200+ Indian cities**.

link-https://www.kaggle.com/datasets/krishnandansha/aqi-india-2020-to-2025-october?utm_source=chatgpt.com

### Dataset period

**January 2020 – October 2025**

### Main columns

| Column | Description |
|---|---|
| Date | Observation date |
| City | Indian city |
| Air Quality | AQI category |
| AQI Value | Numerical AQI value |
| Prominent Pollutant | Reported prominent pollutant |

The original dataset also contained a column labeled `S.No`, which was identified as month information and was not required because month information could be derived directly from the `Date` column.

The `Prominent Pollutant` column was found to contain the same value across the dataset and therefore did not provide useful variation for the analysis.

---

## 🛠️ Technologies Used

### Programming Language
- Python

### Libraries
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Statsmodels
- Scikit-learn
- Prophet

---

## 🔎 Exploratory Data Analysis

The project includes analysis of:

### City-level AQI
Comparison of average AQI across cities in the dataset.

### AQI Categories
Distribution of observations across AQI categories such as:

- Good
- Satisfactory
- Moderate
- Poor
- Very Poor
- Severe

### Yearly Trends
Analysis of average AQI across the years 2020–2025.

> Note: 2025 contains data only through October and should not be directly compared with complete years.

### Monthly Seasonality

The analysis identified a recurring seasonal pattern, with generally higher AQI values during late-year and winter months and lower values during several middle-year months.

### Extreme AQI

The project also investigates observations with very high AQI values, including AQI values of 400 or above.

---

## 📈 Time-Series Analysis

For the forecasting stage, monthly AQI data was created for the selected cities.

Time-series diagnostics included:

### ADF Test

The Augmented Dickey-Fuller test was used to examine stationarity.

### ACF

Autocorrelation analysis was used to identify temporal dependencies and seasonal patterns.

### PACF

Partial autocorrelation analysis was used to understand important lag relationships.

The monthly ACF showed evidence of approximately **12-month seasonal behavior**, supporting the use of yearly seasonality in monthly forecasting.

---

# 🤖 Forecasting Models

The project compares three main forecasting approaches.

## 1. Seasonal Naive

The previous year's value for the same month is used as the forecast.

This provides a simple baseline for evaluating more complex models.

## 2. SARIMA

The main statistical forecasting model used was:

```text
SARIMA(1,0,1)(1,0,1,12)