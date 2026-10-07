# 📚 Kali Linux Security Tools Handbook — Master Index

> [!INFO] 📌 **Handbook Overview & Navigation Hub**
> Welcome to the **Comprehensive Kali Linux Security Tools Handbook**. This master reference guide organizes the most effective security auditing, penetration testing, and forensic investigation tools available in Kali Linux into 12 structured categories.
> 
> Each category features a **Master Overview** file containing domain efficiency matrices, tool breakdowns, and direct links to exhaustive tool guides.

---

## 🧭 Master Categories & Directory Structure

```
Kali-Linux-Tools-Handbook/
├── 00-Master-Index/
│   ├── 00-Handbook-Master-Index.md              <-- Master Navigation Hub
│   └── 01-Complex-Tools-Installation-and-Setup-Guide.md <-- Setup & Installation Guide
├── 01-Information-Gathering/
│   └── 00-Category-Master-Overview.md           <-- Reconnaissance Master Overview
├── 02-Vulnerability-Analysis/
│   └── 00-Category-Master-Overview.md           <-- Vulnerability Scanning Overview
├── 03-Web-Application-Analysis/
│   └── 00-Category-Master-Overview.md           <-- Web Security Master Overview
├── 04-Database-Assessment/
│   └── 00-Category-Master-Overview.md           <-- Database Assessment Overview
├── 05-Password-Cracking-and-Authentication/
│   └── 00-Category-Master-Overview.md           <-- Password Cracking Overview
├── 06-Wireless-Attacks/
│   └── 00-Category-Master-Overview.md           <-- Wireless Security Overview
├── 07-Reverse-Engineering-and-Disassembly/
│   └── 00-Category-Master-Overview.md           <-- Reverse Engineering Overview
├── 08-Exploitation-Frameworks/
│   └── 00-Category-Master-Overview.md           <-- Exploitation Frameworks Overview
├── 09-Sniffing-and-Spoofing/
│   └── 00-Category-Master-Overview.md           <-- Traffic Sniffing Overview
├── 10-Post-Exploitation-and-PrivEsc/
│   └── 00-Category-Master-Overview.md           <-- Post-Exploitation Overview
├── 11-Active-Directory-and-Domain-Security/
│   └── 00-Category-Master-Overview.md           <-- Active Directory Overview
└── 12-Forensics-and-Incident-Response/
    └── 00-Category-Master-Overview.md           <-- DFIR Forensics Overview
```

---

## 🏆 Gold Standard "Most Effective" Tool Matrix

> [!STAR] 📋 **Primary Tool Selection Matrix by Work Domain**

| Work Domain / Operational Goal | Most Effective Tool (#1 Choice) | Alternative / Specialized Tools |
| :--- | :--- | :--- |
| **Network Discovery & Port Scanning** | **Nmap** | Masscan, RustScan, ZMap |
| **Subdomain & OSINT Enumeration** | **Amass** | Subfinder, Assetfinder, theHarvester, Shodan CLI |
| **Web Proxy & Manual Inspection** | **Burp Suite Community / Pro** | OWASP ZAP, Caido, Mitmproxy |
| **Web Directory / Content Fuzzing** | **FFUF** | Gobuster, Feroxbuster, Dirsearch |
| **SQL Injection Automated Exploitation**| **SQLmap** | Commix, NoSQLMap |
| **GPU-Accelerated Password Cracking** | **Hashcat** | John the Ripper, Ophcrack |
| **Online Network Service Brute-Force** | **Hydra** | Medusa, Ncrack |
| **Wireless Security Auditing (802.11)** | **Aircrack-ng Suite** | Kismet, Wifite2, Reaver |
| **Active Directory Post-Exploitation** | **Impacket Suite** | BloodHound, Mimikatz, NetExec (CrackMapExec) |
| **Packet Sniffing & Traffic Analysis** | **Wireshark / Tshark** | Tcpdump, Ettercap, Bettercap |
| **Binary Disassembly & Reverse Eng.** | **Ghidra** | Radare2 / Rizin, GDB + GEF |
| **Memory Forensics & Dump Analysis** | **Volatility 3** | Autopsy, Sleuth Kit (TSK), Binwalk |

---

## 📂 Category Quick Links

- [00. Complex Tools Setup & Prerequisites Guide](./01-Complex-Tools-Installation-and-Setup-Guide.md)
- [01. Information Gathering & Reconnaissance](../01-Information-Gathering/00-Category-Master-Overview.md)
- [02. Vulnerability Assessment & Scanning](../02-Vulnerability-Analysis/00-Category-Master-Overview.md)
- [03. Web Application Security Testing](../03-Web-Application-Analysis/00-Category-Master-Overview.md)
- [04. Database Security Assessment](../04-Database-Assessment/00-Category-Master-Overview.md)
- [05. Password Cracking & Authentication Attacks](../05-Password-Cracking-and-Authentication/00-Category-Master-Overview.md)
- [06. Wireless Network Security Auditing](../06-Wireless-Attacks/00-Category-Master-Overview.md)
- [07. Reverse Engineering & Binary Analysis](../07-Reverse-Engineering-and-Disassembly/00-Category-Master-Overview.md)
- [08. Exploitation Frameworks & Utility Tools](../08-Exploitation-Frameworks/00-Category-Master-Overview.md)
- [09. Traffic Sniffing, Spoofing & MitM](../09-Sniffing-and-Spoofing/00-Category-Master-Overview.md)
- [10. Post-Exploitation & Privilege Escalation](../10-Post-Exploitation-and-PrivEsc/00-Category-Master-Overview.md)
- [11. Active Directory & Enterprise Domain Security](../11-Active-Directory-and-Domain-Security/00-Category-Master-Overview.md)
- [12. Digital Forensics & Incident Response (DFIR)](../12-Forensics-and-Incident-Response/00-Category-Master-Overview.md)
