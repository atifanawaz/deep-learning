# Employee Attrition Prediction Using ANN

This project implements an **Employee Attrition Prediction system** using an **Artificial Neural Network (ANN)**. The model predicts whether an employee will leave the company based on historical HR data.

## Table of Contents

- [Project Overview](#project-overview)  
- [Dataset](#dataset)  
- [Data Preprocessing](#data-preprocessing)  
- [Model Architecture](#model-architecture)  
- [Training](#training)  
- [Evaluation](#evaluation)  
- [Visualizations](#visualizations)  
- [Usage](#usage)  
- [Dependencies](#dependencies)  

## Project Overview

The goal is to predict employee attrition using a neural network model. The ANN is trained on historical HR data with features such as job role, satisfaction, years at company, and other relevant employee information.

The model handles **categorical data** with **one-hot encoding** and applies **feature scaling** to numeric columns.

## Dataset

- The dataset used is `test.csv`.  
- Target column: `Attrition` (`Stayed` = 0, `Left` = 1)  
- The dataset contains numeric and categorical features.  
- Irrelevant columns like `Employee ID` are removed.  
- Duplicate rows are removed to ensure clean data.

## Data Preprocessing

- Duplicate removal to clean data.  
- Dropping irrelevant columns (`Employee ID`).  
- Encoding categorical features using one-hot encoding.  
- Train-test split: 80% train, 20% test with stratification.  
- Feature scaling applied to all features.

## Model Architecture

- Input layer matching the number of features after encoding.  
- Dense layers with ReLU activation.  
- Dropout layers can be used to reduce overfitting.  
- Output layer with Sigmoid activation for binary classification (Attrition: 0 or 1).  

## Training

- Optimizer: Adam (learning rate adjustable).  
- Loss: Binary Crossentropy.  
- Metrics: Accuracy.  
- Early stopping can be applied to avoid overfitting.  

## Evaluation

- Metrics include Accuracy, Precision, Recall, F1-score, and Confusion Matrix.  
- High recall is important to correctly identify employees likely to leave.

## Visualizations

- Training history (accuracy and loss over epochs) can be visualized to monitor performance.  

## Usage

1. Clone the repository:

```bash
git clone <repository_url>
cd <repository_folder>
```
Install dependencies:

```
pip install numpy pandas matplotlib seaborn scikit-learn tensorflow
```

Run the script:

```
python Employee_Attrition_Prediction_ANN.py
```

Dependencies

Python 3.x

numpy

pandas

matplotlib

seaborn

scikit-learn

tensorflow
