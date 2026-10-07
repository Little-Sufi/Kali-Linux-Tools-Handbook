# 🛠️ Tool Master Guide: tcpdump Command-Line Packet Capture

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: tcpdump
> - **Category**: CLI Packet Analyzer & Network Sniffer Standard
> - **License**: Open Source (BSD-3-Clause)
> - **Installation Command**: `sudo apt update && sudo apt install -y tcpdump`
> - **Binary Path**: `/usr/sbin/tcpdump`
> - **Primary Objective**: Provides lightweight, low-overhead command-line network packet capture and Berkeley Packet Filter (BPF) evaluation.

---

## 💻 1. Operational Command Workflows

```bash
# 1. Capture Port 80 HTTP Traffic on eth0 and Save to PCAP file
sudo tcpdump -i eth0 port 80 -w http_capture.pcap

# 2. Read PCAP file with Hex and ASCII output (-X)
tcpdump -r http_capture.pcap -X -n
```
