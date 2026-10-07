# 🛠️ Tool Master Guide: Layer 2 & Layer 3 Network Discovery (Netdiscover, Hping3, Arping)

> [!INFO] 📋 **Root Metadata**
> - **Category**: Ethernet ARP Sweeps & Custom TCP/IP Packet Injection
> - **Tools Covered**: Netdiscover, Hping3, Arping
> - **Installations**: Pre-installed on Kali Linux (`netdiscover`, `hping3`, `arping`)
> - **Primary Objective**: Discovering live MAC/IP hosts on local LAN subnets, bypassing ICMP firewall restrictions, and testing firewall filtering behavior with custom crafted TCP/UDP packets.

---

## ⚡ 1. Netdiscover Layer-2 ARP Discovery

```bash
# 1. Active ARP Sweep on local network interface eth0
sudo netdiscover -i eth0 -r 192.168.1.0/24

# 2. Passive Stealth ARP Monitoring (Sniffs ARP requests without transmitting frames)
sudo netdiscover -p -i eth0
```

---

## ⚡ 2. Hping3 Custom Packet Crafting Engine

```bash
# 1. Send 5 TCP SYN Packets to Port 80 (Custom SYN Scan)
sudo hping3 -S 192.168.1.50 -p 80 -c 5

# 2. Fire-walk / Traceroute using TCP SYN packets on port 443
sudo hping3 --traceroute -V -1 192.168.1.50 -p 443
```
