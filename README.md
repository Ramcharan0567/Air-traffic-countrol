# ✈️ ATC Command — Real-Time Air Traffic Control System

> A full-stack real-time Air Traffic Control (ATC) simulation system built as part of a **Software Development Engineering (SDE) Internship Project**.

---

## 📌 Project Overview

**ATC Command** is a real-time, browser-based Air Traffic Control simulation platform that enables controllers to manage live aircraft, monitor radar, issue flight commands, and export operational reports. The system features role-based access (Admin / Passenger), a live radar view, conflict detection, and multi-runway management — all powered by WebSocket communication.

---

## 🎯 Key Features

- 🛫 **Live Radar View** — Real-time aircraft tracking on an animated radar canvas
- 🛬 **Runway Management** — Multi-runway status monitoring and assignment
- ✈️ **Flight List Panel** — Live aircraft list with state, altitude, speed & heading
- 🧠 **Conflict Detection** — Automated proximity conflict detection between aircraft
- 📋 **Command & Control** — Issue real-time ATC commands to active flights
- 📊 **Log Panel** — Live event log of all controller actions and system events
- 👥 **Role-Based Access** — Admin (full control) and Passenger (read-only) views
- 📁 **Export Reports** — Download flight data as **CSV** or **PDF**
- 🔐 **Auth System** — Token-based login with session management
- 🗄️ **Persistent Database** — SQLite-backed flight data storage

---

## 🏗️ System Architecture

```
ATC Command
├── client/                  # React + Vite Frontend
│   └── src/
│       ├── components/
│       │   ├── RadarView.jsx          # Live radar canvas
│       │   ├── FlightList.jsx         # Aircraft data table
│       │   ├── RunwayStatus.jsx       # Runway occupancy panel
│       │   ├── LogPanel.jsx           # Event log stream
│       │   ├── LoginForm.jsx          # Auth screen
│       │   └── PassengerDashboard.jsx # Read-only public view
│       ├── services/                  # Socket.io client services
│       ├── App.jsx                    # Root component & routing
│       └── main.jsx
│
└── server/                  # Node.js + Express Backend
    ├── game/
    │   ├── GameServer.js      # Core simulation engine
    │   ├── Aircraft.js        # Aircraft state & physics model
    │   ├── ConflictDetector.js# Proximity conflict detection
    │   └── Runway.js          # Runway state management
    ├── db.js                  # SQLite database layer
    └── index.js               # Express server + Socket.io hub
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React 19, Vite, Tailwind CSS |
| **UI Icons** | Lucide React |
| **Real-Time** | Socket.io (WebSockets) |
| **Backend** | Node.js, Express 5 |
| **Database** | SQLite3 |
| **PDF Export** | PDFKit |
| **Auth** | UUID token-based sessions |
| **Dev Tools** | Concurrently, ESLint |

---

## 🚀 Getting Started

### Prerequisites

- Node.js `v18+`
- npm `v9+`

### Installation

```bash
# Clone the repository
git clone https://github.com/Ramcharan0567/Air-traffic-countrol.git
cd Air-traffic-countrol

# Install root dependencies
npm install

# Install client dependencies
cd client && npm install && cd ..

# Install server dependencies
cd server && npm install && cd ..
```

### Run (Development)

```bash
# Starts both client and server concurrently
npm run dev
```

| Service | URL |
|---|---|
| Client (React) | http://localhost:5173 |
| Server (API) | http://localhost:3001 |

### Access Credentials

| Role | Access |
|---|---|
| **Admin** | Enter the access code on the login screen |
| **Passenger** | Click "View as Passenger" for read-only mode |

---

## 📡 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/login` | Authenticate and receive a session token |
| `GET` | `/export` | Download all flight data as CSV |
| `GET` | `/export/pdf` | Download all flight data as PDF |

### WebSocket Events

| Event | Direction | Description |
|---|---|---|
| `gameState` | Server → Client | Full initial game state |
| `update` | Server → Client | Real-time aircraft position updates |
| `command` | Client → Server | ATC command for a specific aircraft |

---

## 📂 Project Structure Highlights

```
├── package.json          # Root scripts (dev, dev:client, dev:server)
├── .gitignore            # Excludes node_modules, logs, build artifacts
├── client/               # Vite + React SPA
└── server/               # Express + Socket.io backend
    └── atc_data.db       # SQLite persistent storage
```

---

## 🧪 Core Modules

### `GameServer.js`
The central simulation loop. Manages aircraft spawning, state transitions, game tick updates, and broadcasting real-time state to all connected clients.

### `Aircraft.js`
Represents individual aircraft with physics-based position updates, altitude/speed/heading model, and state machine (approaching → landing → landed / departing → airborne).

### `ConflictDetector.js`
Monitors all active aircraft pairs and raises alerts when aircraft enter a minimum safe separation distance.

### `Runway.js`
Tracks runway occupancy states and handles assignment/release logic for landing and departing aircraft.

---

## 📊 Export & Reporting

The system supports exporting a complete flight record including:
- Start time, callsign, aircraft type
- Final phase (state), altitude, speed
- Assigned runway, action timestamps

Formats: **CSV** and **PDF** (landscape layout with PDFKit)

---

## 👨‍💻 Author

**Maddala Sri Ramcharan**
SDE Intern Project — 2026
GitHub: [@Ramcharan0567](https://github.com/Ramcharan0567)

---

## 📄 License

This project is for educational and internship demonstration purposes.
