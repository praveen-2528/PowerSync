# Smart Power Management System

A centralized power management solution for computer laboratories featuring:
- **Tauri Desktop App** - Native admin dashboard
- **Python Agent** - Activity monitoring on lab computers  
- **FastAPI Server** - Central API for coordination

## Quick Start

### 1. Start the Server
```bash
cd server
pip install -r requirements.txt
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```
API docs: http://localhost:8000/docs

### 2. Start the Agent (on lab computers)
```bash
cd agent
pip install -r requirements.txt
python setup_gui.py  # Configure settings
python agent.py      # Start monitoring
```

### 3. Run the Dashboard
```bash
cd dashboard
npm install
npm run dev          # Web mode
npm run tauri:dev    # Desktop mode (requires Rust)
```

## 🚀 Auto-Startup Installation

Run the installer to set up automatic startup and desktop shortcuts:

```bash
python install.py
```

This will:
- ✅ Create Task Scheduler entries for Agent and Server
- ✅ Create desktop shortcuts for Settings, Server, and Dashboard
- ✅ Agent runs silently in background at user login
- ✅ Server starts automatically at login

## Architecture

```
┌─────────────────┐     ┌─────────────────┐
│  Tauri Desktop  │────▶│   FastAPI       │
│    Dashboard    │◀────│   Server        │
└─────────────────┘     └────────┬────────┘
                                 │
              ┌──────────────────┼──────────────────┐
              ▼                  ▼                  ▼
        ┌──────────┐       ┌──────────┐       ┌──────────┐
        │  Agent   │       │  Agent   │       │  Agent   │
        │   PC-1   │       │   PC-2   │       │   PC-n   │
        └──────────┘       └──────────┘       └──────────┘
```

## Features

- ✅ Real-time device monitoring
- ✅ Auto-shutdown of idle computers
- ✅ Wake-on-LAN support
- ✅ Energy savings analytics
- ✅ CO₂ reduction tracking
- ✅ Configurable idle thresholds
- ✅ Working hours / after-hours rules
- ✅ Accurate CPU/OS detection (Intel Core i7, Windows 11 Pro, etc.)
- ✅ Auto-startup via Task Scheduler
- ✅ Agent waits for server connection

## Tech Stack

| Component | Technology |
|-----------|------------|
| Dashboard | Tauri 2.0, React, Vite, Recharts |
| Server | Python, FastAPI, SQLAlchemy |
| Agent | Python, pynput, psutil |
| Database | SQLite |
