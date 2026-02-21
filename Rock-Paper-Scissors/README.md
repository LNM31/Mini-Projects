# Rock Paper Scissors

A classic Rock Paper Scissors game built with vanilla JavaScript, featuring score persistence, keyboard controls, and an AutoPlay mode.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

<!-- Add screenshot: drag & drop in GitHub editor -->
![Screenshot](https://via.placeholder.com/800x450?text=Screenshot+Placeholder)

## Tech Stack

- **HTML5** — Structure & layout
- **CSS3** — Dark theme styling with circular button design
- **JavaScript** — Game logic, DOM manipulation, localStorage

## How to Run

No dependencies or build tools required — just static files.

```bash
git clone https://github.com/LNM31/Mini-Projects.git
cd <repo-name>
```

Open `12-rock-paper-scissors.html` in your browser.

## Controls

| Action | Button | Keyboard |
|--------|--------|----------|
| Rock | ![rock](Images/rock-emoji.png) | `R` |
| Paper | ![paper](Images/paper-emoji.png) | `P` |
| Scissors | ![scissors](Images/scissors-emoji.png) | `S` |

- **Reset Score** — Clears win/loss/tie counts and removes saved data
- **AutoPlay** — Toggles automatic play (random moves every second)

## Features

- **Score Persistence** — Wins, losses, and ties are saved to `localStorage` and survive browser refreshes
- **Keyboard Shortcuts** — Press `R`, `P`, or `S` to play instantly without clicking
- **AutoPlay Mode** — Toggle continuous random rounds at 1-second intervals
- **Dark Theme** — Sleek dark UI with circular move buttons

## Project Structure

```
Rock-Paper-Scissors/
├── 12-rock-paper-scissors.html   # Main page
├── 12-rock-paper-scissors.css    # Styles
├── 12-rock-paper-scissors.js     # Game logic
├── Images/
│   ├── rock-emoji.png
│   ├── paper-emoji.png
│   └── scissors-emoji.png
└── README.md
```
