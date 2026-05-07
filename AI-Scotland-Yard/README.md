# AI-Driven Scotland Yard Game Simulation

## Overview

This project is a full-stack AI-powered adaptation of the Scotland Yard board game, where intelligent agents compete against each other across a digital map of London. Mr. X tries to stay hidden and evade capture, while a team of Detectives work together to track him down. The entire game from movement and strategy to multiplayer support and analytics is handled automatically by the system.

What makes this project unique is the asymmetric AI design. Mr. X and the Detectives don't use the same strategy but they each have a completely different AI approach that reflects how each role actually plays in the real board game. You can play against the AI, watch two AIs compete, or run hundreds of simulated games to analyze outcomes and strategies.

## Accessing the Code

If you're interested in exploring the full source code, documentation, or setup instructions, feel free to reach out for access for interviews, collaboration, or evaluation purposes.

- **LinkedIn:** [linkedin.com/in/ksheerajprakash](https://www.linkedin.com/in/ksheerajprakash)
- **Email:** ksheerooo@gmail.com

🔗 GitHub Repository (private): [github.com/KsheerajP/AI-Scotland-Yard](https://github.com/KsheerajP/AI-Scotland-Yard.git)

## How It Works

The game is built in layers, each handling a different part of the system.

**Graph Engine (C + Python)**
The foundation of the game is a high-performance pathfinding engine written in C, integrated into Python via pybind11. It models all 199 London stations and 4 transport modes (Taxi, Bus, Underground, Ferry) as a graph, and uses BFS and Dijkstra's algorithm to compute routes and distances. This runs in sub-milliseconds and powers all AI decision-making in real time.

**Mr. X — Q-Learning Agent**
Mr. X is controlled by a pre-trained reinforcement learning agent using Q-learning. Over thousands of training episodes, the agent learned which moves lead to successful escapes and which lead to capture. It maintains a Q-table with 100K+ state-action mappings, considers its distance from each detective, remaining tickets, and upcoming reveal turns, and uses a shaped reward system to balance survival, evasion, and risky moves like secret and double tickets.

**Detectives — Monte Carlo Tree Search**
Each detective uses Monte Carlo Tree Search (MCTS) to plan moves. Instead of reacting greedily, the detective AI simulates 100 possible future game states per move across a 4-turn horizon, then picks the move with the best average outcome. This makes the detectives coordinate naturally by spreading out, cutting off escape routes, and closing in as the round limit approaches.

**Backend and Multiplayer**
All game logic runs on a FastAPI backend with real-time WebSocket support, so moves are broadcast instantly across all players. Redis stores live game state, and if a player disconnects mid-game, the AI automatically takes over their position by keeping the game running without interruption. The whole system is containerized with Docker for easy deployment.

**Frontend**
The game board is rendered using React and Pixi.js, showing all 199 London stations as an interactive map with real-time position updates, ticket counts, and turn history.

## Results

The system was benchmarked across **406 full-length AI-controlled games** under randomized starting conditions. Here are the key findings:

**Win Rates:**
- Detectives won **77.34%** of games (341 wins) by effectively coordinating pursuit using MCTS-based routing
- Mr. X evaded capture in **20.44%** of games (83 wins), relying on secret moves, double tickets, and evasive zoning
- **2.22%** of games (9 games) were incomplete due to forced simulation terminations

**Ticket Usage (15,637 total moves):**
- Taxi: 11,232 uses (71.8%) — most common, short-range movement
- Bus: 3,641 uses (23.3%) — medium-range coverage
- Underground: 763 uses (4.9%) — fast long-range jumps
- Secret Tickets: 31 uses — deployed by Mr. X to hide transport type at critical moments

**Game Metrics:**
- Average game length: **8.33 rounds** before capture or timeout
- AI takeovers: **80+ instances** across 406 games (~16.6 per game), ensuring every game completed without manual input

These results show that the detective AI consistently outperforms Mr. X under standard conditions, though Mr. X's win rate increases noticeably when secret and double tickets are used strategically in the mid-game.
