# Foggy_image_classification

Fog vs non-fog image classification using a fixed CNN architecture and VGG-16 transfer learning, with emphasis on analyzing the effect of different data distributions.

---

## 1. Data Type

- **Data format**: Image data captured using fixed cameras  
- **Classes**:
  - `0` – Non-foggy  
  - `1` – Foggy  
- **Additional metadata**:
  - `date_time` – Timestamp of image  
  - `visibility` – Visibility value at 10-minute intervals  
  - `status` – Fog (1) / No fog (0)  
  - `category` – Fog intensity (0–5, not used in this work)  
- **Sampling interval**: Every 10 minutes  
- **Months used**: November, December, January, February (to reduce seasonal imbalance)

---

## 2. Goal

The goal of this project is to classify images into foggy and non-foggy categories and to study how different data distributions influence model performance. The focus is on binary image classification using a fixed CNN architecture and a VGG-16 transfer learning model.

---

## 3. Models (Input Data and Architecture)

### CNN Architecture
- Input image size: **128 × 128**
- Convolution, max-pooling, and fully connected layers
- Sigmoid output layer
- **Same CNN architecture used for all CNN-based experiments**
- Only the **input data distribution changes**

### CNN Experiments (Different Data Inputs)

- **Model 1 – Baseline**
  - Original data distribution
  - Trained using augmented images
  - Used as reference model

- **Model 2 – Day Data**
  - Trained using only daytime images
  - Data imbalance present

- **Model 3 – Night Data**
  - Trained using only nighttime images
  - Severe class imbalance

- **Model 4 – Balanced Data**
  - Data redistributed to maintain:
    - 50:50 fog / no-fog ratio  
    - 50:50 day / night ratio  
  - Train–test split of 80:20

- **Model 5 – Balanced + Augmented Data**
  - Same balanced data as Model 4
  - Additional data augmentation applied during training

### Transfer Learning Model

- **Model 6 – VGG-16**
  - Pre-trained VGG-16 used for feature extraction
  - Convolutional layers frozen
  - Fully connected layers trained on fog dataset
  - Trained on balanced data distribution

---

## 4. Results

- Separating data into day and night does not significantly improve performance
- Balanced data distribution improves CNN performance compared to the baseline
- Data augmentation does not always reduce overfitting
- **VGG-16 transfer learning achieves the best overall performance**
