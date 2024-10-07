# Options Pricing Model with Black-Scholes

This project implements an options pricing model using the Black-Scholes formula in Python. It fetches historical stock data and options data, calculates option prices and Greeks, and visualizes the results.

## Table of Contents

- [Features](#features)
- [How It Works](#how-it-works)
- [Usage](#usage)
- [Requirements](#requirements)
- [License](#license)

## Features

- Fetch historical stock and options data using `yfinance`.
- Implement the Black-Scholes model for call and put option pricing.
- Calculate option Greeks: Delta, Gamma, Theta, Vega, and Rho.
- Visualize stock price trends and option price sensitivities using `matplotlib`.

## How It Works

1. **Data Fetching**: 
   - The `fetch_options_data` function retrieves call and put options data for a given ticker symbol.
   - The `fetch_stock_data` function fetches historical stock price data from Yahoo Finance.

2. **Black-Scholes Model**:
   - The `BlackScholesModel` class computes the prices of call and put options based on the underlying asset price, strike price, time to expiration, risk-free interest rate, and volatility.
   - The `BlackScholesGreeks` class extends the model to calculate various Greeks, which measure the sensitivity of option prices to different factors.

3. **Historical Volatility**: 
   - The `calculate_historical_volatility` function computes the historical volatility of a stock based on its closing prices.

4. **Visualizations**:
   - The project uses `matplotlib` to plot historical stock prices and the sensitivity of option prices to various parameters.

## Usage

To use the options pricing model, simply run the provided code. Here is an example of how to fetch data for NVIDIA (NVDA) and compute option prices:

```python
nvda_calls, nvda_puts = fetch_options_data('NVDA')
nvda_stock_data = fetch_stock_data('NVDA')

bsm = BlackScholesModel(S=100, K=100, T=1, r=0.05, sigma=0.2)
print(f"Call Option Price: {bsm.call_option_price()}")
print(f"Put Option Price: {bsm.put_option_price()}")
