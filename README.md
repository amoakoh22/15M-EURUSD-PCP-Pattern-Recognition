# XAUUSD Price Change Pattern (PCP) Prediction using Machine Learning

## Project Overview

This project aims to predict the Price Change Pattern (PCP) of XAUUSD (Gold vs. US Dollar) using a machine learning model built with TensorFlow Keras. The PCP is a deterministic pattern identified based on the relationship between the High and Low prices of three consecutive periods (in this case, 15-minute intervals). The model is trained to classify the PCP into two categories: Bullish (potential price increase) and Bearish (potential price decrease).

## Data Source

The project uses historical XAUUSD M15 (15-minute) data loaded from a CSV file located in Google Drive. 
The data includes Open, High, Low, Close, and Volume for each 15-minute interval.

## Methodology

1. **Data Acquisition:** The XAUUSD_M15.csv file is read into a pandas DataFrame.
2. **Data Cleaning & Preprocessing:**
    - Column names are cleaned.
    - Date and Time columns are combined into a single Datetime column.
    - Missing data is removed.
3. **PCP Labeling:** A function `label_pcp` is defined to identify and label the PCP patterns:
    - **Bullish PCP:** Labeled as 1.
    - **Bearish PCP:** Labeled as 0.
    - **No Pattern:** Labeled as -1.
4. **Data Visualization:**
    - OHLC data is visualized using line and candlestick charts.
    - PCP signals are marked on the candlestick chart for visual analysis.
5. **Data Preparation for Modeling:**
    - Data is filtered to include only Bullish and Bearish PCP signals.
    - Features (Open, High, Low, Close) and target (PCP_Label) are separated.
    - Data is split into training and testing sets using TimeSeriesSplit for temporal cross-validation.
    - Data is normalized using MinMaxScaler.
6. **Model Building:**
    - A neural network model is built using TensorFlow Keras with Dense, BatchNormalization, and Dropout layers.
    - The model is compiled using the Adam optimizer and sparse categorical cross-entropy loss function.
7. **Model Training:**
    - The model is trained using the training data with EarlyStopping to prevent overfitting.
    - Training and validation accuracy and loss are monitored.
8. **Model Evaluation:**
    - The model is evaluated on the test data using accuracy and loss metrics.
    - A classification report and confusion matrix are generated.
9. **Model Saving:**
    - The trained model is saved as 'pcp_model_xauusd.keras' for future use.

## Results

- The model achieves a test accuracy of [insert accuracy here] on the XAUUSD M15 data.
- The classification report and confusion matrix provide further insights into the model's performance.

## Usage

1. **Load the saved model:** `loaded_model = load_model('pcp_model_xauusd.keras')`
2. **Prepare input data:** Use the same preprocessing steps as described in the methodology.
3. **Generate predictions:** `predictions = loaded_model.predict(input_data)`
4. **Interpret predictions:**
    - 1: Bullish PCP (potential price increase)
    - 0: Bearish PCP (potential price decrease)

## Future Improvements

- Explore different model architectures and hyperparameters.
- Incorporate additional features, such as technical indicators.
- Develop a trading strategy based on the PCP predictions.

## Disclaimer

This project is for educational and informational purposes only. It should not be considered as financial advice. Trading foreign exchange on margin carries a high level of risk and may not be suitable for all investors. Before deciding to trade foreign exchange, you should carefully consider your investment objectives, level of experience, and risk tolerance. Always seek the advice of a qualified financial professional with any questions you may have regarding Forex trading.
