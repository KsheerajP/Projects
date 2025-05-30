# Early Detection of Parkinson’s Disease Using Machine Learning

## Overview
This project focuses on building a machine learning-based pipeline to detect early signs of Parkinson’s Disease using voice recordings. It aims to offer a non-invasive, low-cost method that could assist in remote diagnostics and telehealth applications.

## Accessing the Code
If you're interested in exploring the full source code of this project, feel free to reach out to me via [LinkedIn](https://www.linkedin.com/in/ksheerajprakash) or email me at `ksheerooo@gmail.com`. I’ll be happy to provide access upon request.

🔗 GitHub Repository (private): [https://github.com/KsheerajP/Parkinson-Disease-Detection](https://github.com/KsheerajP/Parkinson-Disease-Detection.git)

## How It Works
The system analyzes voice features from audio samples of patients and uses these to train machine learning models for early disease detection.

- Voice signals are processed to extract clinical features related to frequency, jitter, and amplitude variation.
- The processed features are used to train models like **MLP**, **SVM**, and **Random Forest**.
- Feature selection techniques and **SMOTE** balancing are applied to ensure high-quality predictions on real-world data.

The pipeline is designed to generalize well to unseen patient samples, enabling reliable screening even in decentralized setups like mobile clinics or remote healthcare systems.

## Results
- Achieved up to **90% accuracy** in detecting early signs of Parkinson’s Disease.
- Balanced performance across models with reliable **precision and recall**, especially using MLP and Random Forest.
- Demonstrated strong potential for early screening using only voice data, without the need for physical tests or sensors.
