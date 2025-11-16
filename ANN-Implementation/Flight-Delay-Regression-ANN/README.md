# Flight Delay Prediction Using ANN

This project implements a **Flight Delay Prediction system** using an **Artificial Neural Network (ANN)**.  
The model predicts **arrival delay in minutes** based on historical flight data, scheduled times, carrier, airport, and delay-related features.

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

The goal of this project is to build a **regression model** that predicts **arrival delay (arr_delay)** in minutes using an ANN.  
The dataset contains detailed flight information and historical delays. Key features include:

- Scheduled departure and arrival times  
- Departure delays  
- Taxi times  
- Carrier, origin, and destination airports  
- Delay breakdown (carrier, weather, NAS, security, late aircraft)  
- Time-based features (hour of departure, weekend indicator)  

The ANN learns complex patterns from flight schedules, delays, and airport/carrier characteristics.

---

## Dataset

- **Source:** BTS TranStats, merged monthly CSV files (2024)  
- **File:** `flight_data_2024_sample.csv` (~10,000 rows)  
- **Total rows in full dataset:** ~7 million (optional for larger experiments)  
- **Target column:** `arr_delay`  
- **Features include:**

| Feature | Description |
| ------- | ----------- |
| year, month, day_of_month, day_of_week | Date and day information |
| crs_dep_time, crs_arr_time | Scheduled departure and arrival times |
| dep_delay | Departure delay in minutes |
| taxi_out, taxi_in | Taxiing times in minutes |
| air_time, distance | Flight duration and distance |
| carrier_delay, weather_delay, nas_delay, security_delay, late_aircraft_delay | Delay breakdown by cause |
| op_unique_carrier, origin, dest | Carrier and airport information |
| dep_hour, is_weekend | Derived time features |

---

## Data Preprocessing

Steps performed:

1. Loaded dataset and removed duplicates.  
2. Removed cancelled and diverted flights.  
3. Filled missing delay-related values with 0.  
4. Dropped columns that leak information or are irrelevant.  
5. Converted scheduled times to minutes and extracted **departure hour**.  
6. Created **is_weekend** feature.  
7. One-hot encoded categorical features: carrier, origin, destination.  
8. Scaled numeric features using `StandardScaler`.  
9. Split dataset into **80% training** and **20% test**.  
10. Aggressively handled outliers by clipping `arr_delay` to 0–300 minutes.  

---

## Model Architecture

A simple feed-forward ANN was used for regression:

```python
Sequential([
    Dense(128, activation='relu', input_shape=(X_train.shape[1],)),
    Dropout(0.2),
    Dense(64, activation='relu'),
    Dense(32, activation='relu'),
    Dense(1, activation='linear')
])
```

Optimizer: Adam (learning rate = 0.001)
Loss: Huber Loss (robust to outliers)
Metrics: Mean Absolute Error (MAE)Training
Epochs: 50
Batch Size: 32
Validation Split: 20%
Early Stopping: Monitored val_loss with patience of 5
The model trained consistently and generalized well on validation data.

## Evaluation

Metrics on the test set:

Metric	Value
MAE	1.83 minutes
RMSE	7.63 minutes
R² Score	0.9662

These results indicate excellent performance, with predictions highly accurate for most flights.

## Visualizations

Important visualizations included:

-Actual vs Predicted Arrival Delay
 Scatter plot showing predictions close to the diagonal line.
 
-Residuals Distribution
 Histogram of residuals (actual - predicted) to check bias.

-Residuals vs Predicted
 Ensures errors are randomly distributed.

-Training vs Validation MAE
 Shows learning progression and absence of overfitting.

## Usage

Clone the repository:
```
git clone <repository_url>
cd <repository_folder>
```

Install dependencies:
```
pip install numpy pandas matplotlib scikit-learn tensorflow seaborn
```

Run the script:
```
python Flight_Delay_ANN.py
```

Dependencies
```
Python 3.x

numpy

pandas

matplotlib

seaborn

scikit-learn

tensorflow
```
