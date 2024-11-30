# Anomaly Detection in Stock Market Data

## Overview
This project focuses on detecting anomalies in stock mearket time series data, utilizing an **Isolation Forest** model. The primary goal is to identify unusual patterns or outliers in stock market data, which may signal significant events, market manipulations, or unexpected trends. The project includes steps like data preprocessing, feature engineering, model training, and visualizing detected anomalies to make insights more actionable.

---

## Project Workflow

1. **Data Preprocessing**: Ensures data is clean, consistent, and ready for analysis.
2. **Feature Engineering**: Enhances the dataset by creating new features for better anomaly detection.
3. **Model Training**: Uses Isolation Forest to learn patterns and identify anomalies.
4. **Visualization**: Highlights anomalies through intuitive plots.
5. **Testing**: Applies the model to unseen data to evaluate its performance.

---

## Preprocessing Steps

### 1. **Loading Data**
- Training and test datasets are loaded from CSV files.
- Column names are standardized by converting them to lowercase.

### 2. **Date Conversion and Sorting**
- The `date` column is converted into a `datetime` format for easier manipulation.
- The dataset is sorted chronologically to maintain the sequence of financial events.

### 3. **Feature Engineering**
Feature engineering is critical for extracting meaningful patterns from raw data. Below are the features derived:
- **Price Range**: `high - low` (daily price movement range).
- **Price Change**: `close - open` (difference between closing and opening prices).
- **Price Change Percentage**: `((close - open) / open) * 100` (percentage change from open to close).
- **Volume Change Percentage**: `((volume_today - volume_yesterday) / volume_yesterday) * 100` (percentage change in trading volume; clipped for extreme values).
- **Moving Averages**: 
  - 5-day moving average of the closing price.
  - 20-day moving average of the closing price.
- **Volatility**: 20-day rolling standard deviation of the closing price, measuring market fluctuation.
- **Relative Strength Index (RSI)**: Computed using the 14-day average gain and loss to evaluate overbought/oversold conditions.

### 4. **Handling Missing Values**
- Missing data is initially forward-filled to propagate previous values.
- Remaining missing values (if any) are filled with zeros to ensure no disruptions.

### 5. **Feature Selection and Scaling**
- Selected features for modeling: `price change percentage`, `volume change percentage`, `price range`, `volatility`, and `RSI`.
- To handle extreme outliers, feature values are clipped to reasonable ranges.
- Features are scaled using **StandardScaler** for normalization, ensuring consistent input for the model.

---

## Model and Hyperparameters

### Isolation Forest Model
The Isolation Forest algorithm is ideal for anomaly detection in high-dimensional datasets due to its efficiency and robustness. The chosen hyperparameters are:
- **Contamination**: Set to `'auto'` to estimate the proportion of anomalies automatically.
- **Random State**: Fixed at `41` to ensure reproducibility of results.
- **n_jobs**: Set to `-1` to leverage all available CPU cores for faster computation.

### Training and Scoring
- The model is trained on the preprocessed and scaled feature set.
- Anomaly scores are computed using the `decision_function` method, with lower scores indicating higher anomaly likelihood.

---

## Features Implemented

### 1. **Data Preprocessing**
- Comprehensive steps to clean, transform, and normalize data.
- Derived several financial features for better anomaly detection.

### 2. **Anomaly Detection**
- Successfully trained an Isolation Forest model to detect anomalies in financial data.
- Model optimally identifies outliers by isolating data points.

### 3. **Visualization**
- Plotted detected anomalies by year to reveal temporal patterns and highlight significant outliers.

### 4. **Test Data Processing**
- Applied the trained Isolation Forest model to unseen test data to obtain a CSV file which contains the anomalies
[Test Result](test_result.csv)

---

## Deployment

The deployment of this project is in progress. It will be hosted on a user-friendly platform 

---

## Datasets

The datasets used in this project are publicly available and can be accessed via the following links:
- [Training Data](https://drive.google.com/file/d/1fPKx6cBvcXJU9VmLqF9PsAsiMabV_swL/view?usp=sharing)
- [Test Data](https://drive.google.com/file/d/1Mp0kfo4woCwpUXtSDlG2FnMSoNcjaLAN/view?usp=sharing)

---








