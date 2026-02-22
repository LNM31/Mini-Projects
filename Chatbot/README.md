<div align="center">

# Chatbot

A real-time chatbot web app with persistent conversations, built with React 19 and TypeScript.

![React](https://img.shields.io/badge/React-19.1-61DAFB?style=flat&logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5.8-3178C6?style=flat&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-6.3-646CFF?style=flat&logo=vite&logoColor=white)
![React Compiler](https://img.shields.io/badge/React_Compiler-19.1_RC-149ECA?style=flat&logo=react&logoColor=white)
![dayjs](https://img.shields.io/badge/dayjs-1.11-FF5F6D?style=flat)

</div>

---

<img width="1566" height="1743" alt="Demo" src="https://github.com/user-attachments/assets/8e4cc6d1-182f-4c22-ae53-643357b3b802" />

## Tech Stack

| Category | Technology |
|----------|------------|
| **Framework** | React 19 with automatic JSX transform |
| **Language** | TypeScript (strict mode) |
| **Build Tool** | Vite 6 with HMR |
| **Compiler** | React Compiler via `babel-plugin-react-compiler` |
| **Date Formatting** | dayjs (lightweight Moment.js alternative) |
| **Chatbot Engine** | `supersimpledev` library for response management |
| **Linting** | ESLint 9 + TypeScript ESLint + React Hooks plugin |

## Prerequisites

Make sure you have **Node.js** installed on your machine.

```bash
# Check if Node.js is installed
node --version

# If not installed, download from:
# https://nodejs.org/
```

## Getting Started

```bash
# Clone the repository
git clone https://github.com/LNM31/Mini-Projects.git
cd Chatbot/chatbot-project-ts

# Install dependencies and start the dev server
npm install && npm run dev
```

The app will be available at `http://localhost:5173`.

### Other Scripts

```bash
npm run build     # Type-check with tsc and build for production
npm run preview   # Preview the production build locally
npm run lint      # Run ESLint across the project
```

## Features

- **Persistent Conversations** — Messages are saved to `localStorage` and survive page refreshes
- **Auto-Scroll** — Chat container automatically scrolls to the latest message via a custom `useAutoScroll` hook
- **Loading Spinner** — Animated spinner displays while awaiting bot responses, preventing duplicate sends
- **Timestamps** — Each message shows a 24-hour formatted time (`HH:mm`) powered by dayjs
- **Keyboard Shortcuts** — `Enter` to send, `Escape` to clear the input field
- **Clear Chat** — One-click button to wipe the entire conversation history
- **Custom Bot Responses** — Configurable response map via `Chatbot.addResponses()` with support for dynamic functions
- **Dynamic Page Title** — Browser tab shows the current message count in real time
- **Welcome Message** — Friendly prompt displayed when the conversation is empty

## Project Structure

```
chatbot-project-ts/
├── index.html                          # HTML entry point
├── package.json                        # Dependencies and scripts
├── vite.config.ts                      # Vite + React Compiler config
├── tsconfig.json                       # TypeScript configuration
├── eslint.config.js                    # ESLint rules
├── public/
│   └── vite.svg
└── src/
    ├── main.tsx                        # React root — mounts <App /> with StrictMode
    ├── App.tsx                         # Root component — state, localStorage sync, bot config
    ├── App.css                         # App layout (centered container, welcome message)
    ├── index.css                       # Global styles (font, margin reset)
    ├── vite-env.d.ts                   # Vite type declarations
    ├── assets/
    │   ├── robot.png                   # Bot profile image
    │   ├── user.png                    # User profile image
    │   └── loading-spinner.gif         # Loading animation
    ├── components/
    │   ├── ChatMessages.tsx            # Scrollable message list with auto-scroll
    │   ├── ChatMessages.css
    │   ├── ChatMessage.tsx             # Individual message bubble (user/bot layout)
    │   ├── ChatMessage.css
    │   ├── ChatInput.tsx               # Input field, send/clear buttons, keyboard handling
    │   └── ChatInput.css
    └── utility-functions/
        └── functions.jsx               # useAutoScroll custom hook
```

## Component Architecture

```
┌─────────────────────────────────────────────────────────┐
│  App                                                    │
│  State: chatMessages[]                                  │
│  localStorage sync · Bot response config                │
│                                                         │
│  ┌────────────────────┐    ┌──────────────────────────┐ │
│  │  ChatMessages      │    │  ChatInput               │ │
│  │  useAutoScroll()   │    │  State: inputText,       │ │
│  │                    │    │         isLoading        │ │
│  │  ┌──────────────┐  │    │  Enter → send            │ │
│  │  │ ChatMessage  │  │    │  Escape → clear          │ │
│  │  │ bubble +     │  │    │                          │ │
│  │  │ avatar +     │  │    │ [ input ] [Send] [Clear] │ │
│  │  │ timestamp    │  │    └─────────┬────────────────┘ │
│  │  └──────────────┘  │              │                  │
│  │  ┌──────────────┐  │              ▼                  │
│  │  │ ChatMessage  │  │    ┌──────────────────────┐     │
│  │  └──────────────┘  │    │  supersimpledev      │     │
│  │  ┌──────────────┐  │    │  Chatbot Library     │     │
│  │  │ ChatMessage  │  │    │  getResponseAsync()  │     │
│  │  └──────────────┘  │    └──────────────────────┘     │
│  └────────────────────┘                                 │
└─────────────────────────────────────────────────────────┘
```

## Data Flow

```
 User types message
       │
       ▼
 ┌───────────┐   setChatMessages()   ┌─────────┐   useEffect()   ┌──────────────┐
 │ ChatInput │ ───────────────────▶  │   App   │ ─────────────▶ │ localStorage │
 └───────────┘                       └─────────┘                 └──────────────┘
       │                                  │
       │  getResponseAsync()              │  props: chatMessages[]
       ▼                                  ▼
 ┌──────────────┐                   ┌──────────────┐
 │ supersimple  │                   │ ChatMessages │
 │ dev Chatbot  │                   │ + auto-scroll│
 └──────┬───────┘                   └──────┬───────┘
        │                                  │
        │  bot reply                       │  maps each message
        ▼                                  ▼
  setChatMessages()                 ┌──────────────┐
  with bot response                 │ ChatMessage  │
  ─────────────────▶ App ──▶ ...   │ bubble + time│
                                    └──────────────┘
```

## Message Object Shape

```typescript
{
  id: string;       // crypto.randomUUID()
  sender: string;   // 'user' | 'robot'
  message: string;  // Message text (or ReactNode during loading)
  time: number;     // Unix timestamp via dayjs().valueOf()
}
```


