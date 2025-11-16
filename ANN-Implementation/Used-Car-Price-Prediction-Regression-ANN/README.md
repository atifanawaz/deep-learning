
# Used Car Price Prediction Using ANN

This project implements a **Used Car Price Prediction system** using an **Artificial Neural Network (ANN)**.  
The model predicts the **selling price of a used car (price_usd)** based on vehicle features such as brand, model, year, mileage, engine size, transmission, fuel type, and more.

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

The goal of this project is to build a **regression model** that predicts the **resale price of a used car** using an ANN.  
The dataset contains **10,000 synthetically generated records** with realistic automotive features.

Key features include:

- Car brand & model  
- Manufacturing year  
- Mileage driven  
- Engine size & horsepower  
- Fuel type & transmission  
- Number of previous owners  
- Car condition rating  
- Location information  

The ANN learns complex patterns from these variables to estimate the selling price.

---

## Dataset

- **Source:** Kaggle — Used Car Price Prediction Dataset  
- **File name:** `used_car_price_dataset_extended.csv`  
- **Rows:** 10,000  
- **Task:** Regression  
- **Target column:** `price_usd`

### Features include:

| Feature | Description |
|--------|-------------|
| brand | Manufacturer (e.g., Toyota, Honda) |
| model | Car model name |
| year | Manufacturing year |
| mileage | Kilometers/miles driven |
| engine_size | Engine capacity (L) |
| horsepower | Horsepower rating |
| fuel_type | Petrol/Diesel/Electric |
| transmission | Automatic/Manual |
| owners | Number of previous owners |
| condition | Numerical condition rating |
| location | City or state |
| price_usd | Selling price (target) |

---

## Data Preprocessing

Steps performed:

1. Loaded dataset and removed duplicates.  
2. Filled missing numeric values using **median**.  
3. Filled missing categorical values using **mode**.  
4. Handled outliers by optionally clipping extreme prices.  
5. Encoded categorical features using **OneHotEncoder** (drop='first').  
6. Scaled numerical features using **StandardScaler**.  
7. Split dataset into **80% training** and **20% test**.  
8. Ensured no data leakage from preprocessing steps.

---

## Model Architecture

A feed-forward **Dense Neural Network** was used for regression:

```python
Sequential([
    Dense(128, activation='relu', input_shape=(X_train.shape[1],)),
    Dropout(0.2),
    Dense(64, activation='relu'),
    Dense(32, activation='relu'),
    Dense(1, activation='linear')
])
```
Details:

Optimizer: Adam (learning rate = 0.001)
Loss: Mean Squared Error (MSE)
Metric: Mean Absolute Error (MAE)
Epochs: 100
Batch Size: 256
Validation Split: 20%
Early Stopping: Enabled
Monitored: val_loss
Patience: 5
restore_best_weights=True

## Training

The model was trained with EarlyStopping to avoid overfitting.
Training curves show improving loss and good generalization.

## Evaluation

Final metrics on the test set:

Metric	Value
MAE	~800
MSE	~1,004,782
RMSE	~1002
R² Score	0.874

These scores indicate excellent performance for a real-world car pricing regression task.

## Visualizations

The project includes:

-Training vs Validation Loss

-Training vs Validation MAE

-Actual vs Predicted Prices

-Residual Distribution

These visualizations confirm strong performance and stable training.

## Usage
Clone the repository:
```
git clone <repository_url>
cd <repository_folder>
```

Install dependencies:
```
pip install numpy pandas matplotlib seaborn scikit-learn tensorflow
```

Run the training script:
```
python Car_Price_ANN.py
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
