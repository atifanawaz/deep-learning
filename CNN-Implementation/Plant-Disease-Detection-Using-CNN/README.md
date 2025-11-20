# Plant Disease Detection Using CNN

## Table of Contents
1. Project Overview  
2. Dataset  
3. Objectives  
4. Methodology  
5. Model Architecture  
6. Training Process  
7. Evaluation  
8. Results and Insights  
9. How to Use  
10. Future Improvements  
11. License  

---

## 1. Project Overview
This project develops a Convolutional Neural Network (CNN) capable of identifying plant diseases from leaf images. The goal is to support early diagnosis and promote efficient crop management by automating disease detection.

---

## 2. Dataset
The project uses the PlantVillage dataset, which contains images of plant leaves labeled with their corresponding disease classes.

Key details:  
- Total images available: 54,303  
- Number of classes: 38  
- This project utilizes a subset of 20,000 images to reduce training time while preserving class diversity.  

---

## 3. Objectives
- Build a deep learning model that can classify plant leaf diseases accurately.  
- Apply preprocessing techniques to optimize model performance.  
- Evaluate the model using metrics such as accuracy, loss, confusion matrix, and classification report.  
- Demonstrate practical usage for agricultural diagnostics.

---

## 4. Methodology
- Load a subset of the PlantVillage dataset via TensorFlow Datasets (TFDS).  
- Preprocess images by resizing and normalizing pixel values.  
- Apply batching and prefetching for efficient training.  
- Train a CNN to learn disease-specific patterns in leaf images.  
- Validate performance using unseen data.  

---

## 5. Model Architecture
The CNN architecture includes:
- Convolution layers for feature extraction  
- MaxPooling layers for spatial reduction  
- Flatten layer for feature vector conversion  
- Dense layers for classification  
- Softmax activation for multiclass output  

Loss function: sparse categorical crossentropy  
Optimizer: Adam  
Metrics: accuracy, precision, recall, F1-score  

---

## 6. Training Process
- The dataset is split into 80 percent training and 20 percent validation.  
- EarlyStopping prevents overfitting by monitoring validation loss.  
- The model is trained for multiple epochs until convergence.  

---

## 7. Evaluation
The trained model is evaluated using:
- Validation accuracy and loss  
- Confusion matrix  
- Classification report for all classes  
- Visualization of predictions on sample images  

---

## 8. Results and Insights
The results confirm that the CNN captures disease-specific visual features such as color distortions, texture anomalies, and shape patterns. The confusion matrix reveals which diseases are recognized accurately and which require further data balancing or architectural enhancement.

---

## 9. How to Use
- Load the dataset through TensorFlow Datasets.  
- Train the provided CNN model.  
- Evaluate using the included metrics and visualization utilities.  
- Use the prediction function to classify new leaf images.

---

## 10. Future Improvements
- Integrate transfer learning for higher accuracy.  
- Build a mobile application using TensorFlow Lite.  
- Add Grad-CAM visualizations for model explainability.  
- Improve class balance with targeted data augmentation.  

---

## 11. License
This project may be used or modified for academic and research purposes.

