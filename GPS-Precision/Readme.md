# Techniques to Improve GPS Precision

## Overview
This project explores a range of software-based methods to enhance GPS accuracy, especially in environments with high error margins such as urban or low-signal zones. It combines mathematical modeling, dynamic filtering, and fuzzy logic to reduce location errors and provide more precise positioning data for mobile systems.

## Accessing the Code
If you're interested in exploring the complete code of this project, feel free to reach out to me via [LinkedIn](https://www.linkedin.com/in/ksheerajprakash) or email me at `ksheerooo@gmail.com`. I’ll be happy to provide access upon request.

🔗 GitHub Repository (private): [https://github.com/KsheerajP/GPS-Precision](https://github.com/KsheerajP/GPS-Precision.git)

## How It Works
The system improves raw GPS data by applying multiple correction techniques, including:

- **Kalman Filtering** to reduce noise and predict more accurate location updates over time.
- **Fuzzy Logic Controllers** to dynamically adjust latitude and longitude based on sensor trends.
- **Error Direction Estimation** to detect the direction of deviation and compensate accordingly.
- **Differential GPS (DGPS)** and **Assisted GPS (A-GPS)** concepts to analyze and reduce positional drift in test scenarios.

Using custom calculations, the system determines the deviation between actual and predicted positions and applies compensation models to improve precision with each update.

## Results
- Achieved reduction in average location error from several meters to within **0.2–1 meter** in 95% of test cases.
- Demonstrated improvement in positional stability using enhanced filtering and error modeling.
- System maintained accuracy in low-signal or urban environments where standard GPS struggled.
