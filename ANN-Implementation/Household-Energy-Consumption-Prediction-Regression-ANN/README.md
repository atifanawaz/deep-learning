# Household Energy Consumption Prediction Using ANN

This project implements a Household Energy Consumption Prediction system using an Artificial Neural Network (ANN).  
The model predicts **Global Active Power** based on historical household electrical measurements such as voltage, current intensity, sub-metering values, and time-based features.

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

The goal of this project is to build a regression model that predicts **Global Active Power (kilowatts)** using an ANN.  
The dataset contains minute-level power consumption readings from a household, and features include:

- Voltage  
- Global Intensity  
- Sub-metering values  
- Time features (Hour, Day, Month)

The model uses a feed-forward neural network to learn patterns from energy usage behavior.

---

## Dataset

- Dataset: `household_power_consumption.txt`
- Total rows in raw dataset: Over 2 million  
- For this project, a random sample of **25,000 rows** is used.
- Target column: `Global_active_power`

Dataset features include:

- Global_active_power  
- Global_reactive_power  
- Voltage  
- Global_intensity  
- Sub_metering_1  
- Sub_metering_2  
- Sub_metering_3  
- DateTime (later converted into Hour, Day, Month)

---

## Data Preprocessing

Steps performed:

1. Loaded dataset and cleaned missing values.
2. Converted `Date` and `Time` into a combined `DateTime` field.
3. Converted all numeric columns using `to_numeric(errors='coerce')`.
4. Dropped NaN values.
5. Randomly selected **25,000 clean rows**.
6. Extracted time-based features:
   - Hour  
   - Day  
   - Month
7. Removed `DateTime` after feature extraction.
8. Normalized input features using `MinMaxScaler`.
9. Split dataset into 80% training and 20% test.

---

## Model Architecture

A simple but powerful ANN was used for regression:

```
Dense(64, activation='relu')
Dense(32, activation='relu')
Dense(16, activation='relu')
Dense(1, activation='linear')

```

- Optimizer: Adam (lr = 0.001)  
- Loss: Mean Squared Error (MSE)  
- Metrics: Mean Absolute Error (MAE)

---

## Training

- Epochs: 20  
- Batch Size: 512  
- Validation split: 20%  
- Model learns consistently without overfitting.

`EarlyStopping` can be added for improvement (optional).

---

## Evaluation

Metrics on the test set:

- **MAE:** 0.0187  
- **MSE:** 0.0009  
- **RMSE:** 0.0304  
- **R² Score:** 0.9992  

These results show **excellent model performance**, with predictions extremely close to actual energy usage.

---

## Visualizations

Important visualizations included:

1. **Training vs Validation Loss Curve**  
   Shows learning progression and checks overfitting.

2. **Actual vs Predicted Scatter Plot**  
   Points align closely with the diagonal line, indicating strong accuracy.

---

## Usage

Clone the repository:

```
git clone <repository_url>
cd <repository_folder>

```

Install dependencies:

```
pip install numpy pandas matplotlib scikit-learn tensorflow

```

Run the script:

```

python Energy_Consumption_ANN.py

```

## Dependencies

```
Python 3.x

numpy

pandas

matplotlib

scikit-learn

tensorflow

Copy code
```
