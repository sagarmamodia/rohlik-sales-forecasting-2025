This repository contains our submission for the Rohlik Sales 2025 Forecasting Challenge. The objective of this challenge is to predict the sales volume for specific inventory items across various warehouses over a given period, utilizing historical sales data and additional provided datasets.

## Repository Structure

* sales_train.csv: Historical sales data for training the model.
* sales_test.csv: Dataset for which sales predictions are to be made.
* inventory.csv: Information about inventory items, including product details and warehouse associations.
* calendar.csv: Calendar data indicating holidays and warehouse-specific events.
* solution.csv: The submission file containing our sales predictions.

## Submission File Format (solution.csv)

The solution.csv file contains our sales forecasts and adheres to the following structure:

* id: Composite identifier combining unique_id and date (e.g., 1226_2024-06-03).
* sales: Predicted sales volume for the corresponding id.

Note: The id is constructed by concatenating the unique_id and date with an underscore.
Evaluation Metric

## Evaluation Metric
The performance of the predictions is evaluated using the Weighted Mean Absolute Error (WMAE). The formula for WMAE is:

$$\text{WMAE} = \frac{ \sum_{i=1}^{n} w_i \times |y_i - \hat{y}\_i|}{ \sum_{i=1}^{n} w_i}$$

Where:

* $n$ is the number of predictions.
* $w_i​$ is the weight for the i-th prediction, provided in test_weights.csv.
* $\hat{y}\_i$​ is the actual sales value.
* $y_i$ is the predicted sales value.

## Methodology

Our approach to forecasting involved the following steps:

* Data Preprocessing: Cleaning and preparing the data by handling missing values and merging datasets to enrich features.
* Feature Engineering: Creating additional features such as:
    * Temporal features (e.g., day of the week, month).
    * Lag features to capture sales trends over time.
    * Encoding categorical variables like warehouse and product categories.
* Model Selection: Evaluating various models, including:
    * XGBoost: Selected for its superior performance in capturing complex patterns in the data.
    * Ensemble: Multiple ensembles of XGBoost model were trained and evaluated.
* Validation Strategy: Due to computational constraints, a manual selection of validation periods was employed to simulate future sales scenarios.

## Results

 Best Public WMAE Achieved: 20.573  
 Best Private WMAE Achieved: 20.717    
 Leaderboard Rank: 284th out of 777 participants
