# PowerSync - Smart Power Management System

A centralized power management solution for computer laboratories.

## Features
- 📊 Real-time device monitoring
- ⏰ Auto-shutdown of idle computers
- 🌐 Wake-on-LAN support
- � Energy savings analytics
- 🌱 CO₂ reduction tracking
- ⚙️ Configurable idle thresholds

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

## Quick Start

### Admin PC (Server + Dashboard)

**Prerequisites:** Python 3.10+, Node.js 18+ (Rust auto-installed)

```batch
Setup_Admin.bat
```

### Client PCs (Agent)

**Prerequisites:** Python 3.10+

```batch
Setup_Agent.bat
```

See `INSTALL_GUIDE.md` for detailed instructions.

## Tech Stack

| Component | Technology |
|-----------|------------|
| Dashboard | Tauri 2.0, React, Vite, Recharts |
| Server | Python, FastAPI, SQLAlchemy |
| Agent | Python, PyQt6, psutil |
| Database | SQLite |

## Manual Start

### Server
```bash
cd server
pip install -r requirements.txt
uvicorn main:app --host 0.0.0.0 --port 8000
```

### Dashboard
```bash
cd dashboard
npm install
npm run tauri dev
```

### Agent
```bash
cd agent
pip install -r requirements.txt
python setup_gui.py
python agent.py
```

## API Documentation
http://localhost:8000/docs
