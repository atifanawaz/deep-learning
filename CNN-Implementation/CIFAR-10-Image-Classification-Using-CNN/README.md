# CIFAR-10 Image Classification Using CNN

This project implements a Convolutional Neural Network (CNN) for image classification on the CIFAR-10 dataset. The model is trained using only 20,000 samples instead of the full 50,000 training images to reduce computation time while maintaining strong performance.

---

## Table of Contents
1. Project Overview  
2. Dataset  
3. Data Preprocessing  
4. Model Architecture  
5. Data Augmentation  
6. Training Configuration  
7. Results  
8. How to Run  
9. Dependencies  

---

## 1. Project Overview
This project builds a deep learning model using TensorFlow/Keras to classify images from the CIFAR-10 dataset into ten classes. The model uses convolutional layers, batch normalization, dropout, and global average pooling. Data augmentation is used to improve generalization.

---

## 2. Dataset
CIFAR-10 consists of 60,000 images (32×32 pixels, RGB) across 10 categories:
airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck.

Only 20,000 training images are used in this project for faster computation.

---

## 3. Data Preprocessing
- Loaded CIFAR-10 dataset using Keras.  
- Limited training data to 20,000 samples.  
- Normalized pixel values to the 0–1 range.  
- Visualized the first 25 images with class labels.

---

## 4. Model Architecture
The model is a CNN built with the following components:
- Convolutional layers with ReLU activation  
- Batch Normalization for stable training  
- Max Pooling layers  
- Dropout for regularization  
- Global Average Pooling  
- Dense layers for classification  
- Final Dense layer with 10 outputs (logits)

---

## 5. Data Augmentation
ImageDataGenerator is used to apply:
- Rotation  
- Width and height shifting  
- Horizontal flip  
- Zoom range  

This increases model robustness and reduces overfitting.

---

## 6. Training Configuration
- Optimizer: Adam (learning rate = 0.001)  
- Loss: Sparse Categorical Crossentropy (from logits)  
- Metrics: Accuracy  
- Batch size: 64  
- Epochs: 15  
- Callbacks:
  - EarlyStopping  
  - ReduceLROnPlateau  

---

## 7. Results
Model performance after training:

- Training Accuracy: ~69%  
- Validation Accuracy: ~70–72%  
- Test Accuracy: **72.16%**

Given the reduced training set size (20,000 images), this is a strong result.

---

## 8. How to Run
1. Install required dependencies.  
2. Open the Jupyter Notebook or Google Colab file.  
3. Run all cells to train the model, visualize results, and generate predictions.

---

## 9. Dependencies
```
- Python 3.x  
- TensorFlow  
- NumPy  
- Matplotlib  
- Keras  
```

