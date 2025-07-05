# Benchmark-Models
#INSTRUCTIONS:
#NOTE: Data is given in three parts in this github repo. Join and sort by permno and date. 

Benchmark Model Evaluation for Financial Risk Forecasting

You are given a stock return dataset (S&P-500-Stratified-99.csv) containing daily returns and covariates for multiple stocks (permno) over time (date). Your goal is to implement three benchmark models to forecast 1-day-ahead financial risk and evaluate them using standard risk metrics.

🔧 Step 1: Model Implementation
Implement the following benchmark models:

GARCH(1,1) per stock:

Fit rolling GARCH(1,1) on ret_t using a 500-day window.

Assume normally distributed innovations.

Output:

VaR_95: 5% one-day-ahead Value-at-Risk.

ES_95: Expected Shortfall at 5%.

actual_return: realized return the next day.

Historical Simulation (HS):

Rolling 250-day window of historical returns.

Compute empirical 5% quantile (VaR_95) and conditional average below it (ES_95).

Rolling Quantile Regression (QR):

Use covariates (excluding any non-numeric like industry) to fit 5% quantile regression.

Rolling window: 500 days.

Estimate conditional quantile for VaR and use empirical residuals for ES.

Save all outputs as DataFrames with columns:

css
Copiar
Editar
['permno', 'date', 'actual_return', 'VaR_95', 'ES_95', 'model']
📏 Step 2: Risk Evaluation Metrics
Compute the following per model:

VaR Coverage:

Proportion of times actual_return < VaR_95.

ES Error:

Mean absolute error between actual_return and ES_95 only for violations (i.e., when return < VaR).

VaR Backtesting (Kupiec & Christoffersen tests):

Unconditional Coverage Test (LR_uc).

Independence Test (LR_ind).

Conditional Coverage Test (LR_cc).

Report test statistics and p-values.
