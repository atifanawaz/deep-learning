
# Stock Market Trend Prediction Using ANN

This project implements a Stock Market Trend Prediction system using an Artificial Neural Network (ANN). The model predicts whether the stock price will go up or down the next day based on historical stock data and technical indicators.

---

## Table of Contents
- Project Overview
- Dataset
- Data Preprocessing
- Model Architecture
- Training
- Evaluation
- Visualizations
- Usage
- Dependencies

---

## Project Overview

The goal is to predict next-day stock price movement using an ANN. The model is trained on historical stock data including OHLC prices, volume, and derived technical indicators such as RSI, MACD, Bollinger Bands, ATR, OBV, CCI, and lagged features.

The model handles imbalanced classes using class weights and applies feature scaling for numeric columns.

---

## Dataset

- The dataset used is StockPriceDataset.csv.
- Target column: `Target` (1 = Price Up, 0 = Price Down).
- The dataset contains daily stock features: Open, High, Low, Close, Volume, and engineered technical indicators.
- Duplicate rows are removed, and irrelevant columns are dropped.

---

## Data Preprocessing

- Duplicate removal for cleaning.
- Missing value imputation using forward fill.
- Feature Engineering:
  - Price change & percent change
  - Moving Averages (SMA, EMA)
  - Momentum (RSI)
  - MACD & Signal line
  - Bollinger Bands
  - Additional indicators: OBV, ATR, CCI, Stochastic %K/%D
  - Lagged features (past 3 days of Close, Volume, SMA_5, RSI_14, MACD)
- Train-test split: 80% train, 20% test (time-based, no shuffling).
- Feature scaling: MinMaxScaler applied to all numeric features.
- Handling class imbalance: Class weights applied during model training.

---

## Model Architecture

The ANN consists of:

- Input layer matching the number of features (33 in current dataset).
- Dense layers with ReLU activation and Dropout layers to prevent overfitting.
- Output layer with Sigmoid activation for binary classification.

Example architecture:
```

Dense(128, activation='relu') → Dropout(0.3)
Dense(64, activation='relu') → Dropout(0.2)
Dense(32, activation='relu')
Dense(1, activation='sigmoid')

```
- Optimizer: Adam
- Loss: Binary Crossentropy
- Metrics: Accuracy, Precision, Recall, F1-Score, AUC

---

## Training

- EarlyStopping monitors `val_loss` with patience of 10 epochs.
- Batch size: 32
- Epochs: 100 (can increase for fine-tuning)

---

## Evaluation

Metrics on the test set:

- Accuracy: 0.768
- Precision: 0.738
- Recall: 0.842
- F1-Score: 0.786
- AUC: 0.866

Confusion Matrix:
```

[[1720  762]
[ 402 2143]]

```
The model maintains high recall, which is crucial in capturing upward trends in stock prices.

---

## Visualizations

- Training History: Shows training vs validation accuracy and loss over epochs.
- Confusion Matrix: Highlights correct and incorrect predictions.
- ROC Curve: Demonstrates the model’s ability to distinguish upward vs downward movements.
- Feature Importance (SHAP): Shows which indicators most influence predictions (RSI, MACD, OBV, lagged Close often top contributors).

---

## Usage

Clone the repository:
```

git clone <repository_url>
cd <repository_folder>

```

Install dependencies:
```

pip install numpy pandas matplotlib seaborn scikit-learn tensorflow shap

```

Run the script:
```

python Stock_Market_Trend_ANN.py

```

---

## Dependencies
```
- Python 3.x
- numpy
- pandas
- matplotlib
- seaborn
- scikit-learn
- tensorflow
- shap (optional for feature importance)
```

