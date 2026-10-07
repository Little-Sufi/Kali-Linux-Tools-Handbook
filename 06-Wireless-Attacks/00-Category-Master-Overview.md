# 📶 Category 06: Wireless Network Security — Master Overview

> [!INFO] 📌 **Domain Definition & Scope**
> Wireless Security Auditing focuses on evaluating 802.11 Wi-Fi networks (WEP, WPA/WPA2-PSK, WPA3, WPA-Enterprise), rogue access points, client deauthentication injection attacks, WPS PIN vulnerabilities, and wardriving signal analysis.

---

## 🏆 Tool Selection & Efficiency Matrix

| Assessment Task | Primary Tool (#1 Choice) | Secondary / Advanced Alternatives | Hardware Requirement |
| :--- | :--- | :--- | :--- |
| **802.11 Packet Injection & Handshake Capture**| **Aircrack-ng Suite** | Wifite2, Kismet | Wireless Adapter (Monitor Mode / Packet Injection) |
| **Automated Wireless Attack Orchestration** | **Wifite2** | Aircrack-ng | Wireless Adapter (Monitor Mode) |
| **Wireless Wardriving & Signal Analysis** | **Kismet** | Airodump-ng | Wireless Adapter + GPS Receiver |
| **WPS PIN Exploitation & Pixie-Dust** | **Reaver / Pixiewps** | Bully | Wireless Adapter (Monitor Mode) |

---

## 📂 Comprehensive Tool Master Guides in Category 06

1. 🛠️ [01-Aircrack-ng-Exhaustive-Suite-Guide.md](./01-Aircrack-ng-Exhaustive-Suite-Guide.md)
   - `airmon-ng` interface monitoring, `airodump-ng` channel/BSSID targeting, `aireplay-ng` deauth frame injection, and `aircrack-ng` handshake dictionary cracking.
2. 🛠️ [02-Wifite2-Automated-Wireless-Auditing.md](./02-Wifite2-Automated-Wireless-Auditing.md)
   - Wifite2 automated attack script, PMKID key capture (`hcxdumptool`), and automated WPS Pixie-Dust attacks.
3. 🛠️ [03-Kismet-and-Wardriving-Suite.md](./03-Kismet-and-Wardriving-Suite.md)
   - Kismet wireless packet sniffer, web dashboard interface (`http://localhost:2501`), PCAPNG logging, and GPS mapping.
4. 🛠️ [04-Reaver-and-WPS-Attacks-Guide.md](./04-Reaver-and-WPS-Attacks-Guide.md)
   - Reaver WPS PIN brute-forcing, `wash` WPS access point scanner, and `pixiewps` offline PIN calculation.
