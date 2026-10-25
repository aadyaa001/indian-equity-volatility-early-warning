# Indian Equity Volatility Early-Warning Model

## Overview

This project investigates whether machine learning models can identify periods of elevated volatility in the Indian equity market using historical NIFTY 50 market data.

The objective is to evaluate whether information from recent returns, volatility, intraday price ranges, and trading volume can help flag elevated volatility over the following five trading sessions.

## Research Question

Can machine learning models provide useful early-warning signals for elevated volatility in the Indian equity market, and how does their performance change across different market periods?

## Data and Features

- **Market:** NIFTY 50
- **Data source:** Yahoo Finance (`^NSEI`)
- **Period:** October 2016–October 2026, subject to data availability
- **Prediction horizon:** Five trading sessions
- **Target:** An indicator for elevated future five-session realized volatility, defined using a threshold learned from the training period.

The features include recent returns, rolling volatility, intraday price ranges, open-to-close returns, volume changes, and additional volatility indicators.

## Models

Three classification models are compared:

1. Logistic Regression
2. Random Forest
3. XGBoost

The evaluation uses chronological data splits and expanding-window walk-forward testing to better reflect the time-dependent nature of financial data.

## Walk-Forward Results

| Model | Mean ROC-AUC | Mean Average Precision |
|---|---:|---:|
| Logistic Regression | 0.6117 | 0.3440 |
| Random Forest | 0.7379 | 0.3721 |
| XGBoost | 0.7298 | 0.3648 |

Random Forest achieved the highest mean ROC-AUC and mean Average Precision across the seven evaluated quarters. XGBoost produced comparable results, while Logistic Regression had lower average performance.

These averages should be interpreted cautiously because the evaluated quarters may differ in market conditions, event prevalence, and sample size.

## Results and Visualizations

- [Walk-forward results (CSV)](walk_forward_results.csv)
- [Model performance summary (CSV)](model_performance_summary.csv)
- [Walk-forward ROC-AUC plot](walk_forward_auc.png)
- [Walk-forward Average Precision plot](walk_forward_average_precision.png)

## Repository Contents

- `Indian_Equity_Volatility_Model.ipynb` — analysis, feature engineering, model training, and evaluation.
- `walk_forward_results.csv` — quarterly model evaluation results.
- `model_performance_summary.csv` — summary metrics across evaluated quarters.
- `walk_forward_auc.png` — ROC-AUC comparison over time.
- `walk_forward_average_precision.png` — Average Precision comparison over time.

## Limitations

- Financial markets experience regime changes, so model performance may vary over time.
- High-volatility events may be relatively rare, making accuracy alone an inadequate evaluation metric.
- Average results across quarters can conceal substantial differences in performance.
- The evaluated period has already been inspected during development and should not be treated as a completely untouched final test set.
- Predictive performance in historical data does not guarantee future trading performance or profitability.

## Reproducibility

The notebook is designed to run in Google Colab. Run the cells from top to bottom to reproduce the analysis and generate the evaluation outputs. Results may vary if the underlying data source changes.

##
