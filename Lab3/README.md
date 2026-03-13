## Student Information

**Name:** Vatsal Patel
**Student ID:** 202511040
**Course:** IT549 – Deep Learning  
**Assignment:** Lab 3  

---

# Image-Based AQI Classification using CNN and Transfer Learning

---

# Lab Overview

This project implements an **image-based Air Quality Index (AQI) classification system** using deep learning. The goal is to predict the **AQI_Class** of a location based on environmental images.

Two different models were implemented and compared:

1. **Basic Convolutional Neural Network (CNN)** trained from scratch  
2. **Pretrained CNN using Transfer Learning (ResNet50)**  

The project demonstrates a complete deep learning pipeline including:

- Data preprocessing  
- Model training  
- Model evaluation  
- Performance comparison  
- Misclassification analysis  

---

# Dataset

The dataset consists of two components:

- **data.csv** – contains image file names and related information  
- **sampled_images/** – directory containing the images  

For this assignment, only the following fields were used:

| Column | Purpose |
|------|------|
| Filename | Input image |
| AQI_Class | Target classification label |

Other pollution-related features in the dataset were not used for model training.

---

# Data Preprocessing

The following preprocessing steps were performed:

- Images resized to **224 × 224**
- Pixel normalization using **ImageNet statistics**
- AQI class labels encoded into numeric values
- Dataset split into training, validation, and test sets:

| Split | Percentage |
|------|------|
| Training | 70% |
| Validation | 15% |
| Test | 15% |

---

# Model 1: Basic CNN

A Convolutional Neural Network (CNN) was implemented from scratch for image classification.

### Architecture

Conv → ReLU → MaxPool  
Conv → ReLU → MaxPool  
Conv → ReLU → MaxPool  
Fully Connected Layer  
Dropout  
Output Layer  

### Training Settings

| Parameter | Value |
|------|------|
| Epochs | 5 |
| Optimizer | Adam |
| Loss Function | CrossEntropyLoss |
| Batch Size | 32 |

---

# Model 2: Pretrained CNN (Transfer Learning)

A **ResNet50 model pretrained on ImageNet** was used for transfer learning.

### Transfer Learning Strategy

- First **10 layers were frozen**
- Final classification layer was replaced to match AQI classes
- Remaining layers were fine-tuned during training

### Training Settings

| Parameter | Value |
|------|------|
| Epochs | 5 |
| Optimizer | Adam |
| Loss Function | CrossEntropyLoss |

---

# Model Evaluation

Both models were evaluated on the **test dataset** using:

- Accuracy  
- Precision  
- Recall  
- F1 Score  
- Confusion Matrix  

### Performance Comparison

| Model | Accuracy | Precision | Recall | F1 Score |
|------|------|------|------|------|
| Basic CNN | 0.815555 | 0.822432 | 0.815555 | 0.814150 |
| Pretrained ResNet | 0.801111 | 0.811128 | 0.801111 | 0.800259 |

The **Basic CNN slightly outperformed the pretrained ResNet model** in this experiment.

---

# Discussion

Although pretrained models often perform better, the Basic CNN achieved slightly higher performance in this case. Possible reasons include:

- The dataset may contain relatively simple visual patterns that a custom CNN can learn effectively.
- Only a small portion of the pretrained model was fine-tuned, limiting its adaptation to the dataset.
- Both models were trained for only **5 epochs**, which may not be enough for the pretrained model to fully adjust.
- The pretrained model was trained on **ImageNet objects**, while this dataset focuses on environmental scenes.

---

# Training Curves

Training and validation curves were plotted for:

- **Loss vs Epoch**
- **Accuracy vs Epoch**

These curves help visualize the training process and identify issues such as overfitting or underfitting.

---

# Misclassification Analysis

Several misclassified images from the test dataset were analyzed. Each image was visualized with:

- Predicted AQI class
- Actual AQI class

### Possible Reasons for Misclassification

1. Visual similarity between AQI classes  
2. Variations in lighting or weather conditions  
3. Limited number of samples for some classes  
4. Background objects affecting predictions  
5. Differences in image quality  

---
