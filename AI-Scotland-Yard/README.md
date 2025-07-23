# AI-Driven Scotland Yard Game Simulation

## Overview

This project is a digital simulation of the classic *Scotland Yard* board game powered by AI agents and graph-based pathfinding. The core logic is written in C for performance and exposed to Python using `pybind11`. A Python backend (FastAPI + Redis) powers both human and AI-driven multiplayer games via WebSockets and command-line interfaces.

## Accessing the Code
If you're interested in exploring the full complete code of this project, feel free to reach out to me via 
[LinkedIn](https://www.linkedin.com/in/ksheerajprakash) or email me at `ksheerooo@gmail.com`. I’ll be happy to provide access upon request.

🔗 GitHub Repository (private): [https://github.com/KsheerajP/Emotion-Detection-and-Music-Selection.git](https://github.com/KsheerajP/Emotion-Detection-and-Music-Selection.git)

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

## Results

- **Games Simulated**: 406
- **Mr. X Win Rate**: 20.44%
- **Detectives Win Rate**: 77.34%
- **AI Takeovers**: ~16.6 per game on average
- **Average Rounds Played**: 8.33



