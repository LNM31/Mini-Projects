# Flappy Bird

A browser-based Flappy Bird clone built with vanilla JavaScript and the HTML5 Canvas API.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Canvas API](https://img.shields.io/badge/Canvas_API-FF6F00?style=for-the-badge&logo=html5&logoColor=white)

## Demo

<!-- PLACEHOLDER: Replace with a GIF of actual gameplay — drag & drop into the GitHub editor -->
![Gameplay](https://via.placeholder.com/360x640?text=Gameplay+GIF+Placeholder)

## How to Run

```bash
git clone https://github.com/<your-username>/Flappy-Bird.git
cd Flappy-Bird
```

Open `index.html` in your browser — no build tools or server required.

## Controls

| Key | Action |
|---|---|
| `Space` | Jump / Restart |
| `Arrow Up` | Jump / Restart |
| `X` | Jump / Restart |

## Features

- Smooth 60 FPS gameplay powered by `requestAnimationFrame`
- Gravity-based physics with natural jump arcs
- Procedurally generated pipe obstacles with randomized gaps
- AABB (Axis-Aligned Bounding Box) collision detection
- Live score tracking
- Instant restart on game over

## How It Works

**Canvas Rendering** — The game renders on a 360x640 canvas. Each frame clears the screen and redraws the bird, pipes, and score overlay. The background is applied via CSS to keep the render loop lightweight.

**Gravity & Physics** — The bird has a vertical velocity that increases every frame by a gravity constant (`0.23`). Pressing jump sets the velocity to `-6`, creating a smooth upward arc that gravity pulls back down.

**Pipe Generation** — Every 1.5 seconds, a top and bottom pipe pair spawns at the right edge with a randomized vertical position and a 160px gap between them. Pipes scroll left at a constant speed and are removed once off-screen.

**Collision Detection** — Each frame checks whether the bird's bounding box overlaps with any pipe using four-axis overlap conditions. Falling below the canvas also ends the game.

## Project Structure

```
Flappy-Bird/
├── index.html          # Entry point
├── flappybird.css      # Canvas and layout styles
├── flappybird.js       # Game logic — physics, rendering, input
├── flappybird.png      # Bird sprite
├── flappybirdbg.png    # Background image
├── toppipe.png         # Top pipe sprite
└── bottompipe.png      # Bottom pipe sprite
```
