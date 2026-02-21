# Snake

A classic Snake game built as a desktop application in Java using Swing and AWT.

![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Swing](https://img.shields.io/badge/Swing-007396?style=for-the-badge&logo=java&logoColor=white)

<!-- PLACEHOLDER: Add gameplay GIF here — drag & drop in the GitHub editor -->
![Gameplay](https://via.placeholder.com/600x600?text=Gameplay+GIF+Placeholder)

## Tech Stack & Architecture

| Component | Technology |
|-----------|------------|
| Language | Java |
| GUI Framework | Swing (`JPanel`, `JFrame`) |
| Rendering | AWT `Graphics` with 3D-style rectangles |
| Game Loop | `javax.swing.Timer` at 100 ms intervals |
| Input | `KeyListener` for arrow key controls |
| Data Structure | `ArrayList<Tile>` for the snake body |

### Game Architecture

The game follows a straightforward **timer-driven game loop** pattern:

```
Timer tick (100ms)
  └─ move()
      ├─ Check food collision → grow snake, respawn food
      ├─ Shift body segments forward
      ├─ Update head position by velocity
      └─ Check game-over conditions (wall / self collision)
  └─ repaint()
      └─ draw()
          ├─ Render food (red 3D rect)
          ├─ Render snake head + body (green 3D rects)
          └─ Draw score or "Game Over" text
```

`App` creates the window and hands off to `Game`, which owns all game state and rendering. A nested `Tile` class represents grid coordinates for the snake and food. The board is a **24 x 24 grid** (600 px / 25 px tile size) rendered on a black background.

## Prerequisites

You need a **Java Development Kit (JDK) 8** or higher installed.

**Windows (winget):**

```bash
winget install Oracle.JDK.17
```

**macOS (Homebrew):**

```bash
brew install openjdk@17
```

**Linux (apt):**

```bash
sudo apt update && sudo apt install openjdk-17-jdk
```

Verify the installation:

```bash
java -version
javac -version
```

## How to Compile & Run

**1. Clone the repository:**

```bash
git clone https://github.com/LNM31/Mini-Projects.git
cd Snake
```

**2. Compile:**

```bash
javac -d bin src/*.java
```

**3. Run:**

```bash
java -cp bin App
```

The game window will open and the snake starts moving immediately.

## Controls

| Key | Action |
|-----|--------|
| `↑` | Move up |
| `↓` | Move down |
| `←` | Move left |
| `→` | Move right |

> The snake cannot reverse direction — pressing the opposite key of the current direction is ignored.

## Key Features

- **Smooth game loop** — Timer-driven updates at 10 FPS for consistent movement
- **Collision detection** — Wall boundaries and self-collision end the game
- **Dynamic food spawning** — Food appears at random grid positions after being eaten
- **Score tracking** — Live score displayed during play; final score shown on game over
- **3D-style rendering** — `fill3DRect` gives the snake and food a raised, tactile look
- **Direction guard** — Prevents instant 180-degree reversal that would cause self-collision

## Project Structure

```
Snake/
├── src/
│   ├── App.java          # Entry point — creates the JFrame window
│   └── Game.java         # Core game logic, rendering, and input handling
│       └── Tile (inner)  # Simple (x, y) coordinate pair for grid positions
├── bin/                   # Compiled .class files
└── README.md
```

| Class | Responsibility |
|-------|----------------|
| `App` | Initializes a 600x600 `JFrame`, adds the `Game` panel, and starts the application |
| `Game` | Extends `JPanel`; manages the snake, food, movement, collision detection, scoring, and rendering |
| `Game.Tile` | Inner class representing a single grid cell coordinate (`x`, `y`) |
