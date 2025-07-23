# AI-Driven Scotland Yard Game Simulation

## Overview

This project is a digital simulation of the classic *Scotland Yard* board game powered by AI agents and graph-based pathfinding. The core logic is written in C for performance and exposed to Python using `pybind11`. A Python backend (FastAPI + Redis) powers both human and AI-driven multiplayer games via WebSockets and command-line interfaces.

---

## Accessing the Code

If you're interested in trying out the game or running AI experiments, feel free to contact me:

📧 Email: ksheerooo@gmail.com  
🔗 GitHub (Private): [https://github.com/VSJ001/scotland-yard](https://github.com/VSJ001/scotland-yard)

---

## How It Works

- **Graph Engine**: London’s map is modeled using an adjacency list in C (`Graph` struct).
- **Algorithms**: Implements both BFS and Dijkstra's for reachability and shortest path.
- **Binding**: Uses `pybind11` to expose native C code as a Python module (`graph_engine.pyd`).
- **Game Logic**: FastAPI backend manages players, turns, visibility, and tickets.
- **WebSocket Support**: Enables real-time communication for multiplayer mode.
- **AI Integration**:
  - Greedy Detective AI (shortest path)
  - Mr. X AI (Q-learning, zoning, escape tactics)
- **CLI Support**:
  - Play manually or simulate 100s of games
  - AI takeover for disconnected players or inactive turns

---

## Game Rules Summary

- **Roles**:
  - **Mr. X**: Must evade detectives for 22–24 turns
  - **Detectives**: Must land on Mr. X’s station to win

- **Transport & Tickets**:
  - Modes: Taxi (T), Bus (B), Underground (U), Ferry (F)
  - Mr. X only: Secret (S), Double Move (D)

- **Visibility**:
  - Mr. X reveals location on turns: 3, 8, 13, 18, 24
  - Detectives are always visible

- **Victory**:
  - Detectives win by catching Mr. X
  - Mr. X wins by escaping all turns or stranding all detectives

---

## Results

- **Games Simulated**: 406
- **Mr. X Win Rate**: 20.44%
- **Detectives Win Rate**: 77.34%
- **AI Takeovers**: ~16.6 per game on average
- **Average Rounds Played**: 8.33

---

## Requirements

- Python 3.10+
- CMake
- GCC
- `pybind11`
- Redis
- FastAPI, Uvicorn

---

## Run Instructions

```bash
# Clone the repo and set up environment
git clone https://github.com/VSJ001/scotland-yard.git
cd scotland-yard
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt

# Build the graph engine
cd graph_engine
mkdir build && cd build
cmake ..
cmake --build . --config Release

# Start the backend server
cd ../../
uvicorn backend.main:app --reload

# Play a full CLI game
python simulation/run_full_game.py

# Run 100 AI-only simulations
python simulation/run_simulations.py
