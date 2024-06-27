# Predicting Stock Prices
![image](https://github.com/karthiksivakoti/Predicting-Stock-Prices/assets/8302541/d024045d-dda9-4552-a93b-e2f25f5db43b)

![image](https://github.com/karthiksivakoti/Predicting-Stock-Prices/assets/8302541/38086b50-f7dd-473b-a906-eddf6cde872e)

## Project Overview

This project aims to predict the closing stock prices using a Long Short-Term Memory (LSTM) neural network. The model is trained and validated on historical stock data, with features including closing price, volume, high, and low prices. The main objective is to provide accurate predictions of future stock prices and visualize the results.

## Data Source

The stock data is fetched using the Yahoo Finance API via the `yfinance` library. The data includes the following features:
- Close
- Volume
- High
- Low

The data spans from January 1, 2020, to the current date.

## Methodology

### Data Preparation

1. **Data Loading**: Historical stock data is loaded using the `yfinance` library based on user input for the stock symbol.
2. **Feature Selection**: The relevant features selected for this project are Close, Volume, High, and Low prices.
3. **Data Scaling**: The selected features are scaled using the `MinMaxScaler` from the `sklearn.preprocessing` module to ensure all features are within the range [0, 1].
4. **Sequence Creation**: Sequences of 60 timesteps are created to use as inputs for the LSTM model. Each sequence consists of 60 previous days' worth of data to predict the stock price of the next day.

### Model Architecture

The model is constructed using the Keras library with the following architecture:

1. **LSTM Layers**: Four LSTM layers, each with 50 units and `tanh` activation functions. Dropout regularization with a rate of 0.2 is applied to each LSTM layer to prevent overfitting.
2. **Dense Layer**: A fully connected (Dense) layer with 1 unit to produce the output (predicted closing price).

### Hyperparameters

- **Units**: 50 units for each LSTM layer
- **Dropout Rate**: 0.2
- **Optimizer**: Adam
- **Loss Function**: Mean Squared Error (MSE)
- **Epochs**: 10
- **Batch Size**: 32

### Model Training

The dataset is split into training and validation sets (80-20 split). The model is trained on the training set and validated on the validation set to monitor its performance and adjust weights accordingly.

### Evaluation and Prediction

1. **Model Evaluation**: The model's performance is evaluated using the validation set, and the loss is calculated.
2. **Prediction**: The model predicts the closing prices for the test set, and the predictions are inverse-transformed to the original scale.
3. **Visualization**: The real vs. predicted stock prices are plotted to visualize the model's performance. Training and validation loss are also plotted over epochs to show the model's learning progress.

## Results

The model's prediction accuracy and loss are printed and visualized. The final predictions for the current stock price and the next day's stock price are displayed.

## Usage

To use this project:
1. Ensure you have all the necessary dependencies installed:
   ```bash
   pip install numpy pandas yfinance scikit-learn keras matplotlib
