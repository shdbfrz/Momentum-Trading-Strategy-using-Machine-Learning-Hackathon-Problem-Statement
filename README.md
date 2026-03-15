

# ML Momentum Trading Strategy

### IIT Mandi Hackathon Submission

Machine learning–driven **long-only momentum trading strategy** that predicts stock momentum and constructs a portfolio using an ensemble of classifiers.

The project implements a **complete quant pipeline**:

```
Data Collection → Feature Engineering → ML Models → Backtesting → Performance Metrics → Visualization
```
 Strategy Explanation
 
A machine learning-based long-only weekly momentum strategy applied to 10 US equities (AAPL, MSFT, GOOGL, AMZN, META, TSLA, JPM, V, JNJ, BRK-B) using daily OHLCV data from 2017 to 2025.
Feature Engineering: 31 features per stock per week — including momentum signals (1w to 52w), moving average ratios (MA10 to MA200), realised volatility, RSI-14, MACD, Bollinger Band position, and volume ratios.
Model: A soft-voting ensemble of Logistic Regression, Random Forest (300 trees), and XGBoost predicts the probability of a positive next-week return for each stock. The top-2 ranked stocks are selected each week.
Portfolio: Equal-weight (50% each), long-only, rebalanced weekly. Transaction cost of 0.1% at entry and 0.1% at exit (0.2% round-trip per week) is applied.
Validation: Trained on 2017–2022 (2,600 samples), tested out-of-sample on 2023–2025 (109 weeks). Walk-forward retraining was also implemented (every 26 weeks), achieving 15.3% annualised return with a Sharpe of 0.811.
Result: The strategy delivers a net cumulative return of 49.3% and net annualised return of 21.1% with a Sharpe ratio of 1.189 over the test period, confirming genuine predictive signal in cross-sectional momentum.
---

# Repository Structure

```
project/
│
├── Momentumstrategy.ipynb
|
│
├
│
├── chart_features.png
├── dashboard.png
├── feature_importance.png
│
└── weekly_predictions_portfolio.csv
```

---

# Output Files Explanation

### dashboard.png

Main performance dashboard showing:

* cumulative returns
* strategy vs benchmark
* portfolio growth
* risk metrics



---

### chart_features.png

Shows **momentum indicators and engineered features** used for training the models.

Examples:

* 1-month momentum
* 3-month momentum
* 6-month momentum
* volatility signals


---

### feature_importance.png

Displays **model feature importance** showing which variables contributed most to predictions.

Generated from tree-based models.





---

### weekly_predictions_portfolio.csv

This file contains **model predictions and portfolio allocations**.

Typical columns include:

| Column      | Description           |
| ----------- | --------------------- |
| date        | prediction date       |
| stock       | ticker symbol         |
| prediction  | model prediction      |
| probability | predicted probability |
| weight      | portfolio allocation  |

---
![Image]("C:\Users\shdbf\Downloads\chart3_analysis.png")
# Models Used

The ensemble combines:

* Logistic Regression
* Random Forest
* XGBoost

These models are combined using **VotingClassifier** for stronger prediction stability.

---

# Data Source

Stock data is downloaded using:

* yfinance

Universe includes:

AAPL, MSFT, GOOGL, AMZN, META, TSLA, JPM, V, JNJ, BRK.B

---

![Analysis Chart](images/chart3_analysis.png)


The script will:

1. Download stock data
2. Generate features
3. Train ML models
4. Run backtest
5. Generate charts
6. Save portfolio predictions

---
![Image]("C:\Users\shdbf\Downloads\chart2_heatmap.png")
# Performance Metrics

Key evaluation metrics:

* cumulative return
* annualized return
* volatility
* Sharpe ratio
* ROC-AUC
* accuracy
![Image]("C:\Users\shdbf\Downloads\dashboard(1).png")
---


# Author

Hackathon Submission —
Indian Institute of Technology Mandi

**Shadab Firoz**

---


