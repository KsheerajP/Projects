# Early Detection of Parkinson’s Disease Using Machine Learning

## Overview
This project implements a machine learning-based system to detect early signs of Parkinson’s Disease using voice recordings. By analyzing vocal biomarkers, the system aims to serve as a low-cost, non-invasive diagnostic tool for telehealth and remote care.

---

## Features
- Utilizes real-world patient voice data from the UCI Parkinson’s dataset.
- Applies various preprocessing steps such as feature normalization and SMOTE for class balancing.
- Implements and compares multiple ML models including:
  - **Multi-layer Perceptron (MLP)**
  - **Support Vector Machine (SVM)**
  - **Random Forest Classifier**
- Performs **feature selection** using SelectKBest to retain the most relevant attributes.
- Evaluates models using accuracy, precision, recall, F1-score, and confusion matrices.

---

## Dataset
The system uses the UCI Machine Learning Repository's Parkinson’s Disease dataset, which includes biomedical voice measurements from people with and without the disease.

---

## Results
- Achieved **up to 90% accuracy** using the MLP classifier.
- Demonstrated reliable classification using both traditional and deep models.
- Validated the approach for remote health applications with minimal setup.

---

## Tools & Libraries
- Python
- scikit-learn
- pandas
- numpy
- matplotlib / seaborn
- imbalanced-learn (SMOTE)

---

## How to Run
1. Clone the repository and navigate to the project directory.
2. Install dependencies:
