# Todo List

A clean, browser-based todo list app built with vanilla JavaScript, CSS Grid, and HTML.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

---

<img width="993" height="562" alt="Demo" src="https://github.com/user-attachments/assets/427b01bf-86ef-4b50-9a4f-b7ed87eceb00" />

---

## Tech Stack

| Layer  | Technology         |
| ------ | ------------------ |
| Markup | HTML5              |
| Style  | CSS3 (Grid Layout) |
| Logic  | Vanilla JavaScript |

## Features

- Add todos with a name and due date
- Delete individual todos with a single click
- Dynamic rendering — the list updates instantly without page reloads
- CSS Grid layout for aligned, structured rows
- Pre-populated sample tasks for quick demonstration

## How to Run

No build tools or dependencies required — just static files.

```bash
git clone https://github.com/LNM31/Mini-Projects.git
cd Todo-List-Project
```

Open `12-todo-list.html` in your browser, and you're good to go.

## Project Structure

```
Todo-List-Project/
├── 12-todo-list.html   # Main HTML page
├── 12-todo-list.css    # Grid layout and button styles
├── 12-todo-list.js     # Todo logic — add, delete, render
└── README.md
```

## How It Works

1. **Rendering** — `renderTodoList()` rebuilds the entire list from the `todoList` array using template literals and injects it into the DOM.
2. **Adding** — The "Add" button reads the name and date inputs, pushes a new object to the array, clears the input, and re-renders.
3. **Deleting** — Each "Delete" button is bound to its index via `forEach`; clicking it splices the item from the array and re-renders.
