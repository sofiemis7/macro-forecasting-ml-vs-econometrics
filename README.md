# Forecasting Macroeconomic Indicators  
**Comparing Classical Econometrics and Machine Learning Approaches**

---

## Project Overview

This project investigates the forecasting of key macroeconomic indicators—namely inflation (CPI), unemployment, and GDP growth—using both classical time series models and modern machine learning techniques. The goal is to assess predictive performance, interpretability, and policy relevance across methods.

Forecasting economic indicators is critical for central banks, policy planners, and asset managers. This project bridges the gap between transparent statistical modeling and high-performance machine learning pipelines.

---

## Objectives

- Forecast macroeconomic indicators using real-world time series data
- Compare performance between classical econometric models and machine learning techniques when:
    (i) predictors are high-dimensional,
    (ii) relationships are non-linear, and
    (iii) structural breaks are present.
- Highlight trade-offs in accuracy, interpretability, and policy implications
- Provide a modular, extensible framework for future experimentation
---

## Target Indicators

- **Consumer Price Index (CPI)** – as a measure of inflation
- **Unemployment Rate**
- **Real GDP Growth**
- **Industrial Production: Total Index (INDPRO)** 
- **Personal Consumption Expenditure**

All data are quarterly and span from **Q1 2000 to Q2 2025**.

---

## Data Sources

- [OECD.Stat](https://stats.oecd.org)
- [Federal Reserve Bank of St. Louis (FRED)](https://fred.stlouisfed.org/)
- [International Monetary Fund (IMF)](https://www.imf.org/en/Data)

---

## Methods Compared

| Method              | Type                  | Notes                                                   |
|---------------------|-----------------------|----------------------------------------------------------|
| ARIMA               | Econometric (univariate) | Benchmark for inflation and GDP                         |
| VAR                 | Econometric (multivariate) | Captures co-movements among variables                  |
| Prophet    | Hybrid (additive + holidays) | Flexible, interpretable for trend-seasonal mix      |
| Random Forest       | Machine Learning       | Lagged feature model; robust but not time-aware          |
| XGBoost Regressor   | Machine Learning       | High performance; used with lagged and derived features  |
| LSTM                | Deep Learning (RNN)    | Captures non-linear dynamics and long-range memory       |

---

## Evaluation Metrics

- **RMSE** – Root Mean Squared Error  
- **MAE** – Mean Absolute Error  
- **MAPE** – Mean Absolute Percentage Error  
- **Walk-forward cross-validation** – to simulate real-world forecasting conditions  
- **Forecast interval coverage** – for models that support uncertainty quantification

---

## Repository Structure

```plaintext
/data/                   → Cleaned time series datasets
/notebooks/              → Exploratory analysis, model building, evaluation
/models/                 → Serialized models (where applicable)
/plots/                  → Forecast plots and SHAP explanations
README.md                → Project documentation
requirements.txt         → Reproducible environment setup
