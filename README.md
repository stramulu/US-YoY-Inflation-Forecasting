# US YoY Inflation Forecasting

This project forecasts U.S. year-over-year inflation using CPI data from the Federal Reserve Bank of St. Louis (FRED).

## Files
- **forecast.ipynb** – Main notebook containing model training, evaluation, and forecasting pipeline.
- **cpi_monthly.csv** – Monthly CPI data obtained from FRED (required to run the notebook).
- **requirements.txt** – List of libraries to install for project to run

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

## Quick View

If you only want to **see the forecasts and outputs**, you don’t need to install anything.  
Simply open [`forecast.ipynb`](./forecast.ipynb) in GitHub — all results, plots, and explanations are saved in the notebook itself.

## How to Run

1. Clone the repository and navigate into the project folder:

   ```bash
   git clone https://github.com/your-username/US-YoY-Inflation-Forecasting.git
   cd US-YoY-Inflation-Forecasting
   
2. Create and activate a virtual environment (recommended):

   ```bash
   python3.10 -m venv venv
   source venv/bin/activate   # On macOS/Linux
   venv\Scripts\activate      # On Windows

3. Install dependencies:

   ```bash
   pip install -r requirements.txt

4. Run the cells in forecast.py step by step to reproduce the results.

5. For mac users with an M1 chip or later:

   Replace:

      ```bash
      tensorflow==2.15.0
      ```
      
   With:
   
      ```bash
      tensorflow-macos==2.15.0
      tensorflow-metal==1.1.0
      ```

   in the requirements.txt file
