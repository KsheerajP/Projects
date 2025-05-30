# GPS Precision Enhancement Using Kalman Filter

## Overview
This project focuses on enhancing the accuracy of GPS location data using a **Kalman Filter**. Raw GPS data, often prone to noise and fluctuation due to environmental and satellite-related factors, is filtered and smoothed to produce more stable and precise location tracking.

The project demonstrates how statistical filtering can significantly improve positional accuracy, making it suitable for applications in navigation, tracking, and mobile robotics.

---

## Features
- Real-time acquisition and logging of GPS data from GPS module.
- Implementation of a **Kalman Filter** for smoothing latitude and longitude values.
- Comparison of raw vs filtered GPS paths.
- Designed for embedded platforms (e.g., Arduino, ESP32) but also adaptable to desktop simulations.
- Low-latency filtering suitable for mobile and vehicular applications.

---

## Hardware Used
- GPS Module (e.g., NEO-6M, u-blox)
- Arduino UNO / ESP32 microcontroller
- Serial monitor or SD card module for data logging (optional)

---

## Software Stack
- C / C++ for microcontroller programming
- Python or MATLAB (optional) for post-processing and plotting
- Arduino IDE for firmware development

---

## Kalman Filter Model
- State Vector: [Latitude, Longitude]
- Assumes constant velocity model
- Measurement update based on new GPS readings
- Tuning parameters (Process Noise `Q` and Measurement Noise `R`) manually calibrated based on empirical testing

---

## Results
- **50–70% reduction in GPS jitter** in open environments.
- **Noticeably smoother paths** in vehicle and pedestrian movement tests.
- Increased stability in low-satellite or partially obstructed conditions.

---

## How to Run
1. Upload the Arduino sketch to your board with the GPS module connected.
2. Monitor the Serial output to view real-time filtered coordinates.
3. Optionally, log the results and visualize using a plotting tool.

---

## Applications
- Vehicle tracking and navigation
- Fleet management systems
- Autonomous drones or delivery bots
- Sports and fitness tracking apps

---

## Repository Access
If you'd like to view the full source code or reproduce the results, please reach out to me on [LinkedIn](https://www.linkedin.com/in/ksheerajprakash/) or email me at ksherajprakash@gmail.com.

🔗 **Private Repository Link**: [GPS-Precision-Kalman-Filter (Private Repo)](https://github.com/KsheerajP/GPS-Precision-Kalman-Filter)

---

## Skills Used
C/C++ · Embedded Systems · Kalman Filter · GPS · Arduino · Signal Filtering · Real-Time Systems
