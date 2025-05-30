# Vehicle-to-Vehicle Communication Using IoT

## Overview
This project implements an intelligent vehicular communication system leveraging **IoT** and **VANETs** (Vehicular Ad-hoc Networks). It enables real-time communication between vehicles (V2V) and between vehicles and infrastructure (V2I) to facilitate **accident alerts**, **dynamic route selection**, and **emergency vehicle prioritization**.

The system utilizes GPS, GSM modules, and microcontrollers to simulate real-world traffic scenarios and provide safety-critical updates among vehicles.

---

## Features
- Real-time **accident detection** and automatic alert generation.
- **Vehicle-to-Vehicle (V2V)** and **Vehicle-to-Infrastructure (V2I)** communication protocols.
- **Dynamic routing** and congestion avoidance for emergency response.
- Integration with **Arduino Uno**, **GPS (Neo6M)**, and **GSM (SIM800L)** modules.
- Testbed simulation for **multi-node traffic and emergency** scenarios.

---

## Hardware Components
- Arduino Uno microcontroller
- Neo6M GPS module
- SIM800L GSM module
- Accelerometer (for crash detection)
- LEDs and buzzers for notifications
- Power supply and vehicle mock prototypes

---

## Implementation
1. Each vehicle node is equipped with GPS and GSM modules.
2. On detecting an accident via the accelerometer, the GPS coordinates are sent via GSM to nearby vehicles or a control unit.
3. Other vehicles adjust their route based on proximity and status of the affected node.
4. Centralized system can issue alerts for ambulance routing and traffic control.

---

## Results
- Successful delivery of alerts within **2-3 seconds** in test environments.
- Demonstrated effective **real-time routing** updates and emergency response handling.
- Validated **low-latency communication** across multiple nodes.

---

## Use Case
This system can be extended to:
- Smart city traffic systems
- Emergency response coordination
- Intelligent traffic light control and signal prioritization

---

## How to Run
The system runs on Arduino IDE. Each vehicle node has a corresponding `.ino` file:
1. Load the code into the Arduino using Arduino IDE.
2. Connect sensors and modules as per the circuit diagram.
3. Power each vehicle node separately and monitor GSM messages and GPS coordinates.

---

## Contact
If you would like access to the code or additional documentation, feel free to contact me via [LinkedIn](https://www.linkedin.com/in/ksheerajprakash/) or email.  
🔗 GitHub repo: [https://github.com/KsheerajP/Vehicle-Communication-IoT](https://github.com/KsheerajP/Vehicle-Communication-IoT)
"""
