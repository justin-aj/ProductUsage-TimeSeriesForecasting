ProductUsage-TimeSeriesForecasting

📖 Overview
This repository hosts a Jupyter Notebook for time series forecasting of product usage data, predicting usage quantities over a future period. The pipeline includes data validation, preprocessing, visualization, feature engineering, model training, evaluation, and forecasting using multiple models. The dataset (not included) is expected to contain weekly usage records for multiple entities.
🎯 Objectives

Validate and preprocess time series data for quality and consistency.
Visualize trends, missing values, and outliers for each entity.
Develop and compare forecasting models: ARIMA, Linear Regression, Random Forest, and XGBoost with Cross-Validation.
Forecast usage quantities for a specified future period.
Identify the best-performing model per entity using MAE, RMSE, and MAPE metrics.

📊 Dataset
The dataset (not included) should contain weekly usage records with the following columns:

Entity Identifier: Unique ID for each entity.
Week-Ending Date: Date marking the end of the week.
Total Usage Quantity: Total usage for the week.
Subcategory Usage Quantity (optional): Usage for a specific product type.

🛠️ Methodology
1. Data Validation

Check for null identifiers, duplicate identifier-week combinations, invalid date formats, and inconsistent week-ending dates.
Validate numerical columns for non-numeric values, negative values, and logical consistency (e.g., subcategory usage ≤ total usage).
Identify gaps in weekly data for each entity.

2. Data Preprocessing

Convert date columns to datetime and numerical columns to float, handling non-numeric values as NaN.
Forward-fill missing values for entities with ≤10% missing data.
Cap outliers using the IQR method (1.5 * IQR bounds) to maintain time series continuity.

3. Data Visualization

Plot missing value timelines to identify data gaps.
Visualize outliers over time for each entity.
Plot total usage trends across entities to detect patterns.

4. Feature Engineering

Create lagged features (3 lags) for regression-based models to capture temporal dependencies.
Split data into training and testing sets based on a cutoff date.

5. Model Training
Four models are trained and evaluated:

ARIMA: Time series model assuming stationarity after differencing.
Linear Regression: Baseline model using lagged features.
Random Forest Regressor: Non-linear model with 100 estimators.
XGBoost with Cross-Validation: Optimized using GridSearchCV over hyperparameters (n_estimators, learning_rate, max_depth, subsample).

6. Model Evaluation

Metrics: Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), Mean Absolute Percentage Error (MAPE).
Best model selected per entity based on lowest MAE, with RMSE and MAPE as tiebreakers.

7. Inference

Forecast usage quantities for a specified future period using the best model for each entity.
Visualize forecasts alongside training and test data.

🚀 Installation
Prerequisites

Python 3.8+
Jupyter Notebook
Required libraries listed in requirements.txt

Setup

Clone the repository:git clone https://github.com/yourusername/ProductUsage-TimeSeriesForecasting.git
cd ProductUsage-TimeSeriesForecasting


Install dependencies:pip install -r requirements.txt


Place your dataset (e.g., usage_data.xlsx) in the project root directory.
Launch Jupyter Notebook:jupyter notebook



📈 Usage

Open forecasting.ipynb in Jupyter Notebook.
Run all cells to execute the pipeline, which will:
Load and validate the dataset.
Preprocess data (handle missing values, cap outliers).
Generate visualizations for missing values, outliers, and trends.
Train and evaluate ARIMA, Linear Regression, Random Forest, and XGBoost models.
Produce and visualize forecasts for the specified future period.


Outputs:
Visualizations displayed inline in the notebook.
Forecast results stored in a dictionary.
Model performance metrics printed in the notebook.



📁 Project Structure
ProductUsage-TimeSeriesForecasting/
├── forecasting.ipynb         # Jupyter Notebook with the full pipeline
├── requirements.txt          # List of Python dependencies
└── README.md                 # Project documentation


Note: The dataset is not included in the repository. Ensure it is placed in the root directory before running the notebook.

🔮 Next Steps

Cyclical Features: Encode day-of-week and week-of-year using sine/cosine transformations to capture seasonality.
Rolling Statistics: Include rolling mean, standard deviation, min, and max for past weeks to capture trends and volatility.
Advanced Models: Experiment with Prophet, SARIMA, or LSTM for improved forecasting.
Auto ARIMA: Use pmdarima.auto_arima to automatically select optimal ARIMA parameters.
Hyperparameter Tuning: Extend GridSearchCV to Linear Regression and Random Forest models.
Subcategory Forecasting: Apply the pipeline to subcategory usage data.
External Data: Incorporate external data (e.g., weather, events) for additional context.
Deep Learning: Explore LSTM models for longer time series data.

📜 License
This project is licensed under the MIT License.
