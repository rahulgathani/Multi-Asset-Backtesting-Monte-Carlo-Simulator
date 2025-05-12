🧠 Multi-Asset Backtesting and Volatility Analysis

🚀 Project Overview
Multi-Asset Backtesting and Volatility Analysis is a full-scale quantitative research and strategy engineering framework implemented in Python. The project integrates a wide range of financial instruments — including equities, ETFs, and volatility indices — to conduct multi-dimensional portfolio analysis, volatility modeling, signal-based backtesting, factor regression, and allocation strategy evaluation. The design emphasizes modularity, data transparency, and extensibility within a Jupyter Notebook environment using only open-source tools. The framework incorporates real-time data pipelines, rolling statistical computation, signal logic construction, and performance diagnostics. It is intended for use cases involving tactical allocation modeling, volatility-based strategy design, and macro-factor-based return attribution.

✅ What This Project Demonstrates
Multi-asset financial data ingestion and validation
Preprocessing pipelines for price, return, and volatility data
Log return transformation and cumulative return computation
Rolling historical volatility estimation and volatility spread analysis
Implied volatility skew modeling across options strikes
Signal-based trading logic using simple and custom SMA crossovers
Daily backtesting with equity curve and signal capture
Statistical regression modeling with Fama-French and Momentum factors
Construction of optimized portfolios using advanced allocation schemes
Generation of clean, structured tabular outputs and visualizations

🧱 Key Modules & Workflow
📥 Data Acquisition & Preparation
Sources:
Yahoo Finance via yfinance (auto-adjusted for splits/dividends)

Assets Covered:
Equities: AAPL, MSFT, AMZN, GOOGL, JPM, TSLA
ETFs: SPY, QQQ, TLT, GLD, VNQ, DBC
Volatility Index: ^VIX

Parameters:
Customizable start and end dates
Ticker list can be modified per use case

Validation:
Display of last 5 rows of fetched price data
Summary views to verify ticker alignment and column structure

🧹 Data Processing
Handling:
Price alignment across multiple tickers
NaN removal and edge trimming for synchronization

Return Calculation:
Log returns for each asset
Cumulative log return series derived
Data indexed by business day for consistency

📊 Volatility Analysis
Historical Volatility (HV):
Rolling standard deviation calculation on daily log returns
Output formatted as ticker-specific volatility series

Implied Volatility (IV) Skew:
Static IV values estimated at 90%, 100%, and 110% strikes
Skew DataFrame constructed per ticker

Volatility Spread:
Defined as HV - IV per asset
Tracked over rolling windows and displayed in tabular form
Volatility outputs are plotted using matplotlib and stored in time series format

📈 Signal Generation & Backtesting
Logic:
Short and Long Simple Moving Averages (SMA) applied to SPY and ^VIX
Signal = 1 when Short MA > Long MA, else 0

Execution Framework:
Signals used to simulate buy/sell logic on price series
Daily positions derived based on active signals

Output Tables:
SPY_Short_MA, SPY_Long_MA, SPY_Signal, VIX_Short_MA, VIX_Long_MA, VIX_Signal
Strategy-level cumulative value tracking (SPY_Cumulative, ^VIX_Cumulative)

Portfolio Value Table:
Combined daily portfolio value for SPY, VIX, or any custom selection

Visualizations:
Strategy equity curve
Signal overlay on price series

🔬 Factor-Based Attribution
Inputs:
Strategy excess returns
Fama-French 3-Factor Data and Momentum (loaded from CSV or API)

Model:
OLS Regression: Excess_Returns ~ Mkt-RF + SMB + HML + Momentum
Statistical evaluation with standard errors, t-values, and R-squared
HAC (heteroskedasticity and autocorrelation consistent) covariance used

Output:
Coefficients and significance levels
Clean regression summary table

💼 Portfolio Construction & Optimization
Allocation Strategies:
Risk Parity: Weights scaled inversely to asset volatility
Minimum Volatility: Portfolio with lowest overall variance
Maximum Diversification: Maximizes ratio of diversification benefit

Process:
Volatility/covariance matrix derived from return history
Optimization logic applied to compute weights

Output Tables:
Asset weights per model
Portfolio return, volatility, and Sharpe per strategy

Strategy Simulation:
Daily performance tracking using generated weights
Portfolio equity curve output per model

Optional: Optimal MA window selection based on Sharpe ratio scanning

📊 Structured Output Views
Final 5-day snapshots for:
Validated market data
Historical Volatility (HV)
Volatility Spread (HV - IV)
Implied Volatility Skew
Trading Signals (SPY and ^VIX)
Portfolio Value Tables

Rolling Plots:
Volatility series
Correlation matrices
Strategy vs benchmark comparison

🧰 Tech Stack
Language: Python
Data & Math: pandas, numpy, yfinance
Statistical Modeling: statsmodels
Visualization: matplotlib, seaborn
Environment: Jupyter Notebook
Optional Extensions: pyfolio, ffn, scikit-learn

📃 License
This project is provided under the MIT License. All code and data usage is intended for open-source research, academic learning, and professional development.
