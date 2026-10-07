# 🛠️ Tool Master Guide: WPScan & CMS Auditing Suite (WordPress, Joomla, Drupal)

> [!INFO] 📋 **Root Metadata**
> - **Category**: Content Management System (CMS) Security Auditing Engine
> - **Tools Covered**: `wpscan`, `joomscan`, `droopescan`
> - **Installations**: `sudo apt update && sudo apt install -y wpscan joomscan` | `pip install droopescan`
> - **Binary Path**: `/usr/bin/wpscan`
> - **Config File**: `~/.wpscan/scan.json` or `~/.wpscan/wpscan.yml`
> - **API Token Portal**: `https://wpscan.com/` (Free API key enables WPVULN DB vulnerability lookups)
> - **Primary Objective**: Scans WordPress, Joomla, and Drupal web installations to detect vulnerable core versions, outdated plugins/themes, exposed user accounts, and execute login brute-forcing.

---

## 📋 1. WPScan Enumeration Matrix (`--enumerate`)

| Option Code | Enumeration Target | Operational Description |
| :--- | :--- | :--- |
| `vp` | **Vulnerable Plugins** | Scans for active plugins with known CVE entries in WPVULN DB |
| `ap` | **All Plugins** | Scans for all active/inactive installed plugins (Popular ~10,000 plugin list) |
| `vt` | **Vulnerable Themes** | Scans for active themes with known vulnerability entries |
| `at` | **All Themes** | Scans for all installed themes |
| `u` | **Usernames** | Enumerates valid WordPress user accounts via REST API (`/wp-json/wp/v2/users`) & author archives |
| `cb` | **Config Backups** | Searches for exposed `wp-config.php.bak` or `wp-config.php.old` backup files |
| `dbe` | **Database Dumps** | Searches for publicly accessible SQL export files in web root |

---

## 💻 2. Practical Operational Workflows

### Scenario A: Comprehensive WordPress Vulnerability & User Audit
```bash
# 1. Export WPScan API Token to environment
export WPSCAN_API_TOKEN="your_api_token_here"

# 2. Run full enumeration scan checking vulnerable plugins, themes, users, and backup files
wpscan --url https://target-blog.com --enumerate vp,vt,u,cb --api-token $WPSCAN_API_TOKEN -o wpscan_audit.json -f json
```

### Scenario B: WP-Login User Password Brute-Forcing
```bash
# Execute password brute-force against enumerated user "admin" using RockYou wordlist
wpscan --url https://target-blog.com --passwords /usr/share/wordlists/rockyou.txt --usernames admin -t 20
```

### Scenario C: Joomla & Drupal Auditing via JoomScan & Droopescan
```bash
# Scan target Joomla CMS site
joomscan -u https://joomla.target.com -ec

# Scan target Drupal CMS site
droopescan scan drupal -u https://drupal.target.com
```
