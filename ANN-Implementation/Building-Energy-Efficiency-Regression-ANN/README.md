# Building Energy Efficiency Prediction Using ANN

This project implements a **Building Energy Efficiency Prediction system** using an **Artificial Neural Network (ANN)**.  
The model predicts the **heating load and cooling load** of a building based on architectural and physical features.

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

The goal of this project is to build a regression model that predicts the **energy efficiency** of a building using an ANN.  
The dataset contains real-world data on building characteristics and energy performance.

Key features include:

- Relative compactness
- Surface area
- Wall area
- Roof area
- Overall height
- Orientation
- Glazing area & glazing area distribution

The ANN learns complex patterns from these variables to estimate **heating load** and **cooling load**.

---

## Dataset

**Source:** Kaggle — Building Energy Efficiency Dataset  
**File name:** building_energy_efficiency.csv  
**Rows:** 1,000+  
**Task:** Regression  
**Target columns:** `heating_load`, `cooling_load`  
**Features include:**

| Feature                  | Description                                      |
|---------------------------|--------------------------------------------------|
| Relative_Compactness      | Ratio of building volume to surface area        |
| Surface_Area              | Total surface area of the building              |
| Wall_Area                 | Total wall area                                  |
| Roof_Area                 | Total roof area                                  |
| Overall_Height            | Building height                                  |
| Orientation               | Orientation of the building (1–4)               |
| Glazing_Area              | Total area of windows                            |
| Glazing_Area_Distribution | Glazing distribution pattern (0–5)              |
| Heating_Load              | Target: Heating energy requirement (kWh/m²)     |
| Cooling_Load              | Target: Cooling energy requirement (kWh/m²)     |

---

## Data Preprocessing

Steps performed:

- Loaded dataset and removed duplicates.
- Filled missing numeric values using median (if any).
- Scaled numerical features using StandardScaler.
- Split dataset into 80% training and 20% test set.
- Ensured no data leakage from preprocessing steps.

---

## Model Architecture

A feed-forward Dense Neural Network was used for regression:

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Dropout

model = Sequential([
    Dense(128, activation='relu', input_shape=(X_train.shape[1],)),
    Dropout(0.2),
    Dense(64, activation='relu'),
    Dense(32, activation='relu'),
    Dense(2, activation='linear')  # Predict heating and cooling load
])

model.compile(optimizer='adam', loss='mse', metrics=['mae'])
```
## Details:

Optimizer: Adam (learning rate = 0.001)
Loss: Mean Squared Error (MSE)
Metric: Mean Absolute Error (MAE)
Epochs: 200
Batch Size: 64
Validation Split: 20%
Early Stopping: Enabled
Monitored: val_loss
Patience: 10
restore_best_weights=True

## Training

The model was trained with EarlyStopping to prevent overfitting.
Training curves show steady convergence and good generalization.

## Evaluation

Final metrics on the test set:

Metric	Heating Load	Cooling Load
MAE	0.685	0.701
MSE	0.945	0.972
RMSE	0.972	0.986
R² Score	0.950	0.947

These scores indicate excellent performance for predicting building energy efficiency.

## Visualizations

Important visualizations included:

 -Training vs Validation Loss
 -Training vs Validation MAE
 -Actual vs Predicted Heating & Cooling Load

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
python Building_Energy_Efficiency_ANN.py
```

Dependencies
```
Python 3.x

numpy

pandas

matplotlib

seaborn

scikit-learn

tensorflowTraining
```

