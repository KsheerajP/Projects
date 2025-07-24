# AI-Driven Scotland Yard Game Simulation

## Overview

This project is a digital version of the Scotland Yard board game, where computer players move around a map of London. You can play against the AI or watch the computer play both sides. Detectives try to catch Mr. X, who uses different moves to hide and escape. The system handles the flow of the game and decides each player’s actions, making it easy to see how different strategies play out as the game progresses.

## Accessing the Code
If you're interested in exploring the full complete code of this project, feel free to reach out to me via 
[LinkedIn](https://www.linkedin.com/in/ksheerajprakash) or email me at `ksheerooo@gmail.com`. I’ll be happy to provide access upon request.

🔗 GitHub Repository (private): [https://github.com/KsheerajP/AI-Scotland-Yard.git](https://github.com/KsheerajP/AI-Scotland-Yard.git)

## How It Works

This project digitally recreates the Scotland Yard board game, enabling both AI and human players to move across a map of London, with each station and route managed by a fast C-based graph engine exposed to Python. The backend handles all turns, player decisions, and game rules in real time, using web technologies for multiplayer support. AI detectives plan their moves to corner Mr. X, who uses adaptive strategies to escape, and the whole system can automatically fill in for missing players

 - The map and pathfinding are powered by a high-speed C graph engine, seamlessly integrated into Python.

 - Detectives use MCTS-based AI to coordinate pursuit, while Mr. X uses reinforcement learning to learn escape strategies over many games.

 - All game logic, multiplayer functionality, and analytics are managed by a FastAPI backend, and the platform runs in Docker for easy deployment anywhere.

Anyone can play against smart AI or watch AI vs. AI games, with the system automatically handling all aspects of gameplay and strategy.
    
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




