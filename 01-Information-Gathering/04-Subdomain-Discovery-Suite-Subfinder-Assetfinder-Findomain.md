# 🛠️ Tool Master Guide: Subdomain Discovery Suite (Subfinder, Assetfinder, Findomain)

> [!INFO] 📋 **Root Metadata**
> - **Category**: Fast Subdomain Enumeration Utilities
> - **Tools Covered**: Subfinder, Assetfinder, Findomain
> - **Installations**:
>   - Subfinder: `sudo apt install subfinder` or `go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest`
>   - Assetfinder: `go install github.com/tomnomnom/assetfinder@latest`
>   - Findomain: Download binary / `cargo install findomain`
> - **Primary Objective**: Rapid passive subdomain aggregation across Certificate Transparency logs, VirusTotal, AlienVault, SecurityTrails, and Chaos feeds.

---

## ⚡ 1. Subfinder Deep Guide

Subfinder is a passive subdomain discovery tool designed by ProjectDiscovery that focuses on speed and source modularity.

```bash
# 1. Standard Passive Subdomain Search
subfinder -d example.com -o subfinder_subs.txt

# 2. Multi-Domain Batch Processing with JSON Output
subfinder -dL domains_list.txt -oJ -o subfinder_batch.json
```

---

## ⚡ 2. Assetfinder Deep Guide

Assetfinder discovers domains and subdomains related to a target organization using public transparency APIs.

```bash
# Search target domain and filter unique subdomains
assetfinder --subs-only example.com | sort -u > assetfinder_subs.txt
```

---

## ⚡ 3. Findomain Deep Guide

Findomain utilizes multi-threaded certificate transparency log monitoring and passive DNS queries to resolve host IP addresses fast.

```bash
# Search target domain and attempt IP address resolution
findomain -t example.com --resolve -u findomain_resolved.txt
```

---

## 💻 4. Combined Subdomain Pipeline Workflow (One-Liner Integration)

```bash
# Combine outputs from Subfinder, Assetfinder, and Findomain into single deduped list
(subfinder -d example.com; assetfinder --subs-only example.com; findomain -t example.com -q) | sort -u > all_combined_subdomains.txt
```
