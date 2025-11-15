# Customer Churn Prediction Using ANN

This project implements a **Customer Churn Prediction system** using an **Artificial Neural Network (ANN)**. The model predicts whether a customer will leave (churn) based on historical customer data.

## Table of Contents

- [Project Overview](#project-overview)  
- [Dataset](#dataset)  
- [Data Preprocessing & Feature Engineering](#data-preprocessing--feature-engineering)  
- [Model Architecture](#model-architecture)  
- [Training](#training)  
- [Evaluation](#evaluation)  
- [Visualizations](#visualizations)  
- [Usage](#usage)  
- [Dependencies](#dependencies)  

## Project Overview

The goal is to predict customer churn using a neural network model. The ANN is trained on historical customer data with features including demographics, account information, and activity metrics.  

Feature scaling is applied to numeric columns to improve model performance.  

## Dataset

- The dataset used is `Churn_Modelling.csv`.  
- Target column: `Exited` (1 = Churn, 0 = Stayed)  
- Features include `CreditScore`, `Geography`, `Gender`, `Age`, `Tenure`, `Balance`, `NumOfProducts`, `HasCrCard`, `IsActiveMember`, `EstimatedSalary`.  
- Categorical variables `Geography` and `Gender` are encoded into numeric columns.  

## Data Preprocessing & Feature Engineering

1. **Encoding categorical features**:
   - Geography → One-hot encoding (drop first column)  
   - Gender → One-hot encoding (drop first column)  
2. **Concatenation**: Encoded columns are concatenated to the main dataset and original categorical columns are dropped.  
3. **Train-test split**: 80% train, 20% test.  
4. **Feature scaling**: StandardScaler applied to numeric features.  

## Model Architecture

The ANN consists of:

- Input layer matching the number of features (11)  
- Dense layers with ReLU activation:  
  - Dense(11, activation='relu') → input layer  
  - Dense(7, activation='relu') → first hidden layer  
  - Dense(6, activation='relu') → second hidden layer  
- Output layer: Dense(1, activation='sigmoid') for binary classification  
- Optimizer: Adam with learning rate 0.01  
- Loss: Binary Crossentropy  
- Metrics: Accuracy  

## Training

- Validation split: 33% of training data  
- Batch size: 10  
- Epochs: 1000 with **EarlyStopping** (monitor='val_loss', patience=20)  
- Early stopping triggered at epoch 38  

## Evaluation

- Confusion matrix:

[[1528 67]
[ 219 186]]


- Accuracy: 0.857  

The model shows reasonable accuracy and can identify churned customers effectively.  

## Visualizations

- **Accuracy over epochs**:

![Model Accuracy](accuracy_plot.png)

- **Loss over epochs**:

![Model Loss](loss_plot.png)

These plots help visualize model learning and detect potential overfitting.  

## Usage

1. Clone the repository:

```bash
git clone <repository_url>
cd <repository_folder>
```

Install dependencies:

```
pip install numpy pandas matplotlib scikit-learn tensorflow
```

Run the script:

```
python Churn_Modelling_ANN.py
```

Dependencies

Python 3.x

numpy

pandas

matplotlib

scikit-learn

tensorflow
