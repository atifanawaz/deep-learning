# AgeNet: CNN-Based Facial Age Regression

## Project Overview
This project implements a Convolutional Neural Network (CNN) to predict human age from face images using the UTKFace dataset. The task is a **regression problem**, where the model predicts a continuous age value rather than classifying into categories. The project demonstrates data preprocessing, CNN model building, training, and evaluation for real-world age estimation.

## Dataset
**UTKFace**: A large-scale face dataset with over 20,000 images annotated with age, gender, and ethnicity. Images have variations in pose, expression, illumination, and resolution.  

- Total images used: **10,000** (subset sampled after merging both folders)  
- Image size: 128×128 (resized for CNN)  
- Age range: 0–116 years  

## Data Preprocessing
- Extracted and merged images from two folders inside the archive.
- Randomly selected 10,000 images for training and validation.
- Split dataset into:
  - **Training set:** 8,000 images
  - **Validation set:** 2,000 images
- Rescaled pixel values to [0,1].
- Applied data augmentation (rotation, shifts, horizontal flips) to training set to reduce overfitting.

## Model Architecture
A simple CNN regression model was built:

- **Input:** 128×128×3 RGB image
- **Conv2D + MaxPooling2D layers:** Feature extraction
- **Flatten + Dense layers:** Regression mapping
- **Dropout:** 0.3 to reduce overfitting
- **Output layer:** Single neuron for continuous age prediction
- **Loss:** Mean Squared Error (MSE)
- **Metric:** Mean Absolute Error (MAE)

## Training
- Trained for **20 epochs** with early stopping based on validation loss.
- Batch size: 32
- Optimizer: Adam

**Training Results:**
- Final validation MAE: **~7.11 years**
- Final validation loss (MSE): **~91.60**

**Sample Epoch Progress:**
```
Epoch 1: MAE ~17.35, val_MAE ~13.13
Epoch 10: MAE ~7.61, val_MAE ~7.34
Epoch 20: MAE ~5.54, val_MAE ~7.59
```

## Evaluation
- Model evaluated on validation set.
- **Test MAE:** 7.11 years
- Scatter plots of predicted vs actual ages show predictions close to true ages.
- Sample images visualized with predicted and actual ages for qualitative check.

## Observations
- The model achieves **good performance** for a simple CNN on a subset of UTKFace.
- MAE around 7 years is acceptable given the dataset variability.
- Further improvements can be achieved using:
  - Transfer learning with pretrained CNNs (e.g., ResNet, MobileNet)
  - Larger dataset usage
  - Hyperparameter tuning and deeper CNN architectures

## Usage
1. Prepare UTKFace images and merge folders.
2. Preprocess images (resize, rescale, augment).
3. Split into train/validation sets.
4. Train the CNN model using Keras.
5. Evaluate MAE on validation/test set.
6. Visualize predictions with scatter plots or sample images.

## References
- TensorFlow/Keras Documentation for CNN and ImageDataGenerator
