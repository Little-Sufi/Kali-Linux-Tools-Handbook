# 🛠️ Tool Master Guide: Hashcat (GPU Password Cracking Engine)

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: Hashcat
> - **Category**: GPU-Accelerated Offline Hash Recovery Engine (#1 Choice)
> - **License**: Open Source (MIT)
> - **Installation Command**: `sudo apt update && sudo apt install -y hashcat`
> - **Binary Path**: `/usr/bin/hashcat`
> - **Rules Directory**: `/usr/share/hashcat/rules/`
> - **Masks Directory**: `/usr/share/hashcat/masks/`
> - **Session Output File**: `~/.local/share/hashcat/hashcat.potfile`
> - **Primary Objective**: Leverages raw GPU OpenCL/CUDA compute cores to crack cryptographic password hashes (NTLM, Kerberos, WPA2/WPA3, MD5, SHA-256, bcrypt, scrypt, Argon2) at speeds exceeding billions of calculations per second.

---

## ⚡ 1. Compute Architecture & Attack Modes

```
┌──────────────────────────────────────────────────────────────────────────┐
│                          Input Hash File (-m Mode)                       │
└────────────────────────────────────┬─────────────────────────────────────┘
                                     │
                                     ▼
┌──────────────────────────────────────────────────────────────────────────┐
│                       Hashcat Core Compute Engine                        │
│  ┌──────────────────────┐   ┌────────────────────────┐   ┌────────────┐  │
│  │ Attack Mode Selector │──►│ Rules / Mask Engine    │──►│ GPU Compute│  │
│  │ (-a 0/1/3/6/7)       │   │ (best64.rule / ?u?l?d) │   │ (CUDA/OCL) │  │
│  └──────────────────────┘   └────────────────────────┘   └─────┬──────┘  │
└────────────────────────────────────────────────────────────────┼─────────┘
                                                                 │
                                                                 ▼
                                                ┌──────────────────────────┐
                                                │ Cracked Password Output  │
                                                │ (--outfile / potfile)    │
                                                └──────────────────────────┘
```

---

## 📋 2. Hash Mode Reference Matrix (`-m`)

| Hash Mode Code | Target Hash / Security Protocol | Example Hash Format / Source |
| :--- | :--- | :--- |
| `-m 0` | **MD5** | `8743b02016e6027003750fe804038e10` |
| `-m 100` | **SHA1** | `b89eaac7e61417341b710b727768294d0e6a277b` |
| `-m 1000` | **NTLM** | `31d6cfe0d16ae931b73c59d7e0c089c0` (Windows SAM/NTDS) |
| `-m 1800` | **sha512crypt ($6$)** | `$6$salt$hash...` (Linux `/etc/shadow`) |
| `-m 5600` | **NetNTLMv2 / NTLMv2** | `user::domain:server_challenge:ntlmv2_hash...` (Responder) |
| `-m 13100` | **Kerberoasting (krb5tgs)**| `$krb5tgs$23$*user$domain$service...` (Active Directory) |
| `-m 18200` | **AS-REP Roasting (krb5asrep)**| `$krb5asrep$23$user@domain:hash...` (Active Directory) |
| `-m 22000` | **WPA-PBKDF2-PMKID / WPA2**| `WPA*01*...` or `WPA*02*...` (aircrack-ng `.hc22000`) |
| `-m 3200` | **bcrypt ($2a$, $2y$)** | `$2a$10$N9qo8uLOickgx2ZMRZoMye...` |

---

## 📋 3. Attack Modes (`-a`) & Custom Masks

- `-a 0` (**Straight / Wordlist**): Tests every word in wordlist against target hash.
- `-a 1` (**Combination**): Concatenates words from two separate dictionary files (Wordlist1 + Wordlist2).
- `-a 3` (**Brute-Force / Mask**): Tests characters based on defined mask pattern.
- `-a 6` (**Hybrid Wordlist + Mask**): Appends mask characters to wordlist words.
- `-a 7` (**Hybrid Mask + Wordlist**): Prepends mask characters to wordlist words.

### Custom Character Sets for Masks (`-a 3`)
- `?l` = `abcdefghijklmnopqrstuvwxyz`
- `?u` = `ABCDEFGHIJKLMNOPQRSTUVWXYZ`
- `?d` = `0123456789`
- `?s` = `!"#$%&'()*+,-./:;<=>?@[\]^_`{|}~`
- `?a` = `?l?u?d?s` (All ASCII printable characters)

---

## 📋 4. Exhaustive Flag Reference Matrix

| Flag Category | Flag / Option | Description & Technical Function | Syntax Example |
| :--- | :--- | :--- | :--- |
| **Hash & Attack** | `-m <mode>` | Specifies hash type code | `hashcat -m 1000 hashes.txt wordlist.txt` |
| | `-a <mode>` | Specifies attack mode (`0, 1, 3, 6, 7`) | `hashcat -m 1000 -a 3 hashes.txt ?u?l?d` |
| **Rules Engine** | `-r <rule_file>` | Applies rule modifications to wordlist entries | `-r /usr/share/hashcat/rules/best64.rule` |
| **Workload Tuning**| `-w <1-4>` | Sets GPU workload profile (`1` Low, `2` Default, `3` High, `4` Insane) | `hashcat -m 1000 -w 3 hashes.txt` |
| | `-O` | Enables optimized kernel code (Limits password length to 32 chars) | `hashcat -m 1000 -O hashes.txt` |
| **Output / Session**| `-o <file>` | Saves cracked plain-text credentials to file | `hashcat -m 1000 hashes.txt -o cracked.txt` |
| | `--show` | Displays previously cracked hashes from potfile | `hashcat -m 1000 hashes.txt --show` |
| | `--session <sname>`| Names session for pausing and resuming (`--restore`) | `hashcat --session audit01 --restore` |

---

## 💻 5. Practical Operational Workflows

### Scenario A: Active Directory NTLM Hash Cracking via Best64 Rules
```bash
# Crack extracted Active Directory NTDS.dit NTLM hashes using RockYou and Best64 rules
hashcat -m 1000 -a 0 ntlm_domain_hashes.txt /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule -w 3 -o cracked_ad.txt
```

### Scenario B: Kerberoasting Ticket Recovery (-m 13100)
```bash
# Crack Service Principal Name (SPN) Kerberos TGS tickets extracted via Impacket GetUserSPNs.py
hashcat -m 13100 -a 0 spn_tgs_hashes.txt /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/OneRuleToRuleThemAll.rule -o cracked_spn.txt
```

### Scenario C: WPA2-PSK PMKID / Handshake GPU Cracking (-m 22000)
```bash
# Crack captured WPA2 PMKID file exported from hcxpcapngtool
hashcat -m 22000 -a 0 wifi_capture.hc22000 /usr/share/wordlists/rockyou.txt -w 3
```

### Scenario D: Mask Attack for Complex Password Policies
```bash
# Target: 8-character passwords with 1 Uppercase, 5 Lowercase, 2 Digits (e.g. Password12)
hashcat -m 1000 -a 3 ntlm_hashes.txt "?u?l?l?l?l?l?d?d" -w 3
```
