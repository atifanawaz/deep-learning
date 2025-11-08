# Churn Modeling ANN Implementation

This repository contains a deep learning project focused on predicting customer churn using an Artificial Neural Network (ANN) built with TensorFlow and Keras. The notebook demonstrates the full machine learning workflow, from data preprocessing and feature engineering to model training, evaluation, and visualization.

## Project Overview

This project implements a neural network model to predict whether a customer will leave a company (churn) based on various features. It includes:

- Data preprocessing (encoding, scaling, splitting)
- Model design using the Keras Sequential API
- Model training with early stopping
- Performance visualization for accuracy and loss

## Model Workflow

1. **Feature Engineering**
   - Convert categorical data (Geography, Gender) using `pd.get_dummies()`
   - Apply `StandardScaler()` to normalize input features

2. **Model Building**
   - Implemented using `Sequential()` and multiple `Dense()` layers
   - Activation functions: ReLU (hidden layers) and Sigmoid (output layer)

3. **Training**
   - Early stopping to prevent overfitting
   - Monitoring of validation loss and accuracy

4. **Evaluation**
   - Model evaluated on test data
   - Accuracy and loss plotted across epochs

## Visualization Example

Example code for visualizing model accuracy:

```python
import matplotlib.pyplot as plt

plt.plot(model_history.history['accuracy'])
plt.plot(model_history.history['val_accuracy'])
plt.title('Model Accuracy')
plt.ylabel('Accuracy')
plt.xlabel('Epoch')
plt.legend(['Train', 'Test'], loc='upper left')

```
## Requirements

```python
pip install tensorflow keras numpy pandas matplotlib scikit-learn

```
## Results
  -The notebook provides:
  -Training and validation accuracy and loss metrics
  -Early stopping summary
  -Visual plots for accuracy and loss trends

plt.show()

