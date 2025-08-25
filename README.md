# US YoY Inflation Forecasting

This project forecasts U.S. year-over-year inflation using CPI data from the Federal Reserve Bank of St. Louis (FRED).

## Files
- **forecasting.ipynb** – Main notebook containing model training, evaluation, and forecasting pipeline.
- **cpi_monthly.csv** – Monthly CPI data obtained from FRED (required to run the notebook).

## Methodology
1. **Data Preparation**
   - Import monthly CPI data from FRED.
   - Engineer lag features and seasonal terms.
   - Scale features as needed for model training.

2. **Model Training & Evaluation**
   - Tested five models: LightGBM, Simple RNN, Deep Neural Network (DNN), LSTM, and an Ensemble method.
   - Models were evaluated on the last two years of data.

3. **Feature Imputation**
   - Time-series models were built to impute future values of key features (required for forecasting).

4. **Final Forecast**
   - The best-performing model was an ensemble of the top three models, with predictions weighted by inverse MAE and normalized using a softmax-like function to balance weights.
   - The final ensemble model was retrained on the full dataset and used to generate forecasts with imputed features.

## Results
- The ensemble method produced the most accurate and stable forecasts.
- Predictions closely align with the July 2025 CPI report, supporting the model’s validity in the near term.
