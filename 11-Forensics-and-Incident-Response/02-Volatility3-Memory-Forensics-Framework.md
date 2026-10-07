# 🛠️ Tool Master Guide: Volatility 3 Memory Forensics Framework

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: Volatility 3
> - **Category**: Volatile RAM Memory Forensics Framework (#1 Memory Choice)
> - **License**: Open Source (Volatility Software License 1.0)
> - **Installation Command**: `sudo apt update && sudo apt install -y volatility3`
> - **Binary Path**: `/usr/bin/vol` or `vol3`
> - **Primary Objective**: Analyzes RAM memory dumps (.raw, .vmem, .dmp) without needing profile definitions, uncovering running processes, network connections, injected code DLLs, and rootkits.

---

## 📋 1. Core Volatility 3 Windows Plugin Matrix

| Volatility 3 Plugin | Operational Function |
| :--- | :--- |
| `windows.pslist` | Lists all active processes in memory dump |
| `windows.pstree` | Displays parent-child process hierarchy tree |
| `windows.cmdline` | Extracts exact command-line parameters passed to processes |
| `windows.netscan` | Scans memory for active and closed network connections and listening sockets |
| `windows.malfind` | Scans process memory pages for executable permissions (PAGE_EXECUTE_READWRITE) and shellcode injection |
| `windows.dumpfiles` | Dumps executable or file objects directly from memory dump onto disk |

---

## 💻 2. Practical Operational Workflow

```bash
# 1. Inspect Process Tree of Memory Dump
vol -f memory.raw windows.pstree

# 2. Scan for Malicious Code Injections and Suspicious Memory Pages
vol -f memory.raw windows.malfind

# 3. Extract Command Line Execution Arguments
vol -f memory.raw windows.cmdline
```
