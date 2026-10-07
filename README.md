# Forecasting Florida Home Values

This capstone uses monthly Zillow Home Value Index (ZHVI) data to predict Florida's next monthly typical home value. The project began with a broader real estate investment question, but the available dataset supports a more focused forecasting problem rather than a full valuation model.

## Main result

Ridge regression produced the lowest mean absolute error during expanding-window cross-validation. On the independent January 2021-January 2026 holdout period, it achieved:

- MAE: **$886**
- RMSE: **$1,268**
- MAPE: **0.25%**
- R-squared: **0.999**
- MAE improvement over a prior-month persistence baseline: **67.6%**

The linear regression model scored even lower error on the holdout period, but ridge regression remains the selected model because the selection decision was made using cross-validation rather than the final test data.

## Repository contents

- `notebooks/01_Data_Wrangling_EDA.ipynb`: data checks, cleaning decisions, and exploratory analysis
- `notebooks/02_Modeling.ipynb`: leakage-safe feature engineering, time-series validation, tuning, model comparison, and residual review
- `model_metrics.csv`: model parameters and performance metrics
- `models/final_ridge_model.joblib`: fitted final pipeline and feature list
- `results/holdout_predictions.csv`: actual and predicted holdout values
- `figures/`: exported analysis figures
- `Capstone_Two_Final_Report.pdf`: written project report
- `Capstone_Two_Final_Presentation.pptx`: presentation deck

## Reproduce the analysis

Create a Python environment and install the packages in `requirements.txt`. Run the notebooks in order from the `notebooks` folder. Each notebook uses paths relative to that folder.

```bash
pip install -r requirements.txt
jupyter notebook
```

## Data

The repository contains a course-project snapshot of monthly state-level ZHVI data from January 2000 through January 2026. The original notebook identified Kaggle as the download location but did not preserve the exact Kaggle page. Zillow is the underlying publisher. Zillow describes ZHVI as a measure of the typical home value and market changes for a region and housing type.

- Zillow Research housing data: https://www.zillow.com/research/data/
- Zillow public data terms require clear attribution to Zillow.

## Important limitations

- ZHVI is an index of typical state-level home value, not a property sale-price dataset.
- The model forecasts one month ahead and uses only past ZHVI values.
- State-level ZHVI alone cannot identify an undervalued investment market.
- Investment analysis would also need rent, income, inventory, population or migration, mortgage rates, and more local geography.

## Author

Michael McCue

