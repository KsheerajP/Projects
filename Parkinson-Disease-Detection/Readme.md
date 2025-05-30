# Early Detection of Parkinson’s Disease Using Machine Learning

## Overview
This project aims to detect early signs of Parkinson’s Disease using voice signal data and machine learning models. By analyzing vocal attributes like jitter, shimmer, and fundamental frequency variations, the model can classify patients with or without Parkinson’s, aiding in early diagnosis via a non-invasive and low-cost method suitable for remote health applications.

---

## Features
- Preprocessing of patient voice samples including normalization and noise filtering.
- Feature extraction focusing on medically relevant vocal traits.
- Application of SMOTE for balancing class distribution.
- Feature selection using **SelectKBest** to reduce dimensionality and focus on the most important indicators.
- Grid Search Cross-Validation to fine-tune hyperparameters for each model.
- Performance evaluation using metrics like Accuracy, F1-score, Precision, Recall, and Confusion Matrix.

---

## Models Used
- **Multi-Layer Perceptron (MLP)**
- **Support Vector Machines (SVM)**
- **Random Forest (RF)**
- **Logistic Regression**
- **K-Nearest Neighbors (KNN)**

---

## Dataset
- Source: UCI Machine Learning Repository
- Includes 195 recordings from patients diagnosed with Parkinson’s and healthy controls.
- Features extracted: 23 vocal parameters like MDVP:Fo(Hz), jitter, shimmer, HNR, etc.

---

## Results
- Achieved **90% accuracy** with the best-performing model (MLP).
- F1-score: ~0.89 for most balanced models.
- Significant improvements seen after SMOTE and feature selection.
- Demonstrated real-world applicability for telehealth and early screening.

---

## How to Run
1. Clone the repository and install dependencies:
