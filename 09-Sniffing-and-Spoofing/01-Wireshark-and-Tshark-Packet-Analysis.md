# 🛠️ Tool Master Guide: Wireshark & TShark Packet Analysis Suite

> [!INFO] 📋 **Root Metadata**
> - **Category**: Network Protocol Analyzer & Deep Packet Inspection Suite (#1 Choice)
> - **Tools Covered**: Wireshark (GUI), TShark (CLI), Dumpcap
> - **Installations**: `sudo apt update && sudo apt install -y wireshark tshark`
> - **Binary Paths**: `/usr/bin/wireshark`, `/usr/bin/tshark`, `/usr/bin/dumpcap`
> - **Primary Objective**: Captures raw network frames, decodes over 3,000 network protocols, performs TCP stream follow reassembly, and extracts cleartext credentials or transmitted files.

---

## 📋 1. Essential Wireshark & TShark Display Filter Matrix

| Filtering Target | Display Filter Syntax | Technical Description |
| :--- | :--- | :--- |
| **HTTP GET/POST Requests**| `http.request.method == "POST"` | Filters all HTTP POST form submission packets |
| **Target IP Communication**| `ip.addr == 10.10.10.50` | Displays all incoming/outgoing packets for target IP |
| **TCP SYN Handshakes** | `tcp.flags.syn == 1 && tcp.flags.ack == 0` | Isolates initial TCP connection requests |
| **DNS Domain Queries** | `dns.qn.name contains "target"` | Filters DNS lookup queries containing specific domain |
| **Cleartext Credentials** | `http.authbinary || ftp.request.command == "PASS"` | Sniffs HTTP Basic Auth or FTP password transmissions |

---

## 💻 2. Practical Operational Workflows

### Scenario A: TShark CLI Headless Packet Capture with Filter
```bash
# Capture 100 HTTP POST packets on interface eth0 and print requested host and URIs
tshark -i eth0 -Y 'http.request.method == "POST"' -T fields -e ip.src -e http.host -e http.request.uri -c 100
```

### Scenario B: Extracting Transmitted Files from PCAP File
```bash
# Parse captured pcap file and export all HTTP objects into destination folder
tshark -r capture.pcap --export-objects "http,./extracted_files/"
```
