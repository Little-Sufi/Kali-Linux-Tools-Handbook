# 🛠️ Tool Master Guide: OSINT Frameworks (Recon-ng, SpiderFoot, theHarvester, Shodan CLI)

> [!INFO] 📋 **Root Metadata**
> - **Category**: Automated OSINT & Threat Intelligence Collection
> - **Tools Covered**: Recon-ng, SpiderFoot, theHarvester, Shodan CLI
> - **Installations**:
>   - Recon-ng: `sudo apt install recon-ng` | Path: `/usr/bin/recon-ng`
>   - SpiderFoot: `sudo apt install spiderfoot` | Path: `/usr/bin/spiderfoot`
>   - theHarvester: `sudo apt install theharvester` | Path: `/usr/bin/theHarvester`
>   - Shodan CLI: `pip install shodan` | Path: `/usr/local/bin/shodan`

---

## ⚡ 1. Recon-ng Web Reconnaissance Framework

Recon-ng provides a modular CLI framework for collecting public domain intelligence, contact emails, and host IP records.

```bash
# Start Recon-ng shell
recon-ng

# Inside Recon-ng interactive shell:
workspaces create target_corp
db insert domains example.com
modules load recon/domains-hosts/brute_hosts
run
show hosts
```

---

## ⚡ 2. theHarvester Email & Host Gatherer

```bash
# Harvest emails, subdomains, and host IPs using all search sources
theHarvester -d example.com -b all -l 500 -f harvester_results.xml
```

---

## ⚡ 3. SpiderFoot Threat Intelligence Engine

```bash
# Launch SpiderFoot web application GUI server on localhost:5001
spiderfoot -l 127.0.0.1:5001
```

---

## ⚡ 4. Shodan CLI Integration

```bash
# Initialize Shodan CLI with API Key
shodan init YOUR_SHODAN_API_KEY

# Query Shodan for exposed target host details and open services
shodan host 192.168.1.50
shodan search "org:'Target Corporation' product:Apache"
```
