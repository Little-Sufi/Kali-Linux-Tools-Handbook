# 🛠️ Tool Master Guide: John the Ripper & `*2john` Helpers

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: John the Ripper (JtR) jumbo-edition
> - **Category**: Multi-Format Password & Archive Key Recovery Engine (#1 Choice for Files/Archives)
> - **License**: Open Source (GPL-2.0)
> - **Installation Command**: `sudo apt update && sudo apt install -y john`
> - **Binary Path**: `/usr/bin/john`
> - **Helper Scripts Path**: `/usr/bin/*2john` or `/usr/share/john/`
> - **Configuration File**: `/etc/john/john.conf` or `/usr/share/john/john.conf`
> - **Potfile Location**: `~/.john/john.pot`
> - **Primary Objective**: Extracts hash structures from password-protected SSH keys, ZIP/RAR/7z archives, PDF documents, Keepass databases, Microsoft Office files, and unshadowed Linux shadow files to perform multi-threaded CPU hash recovery.

---

## 📋 1. `*2john` Hash Extraction Reference Matrix

| Target File Type | Extraction Command Syntax | Extracted Hash Output Format |
| :--- | :--- | :--- |
| **SSH Private Key** (`id_rsa`) | `ssh2john id_rsa > ssh_hash.txt` | `$6$`, `$rsa$`, or `$openbsd-bcrypt$` |
| **ZIP Archive** (`file.zip`) | `zip2john file.zip > zip_hash.txt` | `$zip2$` |
| **RAR Archive** (`file.rar`) | `rar2john file.rar > rar_hash.txt` | `$rar5$` |
| **PDF Document** (`doc.pdf`) | `pdf2john doc.pdf > pdf_hash.txt` | `$pdf$` |
| **KeePass DB** (`vault.kdbx`) | `keepass2john vault.kdbx > keepass_hash.txt`| `$keepass$` |
| **MS Office Doc** (`data.docx`)| `office2john data.docx > office_hash.txt` | `$office$` |
| **7-Zip Archive** (`data.7z`) | `7z2john.pl data.7z > 7z_hash.txt` | `$7z$` |
| **Linux Accounts** (`/etc/shadow`)| `unshadow /etc/passwd /etc/shadow > unshadowed.txt` | Combined Linux system password hash |

---

## 📋 2. Exhaustive Flag Reference Matrix

| Flag Category | Flag / Option | Description & Technical Function | Syntax Example |
| :--- | :--- | :--- | :--- |
| **Wordlist / Rules**| `--wordlist=<file>` | Specifies wordlist file for dictionary attack | `john --wordlist=rockyou.txt hash.txt` |
| | `--rules=<name>` | Enables mangling rules (`Jumbo`, `KoreLogic`, `Single`) | `john --wordlist=rockyou.txt --rules=Jumbo hash.txt` |
| **Format Override**| `--format=<type>` | Forces hash format (`NT`, `raw-md5`, `SSH`, `ZIP`, `KeePass`) | `john --format=SSH ssh_hash.txt` |
| **Incremental** | `--incremental` | Enables pure brute-force mode testing all permutations | `john --incremental hash.txt` |
| **Session Control** | `--session=<name>` | Names cracking session for pausing (`Ctrl+C`) and restoring | `john --restore=<name>` |
| **Output / Inspection**| `--show` | Displays previously cracked passwords from `john.pot` | `john --show hash.txt` |

---

## 💻 3. Operational Command Workflows

### Scenario A: Encrypted SSH Private Key Passphrase Recovery
```bash
# 1. Extract SSH hash from private key using ssh2john
ssh2john ~/.ssh/id_rsa > ssh_hash.txt

# 2. Run John the Ripper with RockYou wordlist and Jumbo rules
john --wordlist=/usr/share/wordlists/rockyou.txt --rules=Jumbo ssh_hash.txt

# 3. View cracked passphrase
john --show ssh_hash.txt
```

### Scenario B: Password-Protected ZIP / RAR / PDF File Recovery
```bash
# 1. Extract hash from encrypted ZIP file
zip2john secret_data.zip > zip_hash.txt

# 2. Crack ZIP hash using John
john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt

# 3. Display cracked ZIP password
john --show zip_hash.txt
```

### Scenario C: Unshadowing Linux /etc/shadow Files & Cracking
```bash
# 1. Combine /etc/passwd and /etc/shadow into single unshadowed file
sudo unshadow /etc/passwd /etc/shadow > unshadowed_hashes.txt

# 2. Crack unshadowed Linux account hashes
john --wordlist=/usr/share/wordlists/rockyou.txt unshadowed_hashes.txt
```
