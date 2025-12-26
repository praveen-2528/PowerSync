# 📦 PowerSync Installation Guide

A centralized power management system for computer laboratories.

---

## 🖥️ Admin Setup (Server + Dashboard)

### Prerequisites
Install the following software before proceeding:

| Software | Download | Required For |
|----------|----------|--------------|
| **Python 3.10+** | [python.org/downloads](https://www.python.org/downloads/) | Server |
| **Node.js 18+** | [nodejs.org](https://nodejs.org/) | Dashboard |
| **Rust** | [rustup.rs](https://rustup.rs/) | Tauri Desktop App |

> [!IMPORTANT]
> During Python installation, check **"Add Python to PATH"**

### Installation Steps

1. **Extract** `Major-Project.zip` to a folder (e.g., `C:\PowerSync`)

2. **Run Setup** - Right-click `Setup_Admin.bat` → **Run as Administrator**

3. **Wait** for all dependencies to install (5-10 minutes on first run)

4. **Done!** When prompted, press **Y** to open the Dashboard

### What Gets Installed
- ✅ Python server dependencies
- ✅ Node.js dashboard dependencies  
- ✅ Server auto-starts on Windows login
- ✅ Desktop shortcuts: `PowerSync Server` & `PowerSync Dashboard`

### Starting Manually
- **Server**: Double-click `PowerSync Server` shortcut on Desktop
- **Dashboard**: Double-click `PowerSync Dashboard` shortcut on Desktop

---

## 💻 Agent Setup (Client PCs)

### Prerequisites
| Software | Download |
|----------|----------|
| **Python 3.10+** | [python.org/downloads](https://www.python.org/downloads/) |

### Installation Steps

1. **Extract** `Major-Project.zip` to a folder (e.g., `C:\PowerSync`)

2. **Run Setup** - Double-click `Setup_Agent.bat`

3. **Configure** in the GUI window that opens:
   - **Server Address**: Enter the Admin PC's IP address (e.g., `192.168.1.100`)
   - **Device Name**: Enter a name for this PC (e.g., `Lab-PC-01`)
   - **Heartbeat Interval**: How often to report status (default: 30 seconds)

4. **Save & Start** - Click the button to save settings and start the agent

### What Gets Installed
- ✅ Python agent dependencies
- ✅ Agent auto-starts on Windows login (runs hidden)
- ✅ Desktop shortcut: `PowerSync Settings`

### Modifying Settings Later
Double-click `PowerSync Settings` on Desktop to open the configuration GUI.

---

## 🌐 Network Configuration

### Firewall Rules (Admin PC)
The admin server runs on **port 8000**. Add a firewall rule to allow incoming connections:

```powershell
# Run as Administrator
netsh advfirewall firewall add rule name="PowerSync Server" dir=in action=allow protocol=tcp localport=8000
```

### Finding Admin IP Address
On the Admin PC, run this command to find the IP address:
```powershell
ipconfig | findstr IPv4
```
Use this IP address when configuring agents.

---

## 🔧 Troubleshooting

### Server Won't Start
- Check if Python is installed: `python --version`
- Check if port 8000 is available: `netstat -an | findstr 8000`
- View server logs in `server/` folder

### Agent Can't Connect
- Verify the server IP address is correct
- Check if server is running: Open `http://[ADMIN-IP]:8000/health` in browser
- Ensure firewall allows port 8000

### Dashboard Won't Open
- Check if Node.js is installed: `node --version`
- Check if Rust is installed: `cargo --version`
- Run `npm install` in the `dashboard/` folder manually

---

## 📊 Features

- **Real-time Monitoring** - View all connected PCs status
- **Auto Shutdown** - Automatically power off idle computers
- **Wake-on-LAN** - Remotely wake up computers
- **Energy Analytics** - Track power savings and CO₂ reduction
- **Scheduling** - Set working hours and after-hours rules

---

## 📁 Project Structure

```
Major-Project/
├── Setup_Admin.bat     ← Run this on Admin PC
├── Setup_Agent.bat     ← Run this on Client PCs
├── server/             ← FastAPI backend server
├── dashboard/          ← Tauri/React admin dashboard
└── agent/              ← Python monitoring agent
```

---

## 📞 Support

For issues or questions, contact your system administrator.
