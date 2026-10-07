# 📡 Category 09: Sniffing & Spoofing — Master Overview

> [!INFO] 📌 **Domain Definition & Scope**
> Sniffing & Spoofing encompasses passive network traffic capture, protocol decoding, ARP cache poisoning, Man-in-the-Middle (MiTM) packet inspection, DNS spoofing, and MAC address manipulation to analyze network security controls and audit credential transmission over unencrypted protocols.

---

## 🏆 Tool Selection & Efficiency Matrix

| Assessment Task | Primary Tool (#1 Choice) | Secondary / Advanced Tool | Operational Layer |
| :--- | :--- | :--- | :--- |
| **GUI Graphical Packet Analysis** | **Wireshark** | NetworkMiner | Layer 2 - Layer 7 |
| **CLI High-Speed Headless Packet Sniffing** | **TShark / Tcpdump** | Dumpcap | Layer 2 - Layer 4 |
| **Active Network MiTM & ARP Poisoning** | **Bettercap** | Ettercap, MITMproxy | Layer 2 / Layer 3 / Layer 7 |
| **Network Interface MAC Spoofing** | **Macchanger** | Iproute2 (`ip link`) | Layer 2 (Data Link) |

---

## 📂 Comprehensive Tool Master Guides in Category 09

1. 🛠️ [01-Wireshark-and-TShark-Packet-Analysis.md](./01-Wireshark-and-TShark-Packet-Analysis.md)
   - Wireshark GUI & TShark CLI engines, capture filters vs display filters, protocol dissectors, stream reassembly (`tcp.stream`), and PCAP export workflows.
2. 🛠️ [02-Bettercap-and-Ettercap-MiTM-Frameworks.md](./02-Bettercap-and-Ettercap-MiTM-Frameworks.md)
   - Bettercap caplets, ARP poisoning engine (`net.recon`, `arp.spoof`), DNS spoofing (`dns.spoof`), HTTP/HTTPS credential sniffing, and Ettercap GUI/CLI comparison.
3. 🛠️ [03-tcpdump-Commandline-Packet-Capture.md](./03-tcpdump-Commandline-Packet-Capture.md)
   - Tcpdump BPF (Berkeley Packet Filter) syntax (`src host`, `dst port`, `tcp[tcpflags] & tcp-syn != 0`), packet hex dumping (`-X`), and PCAP file logging (`-w`).
4. 🛠️ [04-Macchanger-and-MAC-Address-Spoofing.md](./04-Macchanger-and-MAC-Address-Spoofing.md)
   - Macchanger MAC randomizer, vendor OUI impersonation, interface down/up scripts, and network anonymity protocols.
