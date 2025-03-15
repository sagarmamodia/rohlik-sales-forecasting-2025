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

The performance of the predictions is evaluated using the Weighted Mean Absolute Error (WMAE). The formula for WMAE is:

WMAE=∑i=1nwi×∣yi−y^i∣∑i=1nwiWMAE=∑i=1n​wi​∑i=1n​wi​×∣yi​−y^​i​∣​

Where:

    nn is the number of predictions.
    wiwi​ is the weight for the ii-th prediction, provided in test_weights.csv.
    yiyi​ is the actual sales value.
    y^iy^​i​ is the predicted sales value.

Methodology

Our approach to forecasting involved the following steps:

    Data Preprocessing: Cleaning and preparing the data by handling missing values and merging datasets to enrich features.
    Feature Engineering: Creating additional features such as:
        Temporal features (e.g., day of the week, month).
        Lag features to capture sales trends over time.
        Encoding categorical variables like warehouse and product categories.
    Model Selection: Evaluating various models, including:
        XGBoost: Selected for its superior performance in capturing complex patterns in the data.
        LightGBM: Considered but found to be less effective in this context.
        Deep Neural Networks: Explored but required extensive computational resources without significant performance gains.
    Validation Strategy: Due to computational constraints, a manual selection of validation periods was employed to simulate future sales scenarios.
    Hyperparameter Tuning: Conducted extensive tuning to optimize model performance.

Results

    Best WMAE Achieved: 19.63
    Leaderboard Rank: 164th out of 777 participants
    Performance Comparison: Our WMAE was 1.8 points higher than the 4th place result in the competition.
