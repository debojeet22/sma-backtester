# SMA Crossover Backtester

A Python-based backtesting engine for Simple Moving Average (SMA) crossover 
trading strategies using historical stock/index data.

## What it Does
Tests a classic quant trading strategy — when the short-term SMA crosses above 
the long-term SMA, go long. When it crosses below, go short.
Compares strategy performance against a simple Buy & Hold benchmark.

## Features
- 📈 Fetches live historical data via yFinance
- ⚡ SMA crossover signal generation (long/short positions)
- 📊 Strategy vs Buy & Hold performance comparison
- 📉 Cumulative returns visualization
- 🔢 Annualized volatility calculation

## How to Use

### Install Dependencies
pip install numpy yfinance matplotlib pandas

### Run the Backtester
from smabacktest import SMABacktester

# Example: Test on Reliance with SMA 50 vs SMA 200
bt = SMABacktester('RELIANCE.NS', SMA_S=50, SMA_L=200, 
                    start='2020-01-01', end='2024-01-01')

performance, outperformance = bt.test_results()
print(f"Strategy Return: {performance}")
print(f"Outperformance vs Buy & Hold: {outperformance}")

bt.plot_results()

## Parameters
| Parameter | Description              | Example        |
|-----------|--------------------------|----------------|
| symbol    | Stock ticker             | 'RELIANCE.NS'  |
| SMA_S     | Short SMA window (days)  | 50             |
| SMA_L     | Long SMA window (days)   | 200            |
| start     | Start date               | '2020-01-01'   |
| end       | End date                 | '2024-01-01'   |

## Strategy Logic
- Position = +1 (Long)  → when SMA_S > SMA_L
- Position = -1 (Short) → when SMA_S < SMA_L
- Returns calculated using log returns for accuracy

## Tech Stack
Python, NumPy, Pandas, yFinance, Matplotlib

## Author
debojeet22
