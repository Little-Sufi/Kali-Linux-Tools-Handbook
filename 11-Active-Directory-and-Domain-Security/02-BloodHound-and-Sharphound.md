# 🛠️ BloodHound & SharpHound — Active Directory Path Graphing

> [!INFO] 📌 **Tool Metadata**
> - **Category**: Active Directory Trust & Privilege Graph Mapping (#1 Choice)
> - **Installation**: `sudo apt install bloodhound` | Neo4j database backend
> - **Primary Objective**: Uses graph theory to reveal non-obvious relationship paths and misconfigurations within Active Directory domains (e.g. `AdminTo`, `HasSession`, `GenericAll`, `WriteDacl`).

---

## 💻 Operational Workflows

```bash
# Step 1: Collect Active Directory telemetry from domain host using SharpHound / BloodHound-python
python3 bloodhound.py -u jdoe -p Password123 -d corp.local -dc dc01.corp.local -c All

# Step 2: Start Neo4j Database Service on Attacker Kali machine
sudo neo4j start

# Step 3: Launch BloodHound GUI application and import JSON zip file
bloodhound

# Step 4: Run pre-built queries:
# - "Find Shortest Paths to Domain Admins"
# - "Find Principals with Foreign Domain Rights"
# - "Find Kerberoastable Users"
```
