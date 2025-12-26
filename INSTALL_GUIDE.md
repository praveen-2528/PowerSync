# 📦 PowerSync Installation Guide

---

## 🖥️ ADMIN SETUP (Server + Dashboard)

### Prerequisites
Install these before running setup:

| Software | Download Link |
|----------|---------------|
| Python 3.10+ | https://www.python.org/downloads/ |
| Node.js 18+ | https://nodejs.org/ |
| Rust | https://rustup.rs/ |

> **Important:** Check "Add Python to PATH" during Python installation

### Steps
1. Extract the zip file to a folder
2. Right-click **`Setup_Admin.bat`** → Run as Administrator
3. Wait for installation to complete
4. Press **Y** when asked to open Dashboard

### What the Setup Does
- ✅ Installs Python server dependencies
- ✅ Installs Node.js dashboard dependencies (npm install)
- ✅ Creates hidden launchers for server and dashboard
- ✅ Adds server to Windows Startup (auto-start on login)
- ✅ Creates desktop shortcuts:
  - `PowerSync Server` - Starts server in background
  - `PowerSync Dashboard` - Opens admin dashboard
- ✅ Starts server immediately

---

## 💻 AGENT SETUP (Client PCs)

### Prerequisites
| Software | Download Link |
|----------|---------------|
| Python 3.10+ | https://www.python.org/downloads/ |

### Steps
1. Extract the zip file to a folder
2. Double-click **`Setup_Agent.bat`**
3. Configure in the GUI:
   - Enter Admin PC's IP address
   - Set device name
   - Adjust heartbeat interval if needed
4. Click Save to start the agent

### What the Setup Does
- ✅ Installs Python agent dependencies + PyQt6
- ✅ Creates hidden launcher for agent
- ✅ Adds agent to Windows Startup (auto-start on login)
- ✅ Creates desktop shortcut:
  - `PowerSync Settings` - Opens configuration GUI
- ✅ Opens configuration GUI for initial setup
- ✅ Starts agent in background after configuration

---

## 🌐 Network Setup

### Admin PC - Allow Port 8000
Run in PowerShell as Administrator:
```powershell
netsh advfirewall firewall add rule name="PowerSync" dir=in action=allow protocol=tcp localport=8000
```

### Find Admin IP Address
Run on Admin PC:
```powershell
ipconfig | findstr IPv4
```

---

## 🔧 Troubleshooting

| Problem | Solution |
|---------|----------|
| "Python not found" | Install Python, check "Add to PATH" |
| "Node.js not found" | Install Node.js from nodejs.org |
| "Rust not found" | Install Rust from rustup.rs |
| Agent can't connect | Check server IP, verify port 8000 is open |
| Dashboard won't open | Wait for Tauri to compile (first run takes time) |

---

## 📁 Files Overview

```
├── Setup_Admin.bat    ← Run on Admin PC
├── Setup_Agent.bat    ← Run on Client PCs
├── server/            ← API server (Python)
├── dashboard/         ← Admin UI (Tauri/React)
└── agent/             ← Client monitor (Python)
```
