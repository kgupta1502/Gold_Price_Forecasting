# Gold Price Forecasting & Market Efficiency Analysis

[![Python](https://img.shields.io/badge/Python-3.12-blue.svg)](https://www.python.org/)
[![Framework](https://img.shields.io/badge/Theory-Efficient%20Market%20Hypothesis-orange)](https://en.wikipedia.org/wiki/Efficient-market_hypothesis)

An empirical quantitative evaluation of daily gold futures (`GC=F`) historical prices to test the **Weak-Form Efficient Market Hypothesis (EMH)** using univariate time-series modeling (ARIMA).

## Executive Summary & Key Findings
* **The Core Question:** Can historical daily gold closing prices be modeled to beat a basic random-walk baseline?
* **The Verdict:** Consistent with the Weak-Form EMH, an **ARIMA(0,1,0)** model (a random walk with a single variance term) performs exactly as well as complex autoregressive parameters for one-step-ahead forecasting.
* **Key Statistical Insights:**
  * Residual diagnostics reveal high kurtosis (8.25) and significant heteroskedasticity ($Prob(H) = 0.00$), pointing directly toward volatility clustering. 
  * While one-step forecasting achieves a tight Mean Absolute Percentage Error (MAPE), multi-step forecasting rapidly degrades (1.01% vs 31.30% MAPE), highlighting the boundaries of univariate autoregressive price history.

## Tech Stack & Methodology
* **Data Ingestion:** Automated daily historical quotes pulling from COMEX via `yfinance`.
* **Statistical Tools:** Augmented Dickey-Fuller (ADF) test for stationarity, ACF/PACF plots for order determination, and `statsmodels` for ARIMA execution.
* **Validation:** Explicit 80/20 temporal train/test split ensuring zero lookahead bias.

## Project Workflow
1. **Data Collection & Stationarity Testing:** Importing COMEX data and running ADF transformations.
2. **Model Identification:** Analyzing autocorrelation bounds to determine parameters.
3. **Forecasting & Validation:** One-step-ahead vs. multi-step evaluation against real out-of-sample data.
4. **Residual Diagnostics:** Testing for normalized white noise and heteroskedasticity.

##  How to Run the Project
1. Clone this repository:
   ```bash
   git clone [https://github.com/kgupta1502/Gold_Price_Forecasting.git](https://github.com/kgupta1502/Gold_Price_Forecasting.git)"# Gold_Price_Forecasting" 
