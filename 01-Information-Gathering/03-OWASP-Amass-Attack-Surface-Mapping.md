# 🛠️ Tool Master Guide: OWASP Amass

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: OWASP Amass
> - **Category**: Attack Surface Mapping & Subdomain Graph Enumeration (#1 Choice)
> - **License**: Apache License 2.0
> - **Installation Command**: `sudo apt update && sudo apt install -y amass`
> - **Binary Path**: `/usr/bin/amass`
> - **Config File**: `~/.config/amass/config.ini`
> - **Database Dir**: `~/.config/amass/amass.json` / graph database engine
> - **Primary Objective**: In-depth network mapping and attack surface discovery of target organization domains using passive scraping, active DNS queries, ASN mapping, and graph database storage.

---

## 📋 1. Subcommand Reference Matrix

| Subcommand | Function & Operational Description | Primary Syntax Example |
| :--- | :--- | :--- |
| `amass enum` | Performs subdomain enumeration and network mapping | `amass enum -d example.com` |
| `amass intel` | Discovers root domains associated with an organization / ASN | `amass intel -org "Target Corp"` |
| `amass viz` | Generates graph network visualizations (Maltego, D3.js, Graphviz) | `amass viz -d3 -d example.com` |
| `amass track` | Tracks changes in domain infrastructure between different scan dates | `amass track -d example.com` |
| `amass db` | Interrogates stored graph database records for previous target scans | `amass db -show -d example.com` |

---

## 📋 2. Amass Enum Key Flags Matrix

| Flag | Function | Syntax Example |
| :--- | :--- | :--- |
| `-d <domain>` | Specifies primary target domain name | `amass enum -d example.com` |
| `-passive` | Discovers subdomains purely via OSINT sources (no target DNS hits) | `amass enum -passive -d example.com` |
| `-active` | Enables active DNS resolution and IP address validation | `amass enum -active -d example.com` |
| `-brute` | Enables dictionary-based DNS subdomain brute-forcing | `amass enum -active -brute -d example.com` |
| `-w <wordlist>`| Wordlist for DNS subdomain brute forcing | `-w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt` |
| `-src` | Displays data source names next to discovered subdomains | `amass enum -src -d example.com` |
| `-dir <path>` | Specifies custom database directory | `-dir ./amass_db` |
| `-o <file>` | Output text file destination | `-o subdomains.txt` |

---

## 💻 3. Operational Command Workflows

```bash
# 1. Passive Subdomain OSINT Discovery (Safe for initial stealth phase)
amass enum -passive -d example.com -src -o passive_subdomains.txt

# 2. Comprehensive Active Enumeration with Brute Force & Alterations
amass enum -active -d example.com -brute -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt -dir ./amass_project -o active_subdomains.txt
```
