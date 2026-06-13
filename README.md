# Catan Cards Tracker

> **A childhood project built to track the state, resources, and hidden information of a Settlers of Catan game.**

This repository contains a desktop application I wrote when I was younger. The goal of the project was to create a digital companion app for a physical game of Catan that could track what resources every player had, handle dice rolls, and calculate possible hidden card combinations. 

While the codebase is a snapshot of my early programming days, it represents an attempt to model board game mechanics, state tracking, and GUI event handling in C++.

## Features

* **Interactive Board Setup:** Reads a custom board code string to generate the 19 hexes, their resource types, and their dice tokens.
* **Probability & Combination Tracking:** Tracking of player hands. When hidden cards are stolen or discarded, the app calculates and tracks the different possible `resourceCombinations` a player might be holding.
* **Full Turn Mechanics:** UI buttons and logic for:
    * Rolling dice and distributing resources automatically.
    * Building (Roads, Settlements, Cities).
    * Buying and spending Development Cards (Knight, Monopoly, Year of Plenty).
    * Trading (Player-to-Player and Player-to-Bank).
    * Moving the Robber and stealing cards.
* **State History / Undo System:** Utilizes a `std::stack` to save snapshots of the `Board` and `Player` objects, allowing users to undo actions and revert to previous game states.

## Tech Stack

* **Language:** C++
* **Framework:** Qt (QtWidgets) for the Graphical User Interface.

## File Architecture

Since the repository does not use a nested folder structure, here is a conceptual breakdown of how the source files work together:

| Category | Files | Description |
| :--- | :--- | :--- |
| **Game State & Logic** | `board.cpp` / `.h` | Manages the 19 hexes, their resource values, dice numbers, and robber placement. |
| | `player.cpp` / `.h` | Tracks individual player data: owned spaces, development cards, and their possible resource combinations. |
| | `resources.cpp` / `.h` | A custom struct with operator overloading (`+`, `-`, `+=`) to easily manage Lumber, Brick, Wool, Grain, and Ore. |
| | `actions.cpp` / `.h` | The core rules engine. Contains the logic for building, trading, monopolies, and robber interactions. |
| **Graphical Interface** | `widget.cpp` / `.h` | The main Qt window class handling all UI events, button clicks, and rendering the board state. |
| | `widget.ui` | The XML-based Qt Designer layout file outlining the UI grid, buttons, and scrolling areas. |
| | `widget.qrc` | The Qt Resource Collection file linking to local image assets (hexes, resources, buttons). |
| **Application Entry** | `main.cpp` | Initializes the `QApplication`, mounts the `widget`, and starts the Qt event loop. *(Also includes legacy console-based logic in comments)* |

## How to Run

To run this project, you will need the **Qt framework** installed on your machine.

1. Clone the repository.
2. Open the project directory in **Qt Creator**.
3. Generate a `.pro` or `CMakeLists.txt` file (if one is not present) and include all `.cpp`, `.h`, `.ui`, and `.qrc` files.
4. Build and run the project using your local C++ compiler. 

---
*Note: This is an archived project kept for historical and portfolio purposes.*
