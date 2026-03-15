

# ML Momentum Trading Strategy

### IIT Mandi Hackathon Submission

Machine learning–driven **long-only momentum trading strategy** that predicts stock momentum and constructs a portfolio using an ensemble of classifiers.

The project implements a **complete quant pipeline**:

![Dashboard](Images(visualization)/dashboard%20(1).png)

```
Data Collection → Feature Engineering → ML Models → Backtesting → Performance Metrics → Visualization
```
### Strategy Explanation

This project implements a machine learning–based long-only weekly momentum strategy applied to 10 US equities.

The strategy uses daily OHLCV data (2017–2025) and predicts the probability of positive weekly returns using an ensemble of Logistic Regression, Random Forest, and XGBoost models.

### 1. Data Collection

Daily **OHLCV data (2017–2025)** is downloaded for the following 10 US equities using **yfinance**:

* AAPL
* MSFT
* GOOGL
* AMZN
* META
* TSLA
* JPM
* V
* JNJ
* BRK-B

---

### 2. Feature Engineering

A total of **31 weekly features** are computed for each stock, including:

* Momentum returns (1–52 weeks)
* Moving average ratios (MA10–MA200)
* RSI-14
* MACD
* Realized volatility
* Bollinger Band position
* Volume ratios

These indicators capture **trend strength, volatility patterns, and market momentum behavior**.

---

### 3. Weekly Dataset Construction

Daily data is converted into a **weekly panel dataset**.

Each row represents:

```
(stock, week)
```

with engineered features and the **next-week return label**.

---

### 4. Target Variable

A **binary classification target** is defined:

* **1 → next week return > 0**
* **0 → next week return ≤ 0**

---

### 5. Model Training

Three machine learning models are trained:

* Logistic Regression
* Random Forest (300 trees)
* XGBoost

---

### 6. Ensemble Prediction

The predictions from the three models are combined using a **soft-voting ensemble**.

The ensemble outputs the **probability of a positive return in the next week** for each stock.

---

### 7. Stock Ranking

Each week, all stocks are **ranked by predicted probability**.

---

### 8. Portfolio Selection

The **top 2 highest-probability stocks** are selected.

---

### 9. Portfolio Allocation

Capital is allocated using an **equal-weight strategy**:

* 50% in stock 1
* 50% in stock 2

The strategy is **long-only**.

---

### 10. Rebalancing

The portfolio is **rebalanced weekly** using updated model predictions.

---

### 11. Transaction Costs

Realistic trading costs are applied:

* **0.1% at entry**
* **0.1% at exit**

Total trading cost = **0.2% round-trip per week**.

---

### 12. Backtesting

The strategy is evaluated using a **time-based split**:

| Period      | Description           |
| ----------- | --------------------- |
| 2017–2022   | Training data         |
| 2023–2025   | Out-of-sample testing |
| Test length | 109 weeks             |

---

### 13. Walk-Forward Retraining

To adapt to market changes, models are **retrained every 26 weeks** using new data.

---

### 14. Performance Evaluation

Strategy performance is evaluated using standard financial metrics:

* Cumulative Return
* Annualized Return
* Volatility
* Sharpe Ratio
* Maximum Drawdown
* Hit Rate

---

### 15. Final Results (After Transaction Costs)

| Metric                | Value     |
| --------------------- | --------- |
| Net Cumulative Return | **49.3%** |
| Annualized Return     | **21.1%** |
| Sharpe Ratio          | **1.189** |

These results indicate **predictive power in cross-sectional momentum signals** and demonstrate the effectiveness of the machine-learning ensemble strategy.

---

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




The script will:

1. Download stock data
2. Generate features
3. Train ML models
4. Run backtest
5. Generate charts
6. Save portfolio predictions

---

# Performance Metrics

Key evaluation metrics:

* cumulative return
* annualized return
* volatility
* Sharpe ratio
* ROC-AUC
* accuracy

---


# Author

Hackathon Submission —
Indian Institute of Technology Mandi

**Shadab Firoz**

---


