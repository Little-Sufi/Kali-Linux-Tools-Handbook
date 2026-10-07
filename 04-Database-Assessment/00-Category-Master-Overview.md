# 🗄️ Category 04: Database Assessment — Master Overview

> [!INFO] 📌 **Domain Definition & Scope**
> Database Assessment focuses on evaluating relational (MySQL, PostgreSQL, MSSQL, Oracle) and NoSQL (MongoDB, CouchDB, Redis) databases for SQL Injection (SQLi), command injection, default authentication credentials, unauthorized data extraction, and operating system takeover via database engines.

---

## 🏆 Tool Selection & Efficiency Matrix

| Assessment Task | Primary Tool (#1 Choice) | Secondary / Advanced Alternatives | Target Database Engine |
| :--- | :--- | :--- | :--- |
| **Automated SQL Injection & OS Takeover** | **SQLmap** | Commix, Metasploit | MySQL, MSSQL, PostgreSQL, Oracle |
| **Automated OS Command Injection** | **Commix** | SQLmap `--os-shell` | System Shells (Linux/Windows) |
| **NoSQL Injection & MongoDB Auditing** | **NoSQLMap** | Burp Suite + Custom Fuzzing | MongoDB, CouchDB |
| **MSSQL Direct CLI Interrogation & xp_cmdshell**| **sqsh / impacket-mssqlclient**| Metasploit `mssql_exec` | Microsoft SQL Server (Port 1433) |
| **Oracle TNS Listener & SID Enumeration** | **oscanner / sidguesser** | Metasploit `oracle_login` | Oracle TNS (Port 1521) |

---

## 📂 Comprehensive Tool Master Guides in Category 04

1. 🛠️ [01-SQLmap-Exhaustive-Master-Guide.md](./01-SQLmap-Exhaustive-Master-Guide.md)
   - SQLmap HTTP request parsing (`-r`), injection techniques (`--technique`), tamper scripts (`--tamper`), level/risk tuning, schema dumping, password extraction, and `--os-shell` spawning.
2. 🛠️ [02-Commix-Command-Injection-Mastery.md](./02-Commix-Command-Injection-Mastery.md)
   - Commix OS command injection engine, HTTP POST request file parsing, automated reverse shell spawning, and bypass tamper scripts.
3. 🛠️ [03-NoSQLMap-and-Document-DB-Suite.md](./03-NoSQLMap-and-Document-DB-Suite.md)
   - NoSQLMap MongoDB/CouchDB injection auditing, PHP `$ne` operator bypasses, and unauthenticated Redis key extraction.
4. 🛠️ [04-Database-Direct-CLI-Clients-Guide.md](./04-Database-Direct-CLI-Clients-Guide.md)
   - Direct database connection CLI tools (`mysql`, `psql`, `impacket-mssqlclient`, `sqsh`), SQL query syntax, and privilege escalation functions (`xp_cmdshell`).
