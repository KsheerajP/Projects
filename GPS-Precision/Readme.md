# GPS Precision Enhancement Using Kalman Filter and Fuzzy Logic

## Overview
This project implements a robust GPS correction framework that significantly enhances positioning accuracy using real-time filtering and fuzzy logic. It explores multiple GPS error correction techniques, focusing on **Dynamic Kalman Filters**, **Differential GPS (DGPS)**, and **ANFIS-based fuzzy logic systems** for intelligent localization improvement.

The system is particularly designed for embedded navigation and mobile platforms where precision is critical, such as autonomous vehicles and robotics.

---

## Features
- Dynamic **Kalman Filter** implementation for trajectory prediction and noise suppression.
- **Fuzzy logic correction systems** built using **MATLAB ANFIS** for latitude and longitude error compensation.
- Incorporation of **Position Dilution of Precision (PDOP)** and **Horizontal Dilution of Precision (HDOP)** metrics for error modeling.
- Error estimation techniques including **absolute error calculation**, **distance estimation**, and **haversine-based localization updates**.
- Code written in **C** for performance and embedded compatibility.

---

## Methodology
- Sensor fusion from GPS receivers to dynamically adjust location predictions.
- Use of differential GPS reference station data to calculate correction values.
- Fuzzy inference systems trained on real-world datasets for fine-grained error correction.
- Simulation of "cold start" scenarios and adaptive estimation in low-signal environments.

---

## Results
- Achieved up to **80% improvement** in accuracy over conventional EKF-based systems.
- Positional error reduced from **±5.2 m** to under **±1.0 m**, with stability in noisy environments.
- Validated results through comparison with reference coordinates and predicted paths.

---

## Project Structure
```
├── src/
│   ├── kalman_filter.c
│   ├── fuzzy_logic_lat.c
│   ├── fuzzy_logic_lon.c
│   └── gps_utils.c
├── data/
│   └── gps_test_cases.csv
├── matlab/
│   └── anfis_models.fis
├── include/
│   └── headers.h
└── README.md
```

---

## How to Run
1. **Compile the C code** using any standard compiler:
   ```bash
   gcc -o gps_correction main.c kalman_filter.c gps_utils.c -lm
   ```

2. **Run the program** with your input GPS data file:
   ```bash
   ./gps_correction data/gps_test_cases.csv
   ```

3. To retrain ANFIS models, use MATLAB:
   - Load `anfis_models.fis` in the MATLAB Fuzzy Logic Designer.
   - Use GPS error training data to fine-tune the correction rules.

---

## Technologies Used
- **C** (for system-level implementation)
- **MATLAB** (for ANFIS and fuzzy system modeling)
- **GPS/PDOP/HDOP** theory for spatial error modeling
- **Kalman Filters** for predictive localization
- **Fuzzy Logic & ANFIS** for intelligent compensation

---

## Contact for Access
This repository is private. If you’d like to view the full code or discuss collaboration, feel free to contact me via:

- 📧 [ksheeraj.prakash@gmail.com](mailto:ksheeraj.prakash@gmail.com)  
- 💼 [LinkedIn](https://www.linkedin.com/in/ksheerajprakash)

---
