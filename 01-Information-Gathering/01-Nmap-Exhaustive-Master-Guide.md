# 🛠️ Tool Master Guide: Nmap (Network Mapper)

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: Nmap (Network Mapper)
> - **Category**: Network Discovery & Port Scanning (#1 Choice)
> - **License**: Nmap Public Source License (NPSL / GPL compatible)
> - **Installation Command**: `sudo apt update && sudo apt install -y nmap`
> - **Binary Path**: `/usr/bin/nmap`
> - **NSE Scripts Directory**: `/usr/share/nmap/scripts/`
> - **Nmap Service DB**: `/usr/share/nmap/nmap-services`
> - **Primary Objective**: Host discovery, port state determination (Open, Closed, Filtered), service version banner extraction, OS stack fingerprinting, and Nmap Scripting Engine (NSE) vulnerability auditing.

---

## ⚡ 1. Technical Mechanics & Packet Dynamics

Nmap operates by sending raw IP packets to remote target ports and evaluating the returning response packets:
- **Open**: Target returns `SYN-ACK` (TCP) or valid service response (UDP).
- **Closed**: Target returns `RST-ACK` (TCP) or ICMP Type 3 Code 3 "Port Unreachable" (UDP).
- **Filtered**: No response received, or ICMP Type 3 Code 1/2/9/10/13 returned (Firewall dropped packet).
- **Unfiltered**: Target returns `RST` (ACK scan mode), indicating port is accessible but state is unknown.

---

## 📋 2. Exhaustive Flag & Argument Reference Matrix

| Flag Group | Flag Name | Full Description & Packet Impact | Technical Syntax Example |
| :--- | :--- | :--- | :--- |
| **Scan Types** | `-sS` | **TCP SYN Stealth Scan**: Sends TCP SYN packet. If SYN-ACK returned, sends RST immediately to tear down connection without completing 3-way handshake. Requires root privileges. | `sudo nmap -sS <target>` |
| | `-sT` | **TCP Connect Scan**: Uses OS system `connect()` call to complete full 3-way handshake (SYN -> SYN-ACK -> ACK). Used when running without root. Logged by application firewalls. | `nmap -sT <target>` |
| | `-sU` | **UDP Scan**: Sends raw UDP packets. Slow due to OS ICMP rate limiting on closed ports. | `sudo nmap -sU -p 53,67,161,500 <target>` |
| | `-sA` | **TCP ACK Scan**: Sends ACK packets to map firewall rulesets and determine stateful filtering. | `sudo nmap -sA -p 80,445 <target>` |
| | `-sN / -sF / -sX`| **Null / FIN / Xmas Scans**: Sets no flags (`-sN`), FIN flag (`-sF`), or FIN+PSH+URG flags (`-sX`). Exploits RFC 793 behavior to bypass non-stateful firewalls on Unix target systems. | `sudo nmap -sX <target>` |
| **Discovery** | `-sn` | **Ping Sweep**: Disables port scanning. Performs host discovery only (ARP on local subnet, ICMP+TCP on remote). | `nmap -sn 192.168.1.0/24` |
| | `-Pn` | **Disable Host Discovery**: Treats all hosts as online. Bypasses ICMP blocks by firewalls. | `nmap -Pn <target>` |
| | `-PR` | **ARP Ping**: Uses raw ARP requests for ultra-fast local subnet discovery. Default on local Ethernet/Wi-Fi. | `sudo nmap -sn -PR 192.168.1.0/24` |
| **Service & OS**| `-sV` | **Service Version Detection**: Interrogates open ports with probe strings from `nmap-service-probes`. | `nmap -sV --version-intensity 5 <target>` |
| | `-O` | **OS Fingerprinting**: Analyses TCP window sizes, initial sequence numbers, and option ordering to match against `nmap-os-db`. | `sudo nmap -O <target>` |
| | `-A` | **Aggressive Mode**: Enables `-sV`, `-O`, `-sC`, and `--traceroute` simultaneously. | `nmap -A <target>` |
| **Port Specs** | `-p <ports>` | Specifies target ports: `-p 80,443`, `-p 1-65535`, `-p-` (all 65535 ports), `U:53,111,T:80,445`. | `nmap -p- <target>` |
| | `--top-ports <N>`| Scans the top `N` most common ports based on `nmap-services` frequency data. | `nmap --top-ports 1000 <target>` |
| **Timing & Rate**| `-T<0-5>` | Timing template: `T0` (Paranoid), `T1` (Sneaky), `T2` (Polite), `T3` (Normal), `T4` (Aggressive), `T5` (Insane). | `nmap -T4 <target>` |
| | `--min-rate <N>`| Forces Nmap to send at least `N` packets per second (essential for fast 65k scans). | `nmap --min-rate 5000 -p- <target>` |
| **Output** | `-oA <prefix>`| Saves scan results simultaneously in Normal (`.nmap`), XML (`.xml`), and Grepable (`.gnmap`) formats. | `nmap -oA target_audit <target>` |

---

## 💻 3. Operational Workflows & Commands

### Scenario A: Fast Subnet Host Discovery (Ping Sweep)
```bash
# Sweeps a /24 network for live hosts using ARP (local) or ICMP/TCP (remote) and outputs to grepable file
sudo nmap -sn -PR 192.168.1.0/24 -oG ping_sweep.gnmap
```

### Scenario B: Full 65,535 Port Speed Audit & Service Fingerprinting
```bash
# Step 1: Rapidly discover open ports across all 65,535 TCP ports
sudo nmap -sS -p- --min-rate 5000 -Pn 10.10.10.50 -oG all_ports.gnmap

# Step 2: Extract discovered open ports from gnmap file
PORTS=$(grep -oP '\d+/open' all_ports.gnmap | awk -F'/' '{print $1}' | paste -sd,)

# Step 3: Run comprehensive service versioning, OS detection, and default NSE scripts on open ports
sudo nmap -sS -sV -sC -O -p $PORTS -T4 -oA target_deep_audit 10.10.10.50
```

### Scenario C: Targeted Vulnerability Script Audit (NSE)
```bash
# Run specific SMB vulnerability scripts against target host
nmap --script smb-vuln-ms17-010,smb-vuln-ms08-067 -p 445 10.10.10.50 -oA smb_vulns
```
