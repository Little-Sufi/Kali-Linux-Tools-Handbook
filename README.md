# 🗡️ Kali Linux Tools Handbook — The Penetration Tester's Playbook

[![Platform](https://img.shields.io/badge/OS-Kali%20Linux-blue?logo=kalilinux)](https://www.kali.org)
[![Obsidian Ready](https://img.shields.io/badge/Obsidian-Ready%20Vault-purple?logo=obsidian)](https://obsidian.md)
[![Categories](https://img.shields.io/badge/Domains-12%20Categories-red)]()
[![Tools](https://img.shields.io/badge/Tools-80%2B%20Documented-green)]()
[![License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)

Created & Maintained by **[Amar Sufiyan KC (@Little-Sufi)](https://github.com/Little-Sufi)**

---

## 📖 Handbook Overview

The **Kali Linux Tools Handbook** is an exhaustive, production-grade technical reference vault and operational playbook for penetration testers, security researchers, and SOC analysts.

Unlike generic cheat sheets, every single tool guide in this vault provides:
- Exact Kali Linux package names and root binary execution paths.
- Complete parameter and flag reference matrices with practical explanations.
- Real-world offensive scenarios with copy-paste terminal commands.
- Operational security (OpSec) considerations, output parsing (grep/awk/jq), and automation tips.

---

## 🏆 Global Master Category Navigation

| # | Domain | Core Focus & Tools Included | Count |
|:---:|:---|:---|:---:|
| **01** | **Information Gathering** | Nmap, Masscan, RustScan, Amass, Subfinder, Assetfinder, theHarvester, Shodan | **7** |
| **02** | **Vulnerability Analysis** | Nuclei, OpenVAS / GVM, Nikto, Searchsploit, Nessus Essentials, Trivy | **6** |
| **03** | **Web Application Analysis** | Burp Suite, FFUF, Gobuster, Feroxbuster, WPScan, OWASP ZAP, JWT Suite | **6** |
| **04** | **Database Assessment** | SQLmap, Commix, NoSQLMap, Native DBMS CLI Clients (mysql, psql, mssql-cli) | **4** |
| **05** | **Password Cracking** | Hashcat, John the Ripper, Hydra, Medusa, CeWL, Crunch | **5** |
| **06** | **Wireless Attacks** | Aircrack-ng Suite, Kismet, Wifite, Reaver, Pixiewps, Airgeddon | **4** |
| **07** | **Reverse Engineering** | Ghidra, Radare2, GDB / PEDA / GEF, APKTool, Jadx, strings, objdump | **4** |
| **08** | **Exploitation Frameworks**| Metasploit Framework, Msfvenom, Impacket, NetExec (CrackMapExec), Searchsploit | **4** |
| **09** | **Sniffing & Spoofing** | Wireshark, Tshark, TCPDump, Ettercap, Bettercap, Responder, Macchanger | **4** |
| **10** | **Privilege Escalation** | LinPEAS, WinPEAS, BloodHound, Chisel, Evil-WinRM, Mimikatz, SharpHound | **5** |
| **11** | **Forensics & Incident Response** | Autopsy, Volatility 3, Foremost, Binwalk, Scalpel, Sleuth Kit | **4** |
| **12** | **Reporting & Automation** | Faraday Dashboard, Dradis Framework, Netcat relays, Socat tunnels | **4** |

---

## 📁 Vault Directory Structure

```text
Kali-Linux-Tools-Handbook/
├── 00-Kali-Linux-Tools-Handbook-Master-Index.md          # Global Master Navigation Hub
├── 01-Information-Gathering/                             # Active/passive recon, OSINT & port scanners
├── 02-Vulnerability-Analysis/                            # CVE scanners, web & network auditors
├── 03-Web-Application-Analysis/                          # HTTP proxies, path fuzzers, CMS audit tools
├── 04-Database-Assessment/                               # SQL injection engines & direct database CLIs
├── 05-Password-Cracking-and-Authentication/              # Offline GPU hash crackers & online bruteforcers
├── 06-Wireless-Attacks/                                  # 802.11 Wi-Fi auditing & WPA handshake tools
├── 07-Reverse-Engineering-and-Disassembly/               # Static/dynamic binary analysis & decompilers
├── 08-Exploitation-Frameworks/                           # C2, payload generators & AD exploitation
├── 09-Sniffing-and-Spoofing/                             # Protocol sniffers, ARP spoofing & MiTM
├── 10-Post-Exploitation-and-Privilege-Escalation/        # Local enumeration, domain graphs & pivoting
├── 11-Forensics-and-Incident-Response/                   # Memory triage, disk forensics & carving
└── 12-Reporting-Utilities-and-Automation/                # Security documentation & tunnel utilities
```

---

## 🚀 Obsidian Setup & Navigation

1. Download and open [Obsidian](https://obsidian.md).
2. Click **Open folder as vault** and select this directory.
3. Open **`00-Kali-Linux-Tools-Handbook-Master-Index.md`** as your homepage.
4. Utilize `Ctrl + O` (Quick Switcher) to instantly jump between any tool guide or command matrix.

---

## ⚖️ Ethical & Educational Disclaimer

> **DISCLAIMER:** The documentation provided in this handbook is intended solely for educational instruction, authorized security evaluations, and defensive hardening. Running these tools against systems without prior authorization is strictly prohibited.
