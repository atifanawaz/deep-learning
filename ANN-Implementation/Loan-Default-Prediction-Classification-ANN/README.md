# Loan Default Prediction Using ANN

This project implements a **Loan Default Prediction system** using an **Artificial Neural Network (ANN)**. The model predicts whether a loan applicant is likely to default based on historical loan data.

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

The goal is to predict loan default using a neural network model. The ANN is trained on historical loan data with features including loan amount, applicant information, and other relevant variables.  

The model handles **imbalanced datasets** using **SMOTE oversampling** and applies **feature scaling** to numeric columns.  

## Dataset

- The dataset used is `Loan_Default.csv`.  
- Target column: `Status` (1 = Default, 0 = Non-default)  
- The dataset contains numeric and categorical features.  
- Useless or redundant columns such as `ID`, `construction_type`, `Region`, and others are removed.  

## Data Preprocessing

1. **Duplicate removal** to clean data.  
2. **Missing value imputation**:
   - Numeric columns → Mean  
   - Categorical columns → Mode  
3. **Encoding categorical features**:
   - Binary columns → Label Encoding  
   - Multi-category columns → One-hot Encoding  
4. **Train-test split**: 80% train, 20% test with stratification.  
5. **Feature scaling**: StandardScaler for numeric features.  
6. **Handling class imbalance**: SMOTE applied to training set.  

## Model Architecture

The ANN consists of:

- Input layer matching the number of features  
- Dense layers with ReLU activation and BatchNormalization  
- Dropout layers to prevent overfitting  
- Output layer with Sigmoid activation for binary classification  

Example architecture:

Dense(128, activation='relu') → BatchNormalization → Dropout(0.4)
Dense(64, activation='relu') → BatchNormalization → Dropout(0.3)
Dense(32, activation='relu') → Dropout(0.2)
Dense(1, activation='sigmoid')


- Optimizer: **Adam**, Learning rate: 0.001  
- Loss: **Binary Crossentropy**  
- Metrics: Accuracy, Precision, Recall, AUC  

## Training

- Early stopping monitors `val_loss` with patience of 15 epochs.  
- ReduceLROnPlateau reduces learning rate when validation loss plateaus.  
- Batch size: 32  
- Epochs: 200  

## Evaluation

Metrics on the test set:

- **Accuracy**: 0.9051  
- **Precision**: 0.7626  
- **Recall**: 0.8927  
- **F1-Score**: 0.8226  
- **AUC**: 0.9660  

Confusion matrix:

[[20370 2036]
[ 786 6542]]


The model achieves **high recall**, which is critical in predicting loan defaults to minimize risk.  

## Visualizations

1. **Training History**: Shows training vs validation accuracy and loss over epochs.  
2. **ROC Curve**: Demonstrates model's performance in distinguishing defaults from non-defaults.  
3. **Target Distribution**: Visualizes the class balance in the dataset.  

The ROC curve shows a **high AUC (0.9660)** indicating excellent classification performance. The training history graphs indicate stable learning without overfitting.  

## Usage

1. Clone the repository:  

```bash
git clone <repository_url>
cd <repository_folder>
```

Install dependencies:

```
pip install numpy pandas matplotlib seaborn scikit-learn imbalanced-learn tensorflow
```

Run the script:

```
python Loan_Default_Prediction_ANN.py
```
