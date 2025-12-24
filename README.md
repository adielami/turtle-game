# 🐢 Turtle Crossing - Arcade Game

A Python-based arcade game inspired by the hit "Crossy Road".
Built using the **Turtle** graphics library, this project focuses on **Object-Oriented Programming (OOP)** to manage multiple independent game entities simultaneously.

The player controls a turtle attempting to cross a busy highway where car speed and density increase with every successful level.

---

## ⚡ Key Features

### 🚗 Dynamic Obstacle Management
* **The Car Manager:** A dedicated class responsible for spawning cars at random vertical positions and controlling their movement speed.
* **Randomization:** Utilizes Python's `random` module to generate varied car colors and spawn intervals, ensuring no two game sessions are alike.
* **Garbage Collection:** Optimizes memory by conceptually removing cars that have moved off-screen (though Python handles the memory, the logic ignores them).

### 📈 Level Progression
* **Difficulty Scaling:** Upon reaching the finish line, the level resets, but the car speed increases, making the game progressively harder.
* **Score Tracking:** Displays the current level dynamically on the screen.

### 💥 Collision System
* **Hit Detection:** Continuously calculates the Euclidean distance between the player instance and every active car instance to detect impacts.

---

## 🛠️ Tech Stack & Concepts

| Component | Technology | Concept Demonstrated |
|-----------|------------|----------------------|
| **Language** | **Python 3.x** | OOP, Classes & Instances |
| **Graphics** | **Turtle** | Cartesian Coordinates, Screen Refresh |
| **Architecture** | **Manager Pattern** | `CarManager` class controlling multiple `Car` objects |
| **Animation** | **Tracer Method** | Disabling auto-updates for smooth animation frames |

---

## 🔬 How It Works (The Logic)

### 1. The Car Manager Pattern
Instead of writing code for every single car, I created a `CarManager` class.
* **Generation:** Every 6th game loop (statistically), a new car object is instantiated and added to a list `all_cars`.
* **Movement:** A simple `for` loop iterates through `all_cars` moving each one backward along the X-axis.
* **Encapsulation:** All car-related logic (speed, color, position) is hidden inside this class, keeping the `main.py` clean.

### 2. Smooth Rendering (The `tracer` trick)
Standard Turtle graphics are slow because they draw every step.
To achieve arcade-like smoothness, I used:
```python
screen.tracer(0) # Turn off automatic animation
# ... game logic ...
screen.update()  # Manually refresh the screen once per loop
