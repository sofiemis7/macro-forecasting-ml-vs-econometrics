# Forecasting Macroeconomic Indicators  
**Comparing Classical Econometrics and Machine Learning Approaches**

---

## Project Overview

This project benchmarks the forecasting performance of **classical econometric time-series models** against **modern machine learning approaches** for key U.S. macroeconomic indicators. The focus is on understanding differences in **predictive accuracy**, **interpretability**, and **policy relevance** under realistic forecasting conditions.

Forecasting macroeconomic indicators is central to decision-making at central banks, policy institutions, and asset managers. This repository provides a modular and extensible framework that contrasts transparent statistical models with high-capacity machine learning pipelines, particularly in environments characterized by non-linearity and structural change.

---

## Objectives

- Forecast core macroeconomic indicators using real-world time-series data
- Compare econometric and machine learning models when:
  1. predictors are high-dimensional,  
  2. relationships are non-linear, and  
  3. structural breaks or regime shifts are present
- Quantify trade-offs between accuracy and interpretability
- Provide a reproducible and extensible research framework for further experimentation

---

## Forecast Targets

The project focuses on **three primary forecast targets**:

- **Inflation** – CPI-based inflation measure  
- **Unemployment Rate**  
- **Real GDP Growth** (QoQ annualized or YoY, specified in the data pipeline)

**Sample:** Q1 2000 – Q4 2025  
**Frequency:** Quarterly

---

## Predictors / Feature Set

All predictors are aligned to quarterly frequency and include indicators capturing real activity, labor market dynamics, monetary policy, financial conditions, housing, and expectations.

### Core Real Activity & Demand
- Industrial Production Index (**INDPRO**)  
- Personal Consumption Expenditures (**PCE**)  
- Real Retail Sales  
- Real Personal Income (ex-transfers)  
- Capacity Utilization  

### Labor Market Depth
- Unemployment Rate  
- Initial & Continuing Jobless Claims  
- Employment-Population Ratio  
- Average Weekly Hours (Manufacturing)  

### Inflation Pressure & Costs
- Core CPI  
- Core PCE  
- Producer Price Index  
- Unit Labor Costs  

### Monetary Policy & Yield Curve
- Federal Funds Rate  
- Short- and long-term Treasury yields  
- Yield curve term spreads  

### Financial Conditions & Stress
- Financial Conditions Index  
- Excess Bond Premium  
- Corporate credit spreads  
- Equity market volatility (VIX)  

### Housing & Expectations (optional, ML-focused)
- Housing Starts & Building Permits  
- Mortgage Rates  
- Consumer Sentiment & Inflation Expectations  

> A **parsimonious predictor subset** is used for econometric models (e.g. VAR, SARIMAX), while an **expanded high-dimensional feature set** is employed for machine learning models to ensure a fair and informative comparison.

---

## Data Sources

- OECD.Stat  
- Federal Reserve Bank of St. Louis (FRED)  
- International Monetary Fund (IMF)  

---

## Methods Compared

| Method | Family | Notes |
|------|--------|------|
| ARIMA / SARIMAX | Econometric | Transparent univariate / conditional benchmarks |
| VAR / VECM | Econometric | Captures multivariate dynamics and co-movements |
| Prophet | Additive baseline | Flexible trend-seasonality benchmark |
| Random Forest | Machine Learning | Non-parametric, robust to non-linearities |
| XGBoost | Machine Learning | High-performance with lagged & engineered features |
| LSTM | Deep Learning | Sequence model capturing non-linear dynamics and memory |

---

## Evaluation Framework

- **Walk-forward (rolling-origin) evaluation** to mimic real-time forecasting
- Forecast horizons: short-, medium-, and longer-term (specified per experiment)
- Metrics:
  - RMSE – Root Mean Squared Error  
  - MAE – Mean Absolute Error  
  - MAPE – Mean Absolute Percentage Error  
- **Forecast interval coverage**, where available (e.g. SARIMAX, Prophet, or bootstrapped ML)

---

## Notes on Frequency Alignment

Many macroeconomic indicators are originally observed at monthly or annual frequencies. To ensure comparability and avoid information leakage:

- All series are converted to **quarterly frequency**
- Stock variables and rates: quarterly **mean** or **end-of-period**
- Price indices: quarterly averages, then transformed into inflation measures
- Flow variables: aggregated using appropriate summation or averaging rules

All transformations and alignment choices are explicitly documented in the data preparation notebooks.

---

## Repository Structure

```plaintext
/data/                   → Cleaned and aligned quarterly datasets
/notebooks/              → EDA, feature engineering, modeling, evaluation
/models/                 → Serialized models (where applicable)
/plots/                  → Forecast plots, diagnostics, SHAP explanations
README.md                → Project documentation
requirements.txt         → Reproducible environment setup
