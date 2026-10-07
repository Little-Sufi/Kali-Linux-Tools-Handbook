# 🛠️ Tool Master Guide: Netcat, Socat & Network Utility Swiss-Army-Knife

> [!INFO] 📋 **Root Metadata**
> - **Category**: Multi-Purpose Network Connection & Socket Relay Utilities (#1 Choice)
> - **Tools Covered**: Netcat (`nc`), Ncat, Socat
> - **Installations**: Pre-installed on Kali Linux (`netcat-traditional`, `ncat`, `socat`)
> - **Binary Paths**: `/usr/bin/nc`, `/usr/bin/ncat`, `/usr/bin/socat`
> - **Primary Objective**: Handles arbitrary TCP/UDP socket reads/writes, port listening, banner grabbing, raw file transfers, and fully interactive TTY reverse shell relays.

---

## 📋 1. Core Netcat & Socat Command Reference Matrix

| Tool | Technical Command Syntax | Operational Function |
| :--- | :--- | :--- |
| **Netcat** | `nc -lvnp 4444` | Starts TCP listener on port 4444 with verbose output and no DNS resolution |
| **Netcat** | `nc -vn 10.10.10.50 80` | Connects to remote IP and port to grab service banner |
| **Socat** | `socat file:`tty`,raw,echo=0 tcp-listen:4444` | Listens for reverse connection and upgrades to fully interactive TTY shell |

---

## 💻 2. Practical Operational Workflows

### Scenario A: Netcat Reverse Shell Listener & Port Scanning
```bash
# Start Netcat listener on port 4444
nc -lvnp 4444
```

### Scenario B: Upgrading Dumb Shell to Fully Interactive TTY via Python & Stty
```bash
# 1. Inside spawned reverse shell, launch Python PTY spawn
python3 -c 'import pty; pty.spawn("/bin/bash")'

# 2. Background shell using Ctrl + Z
# 3. In local Kali terminal, set terminal to raw mode and resume shell
stty raw -echo; fg

# 4. In shell: Set terminal environment variables
export TERM=xterm-256color
reset
```
