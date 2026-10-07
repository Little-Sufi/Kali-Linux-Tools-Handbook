# 🛠️ Tool Master Guide: Kismet Wireless Wardriving Engine

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: Kismet
> - **Category**: Wireless Network Detector & Wardriving Analyzer
> - **License**: Open Source (GPL-2.0)
> - **Installation Command**: `sudo apt update && sudo apt install -y kismet`
> - **Binary Path**: `/usr/bin/kismet`
> - **Web Dashboard URL**: `http://localhost:2501`
> - **Primary Objective**: Passively logs 802.11 Wi-Fi, Bluetooth, and Zigbee signals, creating PCAPNG packet logs and mapping GPS location coordinates for wardriving surveys.

---

## 💻 1. Operational Workflow

```bash
# Start Kismet service listening on wireless interface
sudo kismet -c wlan0
# Access web dashboard at http://localhost:2501 to inspect live signal strength and packet logs
```
