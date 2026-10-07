# 🛠️ Volatility 3 Memory Forensics Mastery

> [!INFO] 📌 **Tool Metadata**
> - **Category**: Advanced RAM Memory Forensics Framework (#1 Choice)
> - **License**: Open Source (Volatils License)
> - **Installation**: Pre-installed on Kali Linux (`volatility3` / `vol`)
> - **Primary Objective**: Analyzing physical RAM dumps to extract running processes, active network connections, injected DLL code, raw memory artifacts, and passwords.

---

## 📋 Essential Volatility 3 Plugin Reference Matrix

| Plugin Command | Target OS | Operational Function |
| :--- | :--- | :--- |
| `windows.pslist` | Windows | Lists running processes via doubly-linked ActiveProcessLinks list |
| `windows.pstree` | Windows | Displays process hierarchy tree showing parent-child process relationships |
| `windows.netscan` | Windows | Scans memory for active, closed, and listening network connections |
| `windows.malfind` | Windows | Detects hidden or injected code/DLLs in process memory (VAD regions with RWX permissions) |
| `windows.hashdump` | Windows | Extracts NTLM password hashes from memory-cached SAM & SYSTEM registry hives |
| `windows.dumpfiles`| Windows | Dumps executable binaries or files from memory onto disk |
| `linux.pslist` | Linux | Lists running Linux processes from task_struct |

---

## 💻 Practical Command Workflows

```bash
# 1. Inspect Process Tree from Windows RAM dump
vol -f memory.raw windows.pstree

# 2. Identify injected code and shellcode regions
vol -f memory.raw windows.malfind

# 3. Dump suspicious executable process (e.g. PID 4120) to working directory
vol -f memory.raw -o ./output windows.dumpfiles --pid 4120

# 4. Extract cached NTLM user password hashes
vol -f memory.raw windows.hashdump
```
