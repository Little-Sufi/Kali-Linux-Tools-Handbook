# 🔍 Category 01: Information Gathering & Reconnaissance — Master Overview

> [!INFO] 📌 **Domain Definition & Scope**
> Information gathering is the foundational phase of any penetration test or security assessment. It is divided into **Passive Reconnaissance** (OSINT, metadata scraping, DNS historical record searches without directly alerting the target) and **Active Reconnaissance** (port scanning, service interrogation, packet crafting, ARP sweeps).

---

## 🏆 Tool Selection & Efficiency Matrix

| Assessment Task | Primary Tool (#1 Choice) | Secondary / Advanced Alternatives | Protocol / Layer |
| :--- | :--- | :--- | :--- |
| **Comprehensive Port & Service Auditing** | **Nmap** | Masscan, RustScan | TCP, UDP, ICMP, SCTP |
| **Internet-Wide / Large Subnet Scanning** | **Masscan** | ZMap, RustScan | Asynchronous Raw SYN |
| **OSINT & Subdomain Graph Mapping** | **OWASP Amass** | Subfinder, Assetfinder, Findomain | Passive APIs, DNS |
| **Email, Employee & Metadata Harvesting** | **theHarvester** | SpiderFoot, Recon-ng | Public Search APIs |
| **DNS Zone & Infrastructure Auditing** | **dnsrecon** | fierce, dig, nslookup | UDP/TCP Port 53 |
| **Local Layer-2 MAC/IP Host Discovery** | **Netdiscover** | Arping, Nmap (-sn -PR) | ARP (Layer 2) |
| **Custom Packet Crafting & Firewall Testing**| **Hping3** | Nmap (raw packet modes) | IP, ICMP, raw TCP/UDP |

---

## 📂 Comprehensive Tool Master Guides in Category 01

1. 🛠️ [01-Nmap-Exhaustive-Master-Guide.md](./01-Nmap-Exhaustive-Master-Guide.md)
   - Deep technical flag matrix, TCP/UDP state mechanics, ping sweeps, 65k port discovery pipelines, and NSE SMB vulnerability auditing.
2. 🛠️ [02-Masscan-RustScan-ZMap-HighSpeed-Scanners.md](./02-Masscan-RustScan-ZMap-HighSpeed-Scanners.md)
   - Asynchronous SYN scanning engines, RustScan multi-threading with Nmap piping, and ZMap IPv4 surveying.
3. 🛠️ [03-OWASP-Amass-Attack-Surface-Mapping.md](./03-OWASP-Amass-Attack-Surface-Mapping.md)
   - Amass subcommands (`enum`, `intel`, `viz`, `track`, `db`), passive OSINT gathering, and active DNS graph mapping.
4. 🛠️ [04-Subdomain-Discovery-Suite-Subfinder-Assetfinder-Findomain.md](./04-Subdomain-Discovery-Suite-Subfinder-Assetfinder-Findomain.md)
   - Subfinder, Assetfinder, and Findomain passive API aggregation and Unix pipeline integration.
5. 🛠️ [05-OSINT-Frameworks-Recon-ng-Spiderfoot-theHarvester-Shodan.md](./05-OSINT-Frameworks-Recon-ng-Spiderfoot-theHarvester-Shodan.md)
   - Recon-ng workspace database setup, theHarvester search engine scraping, SpiderFoot local GUI server (`127.0.0.1:5001`), and Shodan CLI API queries.
6. 🛠️ [06-DNS-Enumeration-dnsrecon-fierce-dig-nslookup.md](./06-DNS-Enumeration-dnsrecon-fierce-dig-nslookup.md)
   - `dnsrecon` record enumeration, `dig` manual TXT queries, and AXFR zone transfer attempts.
7. 🛠️ [07-Network-Layer2-Layer3-Netdiscover-Hping3-Arping.md](./07-Network-Layer2-Layer3-Netdiscover-Hping3-Arping.md)
   - `netdiscover` active/passive ARP sweeps, `hping3` custom TCP SYN packet crafting, and fire-walking traceroutes.
