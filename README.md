```markdown
---
title: D&D Real-Time Campaign Chat (dnd-chat)
status: active
tags: [web-application, real-time, Dungeons-and-Dragons, chat, websockets]
vision: "To provide a seamless, integrated, real-time communication platform optimized for online tabletop role-playing sessions."
---

# dnd-chat

## Description

`dnd-chat` is a dedicated real-time communication platform designed specifically for managing Dungeons & Dragons (TTRPG) campaigns. It delivers standard instant messaging features combined with robust, game-specific utilities, ensuring a streamlined virtual tabletop experience.

Key features include:
*   **Real-time Messaging:** Low-latency chat synchronization for all campaign participants.
*   **Native Dice Rolling:** Integrated syntax parsing for standard polyhedral dice rolls (e.g., `/roll 1d20 + 5`).
*   **Session Logs:** Persistent storage and searchability of campaign narrative and events.
*   **Character Integration:** Hooks for linking player characters and NPCs to messages.

## Setup/Installation

This guide assumes you have Node.js (LTS), npm, and Git installed on your system.

### Prerequisites

*   Node.js (v18+)
*   npm or Yarn
*   A running instance of the required database (see Tech Stack).

### Steps

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-repo/dnd-chat.git
   cd dnd-chat
   ```

2. **Install Dependencies:**
   This project uses a split architecture (client/server). Install dependencies for both components.

   ```bash
   # Install server dependencies
   cd server
   npm install

   # Install client dependencies
   cd ../client
   npm install
   ```

3. **Environment Configuration:**
   Create a `.env` file in the root of the `server` directory based on the provided template (`.env.example`). This file must contain database credentials, API keys, and port definitions.

   ```ini
   # Example .env content (server/):
   PORT=3001
   DATABASE_URL="postgres://user:pass@host:port/dnd_chat_db"
   JWT_SECRET="super_secret_key"
   ```

4. **Run Database Migrations (if applicable):**
   ```bash
   cd ../server
   npm run migrate
   ```

5. **Start Services:**
   Run the backend API/WebSocket server and the frontend client concurrently.

   ```bash
   # In the server directory (Terminal 1)
   npm start

   # In the client directory (Terminal 2)
   npm run dev
   ```

The application will typically be accessible via `http://localhost:3000` (Client) and the API available at `http://localhost:3001` (Server).

## Tech Stack

| Component | Technology | Purpose |
| :--- | :--- | :--- |
| **Frontend** | React, TypeScript, Tailwind CSS | UI rendering and modular component development. |
| **Backend** | Node.js, Express | RESTful API handling and business logic. |
| **Real-time** | Socket.IO (WebSockets) | Bidirectional communication for instant chat synchronization and dice rolls. |
| **Database** | PostgreSQL | Persistent storage for users, messages, and campaign metadata. |
| **ORM** | Sequelize / Prisma | Database abstraction and migration management. |
```