# FOOTSIES: Reinforcement Learning Agent for 2D Fighting Games

## Overview
This project implements a reinforcement learning (RL) agent capable of playing the 2D fighting game **FOOTSIES** using a deep Q-learning architecture. The agent observes game frames, interprets spatial states using a Convolutional Neural Network (CNN), and makes decisions using a Deep Q-Network (DQN). The project demonstrates real-time strategic behavior such as blocking, spacing, and attacking.

---

## Features
- Visual state extraction using OpenCV and grayscale preprocessing.
- Frame stacking for temporal awareness.
- Deep Q-Network (DQN) with epsilon-greedy exploration strategy.
- Action space: Move Left, Move Right, Standard Attack, Charged Attack.
- Reward structure based on game win, shield loss, and survival time.
- Real-time keystroke control for game simulation.

---

## Architecture
- **CNN**: Extracts spatial features from stacked frames.
- **DQN**: Maps state-action pairs to Q-values to guide action selection.
- **Experience Replay**: Stores transitions for stable learning.
- **Target Network**: Updates every N episodes for Q-value stability.

### Hyperparameters
- Learning Rate: 0.001  
- Discount Factor (γ): 0.99  
- Epsilon Decay Rate: 0.9995  
- Memory Capacity: 10,000  
- Batch Size: 64  
- Episodes: 1000  
- Target Network Update Frequency: 5 Episodes

---

## Results
- Demonstrated strategic combat behavior across 1000+ episodes.
- Observed defensive blocking, spacing, and timing of charged attacks.
- Cumulative rewards show learning patterns, though with room for improvement.
- Real-time decision-making with ~3 actions/sec on limited hardware.

---

## How to Run
1. Clone the repository and install required dependencies:
   ```bash
   pip install -r requirements.txt
