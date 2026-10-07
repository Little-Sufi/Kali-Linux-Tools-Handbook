# 🏰 Category 11: Active Directory & Domain Security — Master Overview

> [!INFO] 📌 **Domain Definition & Scope**
> Active Directory and Domain Security tools assess enterprise Windows domain controllers, Kerberos authentication (Kerberoasting, AS-REP Roasting), BloodHound domain object graphing, SMB/RPC enumeration, and Pass-the-Hash domain dominance.

---

## 🏆 Tool Selection & Efficiency Matrix

| Assessment Task | Primary Tool (#1 Choice) | Secondary / Advanced Alternatives | Category / Type |
| :--- | :--- | :--- | :--- |
| **Active Directory Python Protocol Attacks**| **Impacket Suite** | NetExec (CrackMapExec) | AD Protocol Library |
| **Active Directory Trust & Path Graphing** | **BloodHound / SharpHound**| PingCastle | Graph Analysis Engine |
| **Multi-Protocol Password Spray & Audit** | **NetExec (CrackMapExec)** | Hydra, Impacket | AD Swiss Army Knife |

---

## 📂 Comprehensive Tool Master Guides in Category 11

1. 🛠️ [01-Impacket-Suite-Master-Guide.md](./01-Impacket-Suite-Master-Guide.md)
   - `GetNPUsers` (AS-REP Roasting), `GetUserSPNs` (Kerberoasting), `secretsdump` (NTDS.dit dumping), and `wmiexec`.
2. 🛠️ [02-BloodHound-and-Sharphound.md](./02-BloodHound-and-Sharphound.md)
   - SharpHound data collection, Neo4j database setup, and BloodHound pre-built graph path queries.
3. 🛠️ [03-NetExec-CrackMapExec.md](./03-NetExec-CrackMapExec.md)
   - NetExec SMB password spraying, Pass-the-Hash authentication, and remote LSA secret dumping.
