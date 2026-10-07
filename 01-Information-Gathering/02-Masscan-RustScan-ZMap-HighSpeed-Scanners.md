# 🛠️ Tool Master Guide: Masscan, RustScan & ZMap (High-Speed Scanners)

> [!INFO] 📋 **Root Metadata**
> - **Category**: Asynchronous High-Speed Network Discovery
> - **Tools Covered**: Masscan, RustScan, ZMap
> - **Installations**:
>   - Masscan: `sudo apt install masscan` | Path: `/usr/bin/masscan`
>   - RustScan: Download deb/cargo (`cargo install rustscan`) | Path: `/usr/local/bin/rustscan`
>   - ZMap: `sudo apt install zmap` | Path: `/usr/bin/zmap`
> - **Primary Objective**: Rapidly scan massive IP networks or full 65,535 port ranges within seconds to minutes by bypassing standard OS TCP socket bottlenecks.

---

## ⚡ 1. Masscan Deep Guide

Masscan transmits asynchronous TCP SYN packets using a custom lightweight network stack.

### Key Command Flags Matrix
| Flag | Function | Syntax Example |
| :--- | :--- | :--- |
| `-p <ports>` | Target port specification | `masscan -p1-65535 10.10.10.0/24` |
| `--rate <pps>` | Transmit rate in packets per second | `masscan --rate 10000 -p80,443 172.16.0.0/16` |
| `--banners` | Grabs basic service banner HTTP/SSH headers | `masscan -p80 --banners 10.10.10.50` |
| `-oG <file>` | Grepable output format | `masscan -p80 10.10.10.0/24 -oG output.gnmap` |

### Command Workflow
```bash
# High-speed discovery across entire class B network for web & management ports
sudo masscan -p80,443,8080,8443,22,3389 172.16.0.0/16 --rate 5000 -oG masscan_subnets.txt
```

---

## ⚡ 2. RustScan Deep Guide

RustScan uses async threads to scan all 65,535 ports on a single host in under 3 seconds, automatically piping discovered ports directly into an Nmap execution engine.

### Command Workflow
```bash
# Auto-discover open ports on target host and execute deep Nmap scan on discovered ports
rustscan -a 10.10.10.50 --ulimit 5000 -- -sV -sC -oA rustscan_results
```

---

## ⚡ 3. ZMap Deep Guide

ZMap is a single-packet network scanner designed for Internet-wide surveys. A single 1Gbps connection can scan the entire IPv4 space in under 45 minutes.

### Command Workflow
```bash
# Scan entire IPv4 network for open port 443 (HTTPS) at 100k pps
sudo zmap -p 443 0.0.0.0/0 -r 100000 -o zmap_port443.txt
```
