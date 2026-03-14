

# ML Momentum Trading Strategy

### IIT Mandi Hackathon Submission

Machine learning–driven **long-only momentum trading strategy** that predicts stock momentum and constructs a portfolio using an ensemble of classifiers.

The project implements a **complete quant pipeline**:

```
Data Collection → Feature Engineering → ML Models → Backtesting → Performance Metrics → Visualization
```

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

![Image](https://s3.tradingview.com/x/xEMoClat_mid.png?v=1773099757)

![Image](https://kjtradingsystems.com/uploads/3/4/0/2/34026855/eqcurvefig3_orig.jpg)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2A6C_96mQbFVmZOvZ7NxXQrA.jpeg)

![Image](https://www.researchgate.net/publication/350424838/figure/fig4/AS%3A1005840190423052%401616822397205/Equity-curves-of-the-long-short-and-combined-models-of-the-PMS-The-left-and-right.png)

---

### chart_features.png

Shows **momentum indicators and engineered features** used for training the models.

Examples:

* 1-month momentum
* 3-month momentum
* 6-month momentum
* volatility signals

![Image](https://s3.tradingview.com/v/VBOn1TYA_mid.png?v=1772808681)

![Image](https://images.openai.com/static-rsc-3/IVRqs6e0oVotVJZJZqu_-ckw1vzY_uSPRl5YUmqS2vJThnMrYCwP31nlw0g1BZ6tb9q1iC-m-jWCasbPgut1PVERtzpDzlzztt7e30609-c?purpose=fullsize\&v=1)

![Image](https://miro.medium.com/1%2AUxAkShUgqQAw4N1AHgdwvw.png)

![Image](https://www.tandfonline.com/cms/asset/b9cab001-3c99-4517-81f4-6ec53911dd85/rero_a_2089192_f0004_c.jpg)

---

### feature_importance.png

Displays **model feature importance** showing which variables contributed most to predictions.

Generated from tree-based models.

![Image](https://www.researchgate.net/publication/332635798/figure/fig2/AS%3A11431281210587685%401702059714039/Feature-importance-bar-plot-based-on-XGBoost.tif)

![Image](https://miro.medium.com/1%2A-GGDhUQV8ZTzsiSR8iEfWQ.png)

![Image](https://www.researchgate.net/publication/384906590/figure/fig5/AS%3A11431281283782618%401728960927363/a-Feature-importance-visualization-for-the-ANN-model-The-bar-chart-displays-the-mean.png)

![Image](https://www.researchgate.net/publication/395458586/figure/fig3/AS%3A11431281635042831%401757757170431/Machine-learning-feature-importance-results-The-bar-chart-illustrates-the-feature_Q320.jpg)

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

# Installation

Install dependencies:

```bash
pip install numpy pandas scikit-learn xgboost yfinance matplotlib
```

---

# Run the Project

```bash
python main.py
```

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


