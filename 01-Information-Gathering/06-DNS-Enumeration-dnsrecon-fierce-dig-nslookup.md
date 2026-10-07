# 🛠️ Tool Master Guide: DNS Enumeration (dnsrecon, fierce, dig, nslookup)

> [!INFO] 📋 **Root Metadata**
> - **Category**: Domain Name System (DNS) Protocol Auditing
> - **Tools Covered**: `dnsrecon`, `fierce`, `dig`, `nslookup`
> - **Installations**: Pre-installed on Kali Linux (`dnsrecon`, `fierce`, `bind9-host`)
> - **Primary Objective**: Enumerating DNS records (A, AAAA, MX, NS, TXT, SOA, SRV), testing for misconfigured DNS Zone Transfers (AXFR), and brute-forcing subdomains.

---

## ⚡ 1. dnsrecon Master Guide

```bash
# 1. Standard DNS Record & Zone Transfer Attempt Scan
dnsrecon -d example.com -t std

# 2. DNS Subdomain Brute Force using Wordlist
dnsrecon -d example.com -D /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -t brt
```

---

## ⚡ 2. dig (Domain Information Groper) Manual Analysis

```bash
# 1. Attempt Manual DNS Zone Transfer (AXFR) against target Nameserver
dig AXFR @ns1.example.com example.com

# 2. Interrogate TXT Records (SPF, DMARC verification)
dig TXT example.com +short
```
