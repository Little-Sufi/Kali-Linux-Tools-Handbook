# 🛠️ Tool Master Guide: Wifite2 (Automated Wireless Auditor)

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: Wifite2
> - **Category**: Automated Wireless Attack Framework (#1 Choice for Automation)
> - **License**: Open Source (GPL-2.0)
> - **Installation Command**: `sudo apt update && sudo apt install -y wifite`
> - **Binary Path**: `/usr/sbin/wifite`
> - **Primary Objective**: Completely automates 802.11 wireless network auditing by automatically handling monitor mode activation, PMKID captures (`hcxdumptool`), WPA2 4-way handshake captures, and WPS Pixie-Dust attacks.

---

## 📋 1. Exhaustive Flag Reference Matrix

| Flag Category | Flag / Option | Description & Technical Function | Syntax Example |
| :--- | :--- | :--- | :--- |
| **Interface** | `-i <iface>` | Specifies wireless interface to use | `wifite -i wlan0` |
| **Attacks** | `--wpa` | Targets WPA/WPA2 access points exclusively | `wifite --wpa` |
| | `--wps` | Targets WPS-enabled access points exclusively | `wifite --wps` |
| | `--pmkid` | Performs clientless PMKID capture attack | `wifite --pmkid` |
| **Cracking** | `-dict <file>` | Specifies dictionary file for handshake cracking | `wifite -dict rockyou.txt` |
| **Automation** | `--daemon` | Runs continuously in daemon mode without user prompts | `wifite --daemon` |

---

## 💻 2. Operational Command Workflow

```bash
# Launch automated wireless attack scanner targeting all WPA2/WPS access points
sudo wifite --wpa --daemon -dict /usr/share/wordlists/rockyou.txt
```
