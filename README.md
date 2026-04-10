# T-Rex Runner Game

A browser-based T-Rex Runner game with a Node.js high-score API, compatible with Playwright for automated testing.

## Tech Stack

| Layer   | Technology                     |
|---------|--------------------------------|
| UI      | HTML, CSS, Vanilla JavaScript  |
| API     | Node.js + Express              |
| Testing | Playwright                     |

## Prerequisites

- Node.js >= 18
- npm

## Project Structure

```
trex-runner/
├── api/
│   ├── server.js       # Express API server
│   └── package.json
└── ui/
    ├── index.html      # Game UI
    └── game.js
```

## Setup & Run

### 1. Start the API Server

```bash
cd trex-runner\api
npm install
node server.js
```

The API runs at **http://localhost:3000**.

#### API Endpoints

| Method | Endpoint         | Description                        |
|--------|------------------|------------------------------------|
| GET    | `/score`         | Returns the current high score     |
| POST   | `/score/:value`  | Submits a score; updates if higher |

#### Port Already in Use?

If port 3000 is already occupied, kill the process first (PowerShell):

```powershell
Stop-Process -Id (Get-NetTCPConnection -LocalPort 3000 | Select-Object -ExpandProperty OwningProcess) -Force
```

Then start the server again:

```bash
cd trex-runner\api
node server.js
```

### 2. Run the UI

The UI must be served over HTTP (not opened as a file) so it can communicate with the API.

Navigate to the `ui` folder and start a local HTTP server:

```bash
cd trex-runner\ui
npx http-server
```

Then open your browser at:

- **http://127.0.0.1:8080** (local)
- **http://\<your-ip\>:8080** (network, shown in terminal output)

> **Note:** `npx http-server` will prompt to install `http-server` on first run — press `y` to confirm.

#### Port Already in Use?

If port 8080 is already occupied, specify a different port:

```bash
npx http-server -p 8081
```

Then open **http://127.0.0.1:8081** instead.

### 3. Playwright (Optional)

Point Playwright to **http://127.0.0.1:8080** (with the `http-server` running as above).
