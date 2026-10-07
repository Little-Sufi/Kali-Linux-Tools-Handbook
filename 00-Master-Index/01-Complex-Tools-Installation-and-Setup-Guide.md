# ⚙️ Complex Tools Installation, Configuration & Setup Guide

> [!INFO] 📌 **Master Setup & Prerequisites Reference**
> Many advanced penetration testing, vulnerability management, and digital forensics tools require specific system services, database engines (PostgreSQL, Neo4j), runtime environments (Java JDK, Python venv, Go, Rust), and network interfaces (TUN/TAP) to function properly.
> 
> This guide details step-by-step installation, dependency configuration, service management, and troubleshooting for complex Kali Linux security utilities.

---

## 🧭 Master Table of Contents
1. [Wordlists & SecLists Infrastructure Setup](#1-wordlists--seclists-infrastructure-setup)
2. [Metasploit Framework & PostgreSQL Database Initialization](#2-metasploit-framework--postgresql-database-initialization)
3. [BloodHound & Neo4j Database Environment](#3-bloodhound--neo4j-database-environment)
4. [Greenbone Vulnerability Manager (OpenVAS / GVM) Installation](#4-greenbone-vulnerability-manager-openvas--gvm-installation)
5. [Ligolo-ng Modern Pivoting TUN Interface Configuration](#5-ligolo-ng-modern-pivoting-tun-interface-configuration)
6. [Ghidra Reverse Engineering Suite & Java OpenJDK Environment](#6-ghidra-reverse-engineering-suite--java-openjdk-environment)
7. [Volatility 3 Memory Forensics & Symbol Tables Installation](#7-volatility-3-memory-forensics--symbol-tables-installation)
8. [Go & Rust Toolchain Setup for Security CLI Utilities](#8-go--rust-toolchain-setup-for-security-cli-utilities)

---

## 📚 1. Wordlists & SecLists Infrastructure Setup

SecLists is the essential collection of multiple types of lists used during security assessments (usernames, passwords, URLs, sensitive data patterns, fuzzing payloads).

```bash
# 1. Install official SecLists package via APT
sudo apt update && sudo apt install -y seclists

# 2. Decompress default rockyou.txt wordlist
sudo gunzip /usr/share/wordlists/rockyou.txt.gz

# 3. Verify wordlist path structure
ls -la /usr/share/seclists/
# Location: /usr/share/seclists/Discovery/Web-Content/
# Location: /usr/share/seclists/Passwords/Common-Credentials/
```

---

## 💣 2. Metasploit Framework & PostgreSQL Database Initialization

Connecting Metasploit (`msfconsole`) to a local PostgreSQL database dramatically accelerates module searching, host tracking, credential storage, and workspace organization.

```bash
# Step 1: Start and enable PostgreSQL service on boot
sudo systemctl start postgresql
sudo systemctl enable postgresql

# Step 2: Initialize Metasploit Database
sudo msfdb init

# Step 3: Launch msfconsole and verify database connection
msfconsole -q
msf6 > db_status
# Expected Output: [*] Connected to msf. Connection type: postgresql.

# Step 4: Manage Workspaces inside MSF
msf6 > workspace -a target_company_audit
msf6 > workspace target_company_audit
```

---

## 🏰 3. BloodHound & Neo4j Database Environment

BloodHound requires the **Neo4j graph database** service running in the background to process Active Directory relationships.

```bash
# Step 1: Install BloodHound and Neo4j via APT
sudo apt update && sudo apt install -y bloodhound neo4j python3-bloodhound

# Step 2: Start Neo4j Database Console
sudo neo4j console

# Step 3: Open Browser at http://localhost:7474
# Default Login -> Username: neo4j | Password: neo4j
# Change default password to a secure custom password (e.g., BloodHound2026!)

# Step 4: Launch BloodHound GUI Application
bloodhound

# Step 5: Connect BloodHound to DB:
# Database URL: bolt://localhost:7687
# DB Username: neo4j
# DB Password: BloodHound2026!
```

---

## 🛡️ 4. Greenbone Vulnerability Manager (OpenVAS / GVM) Installation

GVM (formerly OpenVAS) is an enterprise vulnerability scanner. Setup requires syncing heavy vulnerability feeds (NVTs, SCAP, CERT data).

```bash
# Step 1: Install GVM Package
sudo apt update && sudo apt install -y gvm

# Step 2: Run Automated GVM Setup (Downloads vulnerability definitions feed - 15-30 mins)
sudo gvm-setup

# Step 3: Note the auto-generated Admin Password output at the end of setup!
# To reset admin password manually:
sudo gvm-check-setup
sudo runuser -u _gvm -- gvmd --user=admin --new-password=YourSecurePassword123

# Step 4: Start GVM Services
sudo gvm-start

# Step 5: Access Web Portal at https://127.0.0.1:9392 (Accept self-signed TLS cert)
```

---

## 🔀 5. Ligolo-ng Modern Pivoting TUN Interface Configuration

Ligolo-ng requires creating a virtual `TUN` network interface on the Linux attacker machine to route IP traffic seamlessly.

```bash
# Step 1: Create virtual TUN interface named 'ligolo'
sudo ip tuntap add user $USER mode tun dev ligolo

# Step 2: Bring TUN interface online
sudo ip link set dev ligolo up

# Step 3: Run Ligolo Proxy Server on Attacker Kali machine
./proxy -ingress-port 0.0.0.0:11601 -laddr 0.0.0.0:11601

# Step 4: (Inside Ligolo Proxy CLI after Agent connects):
session
1
ifconfig
# Add route to internal network subnet (e.g. 10.10.20.0/24)
sudo ip route add 10.10.20.0/24 dev ligolo
start
```

---

## ⚙️ 6. Ghidra Reverse Engineering Suite & Java OpenJDK Environment

Ghidra requires Java Development Kit (JDK 17 or higher) runtime.

```bash
# Step 1: Install OpenJDK 17
sudo apt update && sudo apt install -y openjdk-17-jdk ghidra

# Step 2: Verify Java installation version
java -version
# Expected: openjdk version "17.0.x"

# Step 3: Launch Ghidra GUI
ghidra
```

---

## 🔬 7. Volatility 3 Memory Forensics & Symbol Tables Installation

Volatility 3 requires Python 3 dependencies and Symbol Tables (ISF files) for parsing Windows/Linux kernel structures.

```bash
# Step 1: Clone Volatility 3 repository
git clone https://github.com/volatilityfoundation/volatility3.git
cd volatility3

# Step 2: Install required Python dependencies
pip3 install -r requirements.txt

# Step 3: Download official Windows/Linux symbol packages
python3 vol.py -h
# Volatility automatically downloads symbols on demand if internet is connected.
```

---

## 🛠️ 8. Go & Rust Toolchain Setup for Security CLI Utilities

Many modern security tools (FFUF, Gobuster, Subfinder, Feroxbuster, Rustscan) are compiled in Go or Rust.

```bash
# Step 1: Install Go and Rust (Cargo) compilers
sudo apt update && sudo apt install -y golang-go cargo

# Step 2: Add GOPATH and Cargo binaries to your shell profile (~/.zshrc or ~/.bashrc)
echo 'export PATH=$PATH:$HOME/go/bin:$HOME/.cargo/bin' >> ~/.zshrc
source ~/.zshrc

# Step 3: Install tools directly from source repositories
go install github.com/ffuf/ffuf/v2@latest
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
cargo install feroxbuster
```
