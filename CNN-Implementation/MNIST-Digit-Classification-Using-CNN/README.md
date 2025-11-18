# MNIST_Digit_Classification_Using_CNN

A deep Convolutional Neural Network (CNN) to classify handwritten digits (0–9) using the MNIST dataset. The project includes data augmentation to improve generalization and achieve high accuracy even with a subset of the dataset.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Dataset](#dataset)
3. [Requirements](#requirements)
4. [Installation](#installation)
5. [Usage](#usage)
6. [Model Architecture](#model-architecture)
7. [Training Results](#training-results)
8. [Testing & Prediction](#testing--prediction)
9. [Future Improvements](#future-improvements)
10. [License](#license)

---

## Project Overview

This project builds a deep CNN to recognize handwritten digits using MNIST.  
Key features:  

- Deeper CNN architecture for better feature extraction  
- Data augmentation for improved generalization  
- Subset training for faster experimentation  
- High test accuracy (~99.3%)  

---

## Dataset

- **Name:** MNIST Handwritten Digits  
- **Source:** Built-in Keras dataset  
- **Training images:** 60,000 (subset of 20,000 used for faster training)  
- **Test images:** 10,000  
- **Image size:** 28×28 pixels, grayscale  

All code for loading and preprocessing the dataset is included in the notebook.

---

## Requirements
```
- Python 3.x  
- TensorFlow / Keras  
- Numpy  
- Matplotlib  
```
---

## Installation

1. Clone this repository  
2. Ensure dependencies are installed  
3. Run the Jupyter Notebook to execute the project  

---

## Usage

All preprocessing, model building, training, and prediction code is provided in the notebook.  
Users can train the CNN, evaluate accuracy, and test predictions on handwritten digits.

---

## Model Architecture

The CNN consists of:

- 3 Convolutional layers with increasing filters  
- MaxPooling layers after convolutional blocks  
- Dropout layers to prevent overfitting  
- Flatten layer to convert feature maps to vectors  
- Fully connected Dense layers for classification  
- Output layer with 10 neurons for digit classes (0–9)

---

## Training Results

- **Subset used:** 20,000 images  
- **Final Training Accuracy:** ~97.7%  
- **Final Validation/Test Accuracy:** ~99.3%  
- Data augmentation helped achieve high generalization with a smaller subset.

---

## Testing & Prediction

The notebook includes code to predict:

- Single test images  
- Multiple test images  

This allows visualization of predictions alongside the actual handwritten digits.

---

## Future Improvements

- Increase subset to full 60,000 images for higher accuracy  
- Implement real-time prediction with uploaded handwritten images  
- Add an interactive web interface using Streamlit or Flask  
- Experiment with different architectures (e.g., LeNet, ResNet) for comparison

---

## License

This project is open-source and free to use for educational purposes.

