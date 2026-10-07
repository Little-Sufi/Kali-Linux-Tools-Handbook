# 🛠️ Tool Master Guide: Gobuster, Feroxbuster & Dirb (Content Discovery Suite)

> [!INFO] 📋 **Root Metadata**
> - **Category**: Directory, File, Subdomain & S3 Bucket Discovery Suite
> - **Tools Covered**: `gobuster`, `feroxbuster`, `dirb`
> - **Installations**: `sudo apt update && sudo apt install -y gobuster feroxbuster dirb`
> - **Binary Paths**: `/usr/bin/gobuster`, `/usr/bin/feroxbuster`, `/usr/bin/dirb`
> - **Primary Objective**: Performs multi-threaded URI brute-forcing across web applications, DNS subdomains, Virtual Hosts, Amazon S3 storage buckets, and recursive file paths.

---

## 📋 1. Tool Selection & Comparison Matrix

| Feature / Metric | Gobuster | Feroxbuster | Dirb |
| :--- | :--- | :--- | :--- |
| **Language / Engine** | Go (Goroutines) | Rust (Tokio Async Engine) | C (POSIX Sockets) |
| **Recursive Fuzzing** | Manual per directory | Automatic recursive tree depth | Automatic linear recursion |
| **Supported Modes** | `dir`, `dns`, `vhost`, `s3`, `fuzz` | `dir` (Recursive HTTP) | `dir` |
| **Speed Rating** | ⚡ High (1,000+ req/sec) | ⚡⚡ Ultra-High (3,000+ req/sec)| 🐢 Slow (Legacy single-thread)|

---

## 📋 2. Gobuster Subcommand & Flag Matrix

| Subcommand Mode | Target Flag | Key Option Flags | Operational Description |
| :--- | :--- | :--- | :--- |
| `gobuster dir` | `-u <url>` | `-w <list>`, `-x <exts>`, `-t <threads>`, `-k` | Directory and file enumeration |
| `gobuster dns` | `-d <domain>` | `-w <list>`, `-r <resolver>`, `-c` | Subdomain DNS brute-forcing |
| `gobuster vhost`| `-u <url>` | `-w <list>`, `--append-domain` | Virtual host HTTP header enumeration |
| `gobuster s3` | `--wordlist` | `-b <bucket>`, `-v` | Unauthenticated AWS S3 bucket hunting |

---

## 💻 3. Practical Operational Workflows

### Scenario A: Gobuster High-Speed Directory & File Enumeration
```bash
# Brute-force directories with .php, .html, and .json extensions using 50 threads
gobuster dir -u http://10.10.10.50/ -w /usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt -x php,html,json -t 50 -k -o gobuster_results.txt
```

### Scenario B: Feroxbuster Automatic Recursive Fuzzing
```bash
# Perform automatic recursive directory search up to 3 levels deep while bypassing SSL errors
feroxbuster --url http://10.10.10.50/ --wordlist /usr/share/seclists/Discovery/Web-Content/raft-medium-files.txt --depth 3 -x php,txt,config -k -o ferox_recursive.txt
```
