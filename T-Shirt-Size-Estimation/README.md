# T-Shirt Size Estimation Using Monocular Camera Images

## Overview
This project presents a computer vision pipeline that estimates a person's T-shirt size using just a single image from a monocular camera. It aims to solve a common challenge in online retail: determining accurate clothing sizes without the need for physical trials or measurements.

## Accessing the Code
If you're interested in exploring the full source code of this project, feel free to reach out to me via [LinkedIn](https://www.linkedin.com/in/ksheerajprakash) or email me at `ksheerooo@gmail.com`. I’ll be happy to provide access upon request.

🔗 GitHub Repository (private): [https://github.com/KsheerajP/T-Shirt-Size-Estimation](https://github.com/KsheerajP/T-Shirt-Size-Estimation.git)

## How It Works
- The system uses **MediaPipe** for detecting key body landmarks from an image.
- It applies **Perspective Geometry Correction** to adjust for camera angle and distance.
- Finally, a **Deep Learning Model** trained on real-world anthropometric data predicts the user’s measurements.
- Based on these predictions, the system classifies the best-fitting T-shirt size (XS to XL+).

The solution supports both static images and video frames, making it suitable for integration into e-commerce apps or virtual fitting rooms.

## Results
- Achieved up to **89% accuracy** for front-facing, non-obstructed inputs.
- The DL-based approach outperformed baseline and geometric methods in varied lighting and background conditions.
- Effectively categorized users into standard clothing sizes with high reliability.
