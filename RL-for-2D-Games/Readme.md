# T-Shirt Size Estimation Using Monocular Camera Images

## Overview
This project presents a vision-based system that estimates the T-shirt size of a person from a single monocular image. It explores and compares three approaches:  
1. A fast baseline method using MediaPipe landmarks.  
2. A geometric method involving perspective correction and reference scaling.  
3. A deep learning model trained on real-world anthropometric datasets.

This system demonstrates practical potential for contactless sizing in e-commerce and apparel recommendations.

---

## Features
- Pose estimation and body landmark detection using **MediaPipe**.
- Perspective geometry-based height and width approximation.
- Deep Learning-based body measurement prediction using CNN architecture.
- Preprocessing includes background removal, normalization, and patch extraction.
- Size classification (XS, S, M, L, XL, XXL) using estimated upper body width and chest circumference.
- Modular architecture supporting both image-based and real-time webcam input.

---

## Dataset
The deep learning model is trained on real anthropometric datasets, including:
- **ZOZOTOWN** (Japan-based apparel sizing and measurement database)
- **CAESAR** dataset and additional open-source measurement data
- Synthetic augmentations for improved generalization

---

## System Pipeline
1. **Input Image**: Single RGB image from monocular camera (e.g., phone/webcam)
2. **Pose Detection**: Using MediaPipe's BlazePose to detect landmarks
3. **Perspective Correction**: Align body posture and scale using reference object
4. **Feature Extraction**: Crop and measure regions of interest (e.g., chest)
5. **Model Inference**: Pass through CNN for measurement estimation
6. **Size Classification**: Use predicted measurement to classify size

---

## Results
- Achieved up to **89% accuracy** on front-facing images with minimal background clutter using the DL model.
- Geometric model yielded competitive results under ideal reference object placement.
- Fast MediaPipe-only estimation gave instant feedback with slightly lower precision.
- Performance metrics:
  - Accuracy: 89% (Deep Learning), ~81% (Geometric), ~75% (Baseline)
  - F1-score: 0.86 (DL), 0.78 (Geo)

---

## How to Run

### Prerequisites
- Python 3.7+
- Install dependencies:
