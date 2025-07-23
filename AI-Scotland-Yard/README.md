# AI-Driven Scotland Yard Game Simulation

## Overview

This project is a digital simulation of the classic *Scotland Yard* board game powered by AI agents and graph-based pathfinding. The core logic is written in C for performance and exposed to Python using `pybind11`. A Python backend (FastAPI + Redis) powers both human and AI-driven multiplayer games via WebSockets and command-line interfaces.

## Accessing the Code
If you're interested in exploring the full complete code of this project, feel free to reach out to me via 
[LinkedIn](https://www.linkedin.com/in/ksheerajprakash) or email me at `ksheerooo@gmail.com`. I’ll be happy to provide access upon request.

🔗 GitHub Repository (private): [https://github.com/KsheerajP/AI-Scotland-Yard.git](https://github.com/KsheerajP/AI-Scotland-Yard.git)

## How It Works

The Scotland Yard simulation models the London game board as a graph in C using an adjacency list, with each node representing a station and each edge representing a transport route (Taxi, Bus, Underground, Ferry). The system is designed for speed and efficiency:

- **Graph Engine in C**: The map is built using custom structures (`Graph`, `Station`, and `Edge`) optimized for traversal and memory usage. Graph connections are loaded from a `.txt` file into the engine.

- **Pathfinding Algorithms**:  
  - **Breadth-First Search (BFS)** is used for quickly identifying reachable stations for move validation.  
  - **Dijkstra’s Algorithm** is applied to calculate shortest paths, aiding both detective pursuit and Mr. X’s evasion strategy.

- **Python Integration via pybind11**:  
  The C-based graph module is compiled and exposed to Python as a `graph_engine` extension, allowing Python logic to interact with low-level data structures and algorithms efficiently.

- **Game Logic (Python Backend)**:  
  The backend uses FastAPI to handle player movement, visibility rules, ticket tracking, and game progression. Redis provides real-time, in-memory state updates and messaging between clients via WebSockets.

- **AI Agents**:  
  - **Detectives** use greedy strategies based on shortest paths to chase Mr. X.  
  - **Mr. X** employs reinforcement learning (Q-Learning) with a zoning strategy to escape or mislead pursuers.  
  - AI automatically takes over when a player is disconnected or inactive, ensuring uninterrupted gameplay.

- **CLI and Simulation Interface**:  
  - Players can play through a command-line interface, which prompts for legal moves based on current station and ticket inventory.  
  - Developers can simulate hundreds of games using automated scripts for benchmarking and AI evaluation.


## Results

The simulation framework was tested over **406 full-length AI-controlled games** under randomized conditions. The following key observations were recorded:

- **Win Rate Analysis**:
  - **Mr. X** successfully evaded capture in **20.44%** of games (83 wins), using a mix of secret moves, zoning, and double tickets.
  - **Detectives** won in **77.34%** of games (341 wins) by coordinating using shortest-path strategies.
  - **2.22%** of games (9 games) were incomplete or inconclusive due to forced terminations during simulation.

- **Ticket Usage Insights**:
  - **Taxi** was the most commonly used transport, with over **11,232** uses.
  - **Bus** followed with **3,641** uses, and **Underground** had **763** uses.
  - **Secret tickets** (used by Mr. X) were deployed **31 times**, reflecting occasional stealthy escapes.

- **AI Responsiveness**:
  The AI takeover mechanism handled disconnections gracefully, with an average of **16.6 player takeovers per game** distributed across all five players. This ensured that games continued even when manual input was unavailable.

- **Game Length**:
  The average game lasted **8.33 turns**, with early captures occurring frequently due to optimized detective routing and limited evasive options on a dense map.

These results show that the game environment provides a realistic, strategic challenge for both AI and human players. The backend and AI integration demonstrate robust real-time decision-making and smooth failover handling during gameplay.



