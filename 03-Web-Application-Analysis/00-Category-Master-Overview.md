# 🌐 Category 03: Web Application Analysis — Master Overview

> [!INFO] 📌 **Domain Definition & Scope**
> Web Application Security Analysis encompasses inspecting client-side and server-side HTTP/HTTPS interactions, discovery of unlinked directories/endpoints, parameter fuzzing, API route enumeration, authentication testing, and CMS vulnerability auditing.

---

## 🏆 Tool Selection & Efficiency Matrix

| Assessment Task | Primary Tool (#1 Choice) | Secondary / Advanced Alternatives | Protocol / Target Layer |
| :--- | :--- | :--- | :--- |
| **HTTP Traffic Interception & Tampering**| **Burp Suite Professional/Community**| OWASP ZAP, Caido, Mitmproxy | HTTP / HTTPS (Ports 80/443) |
| **High-Speed Path & Parameter Fuzzing** | **FFUF** | Gobuster, Feroxbuster | Go Web Fuzzer |
| **Recursive Directory & VHost Discovery**| **Feroxbuster / Gobuster** | Dirb, Dirsearch | Rust / Go Brute-Forcer |
| **WordPress CMS Vulnerability Auditing** | **WPScan** | Droopescan, CMSeeK | WordPress API & Core |
| **API Route & Endpoint Discovery** | **Kiterunner** | FFUF, Arjun | REST / OpenAPI / GraphQL |
| **JSON Web Token (JWT) Security Auditing**| **jwt-tool** | Burp JWT Editor Extension | JWT Token Signatures |

---

## 📂 Comprehensive Tool Master Guides in Category 03

1. 🛠️ [01-Burp-Suite-Complete-Mastery.md](./01-Burp-Suite-Complete-Mastery.md)
   - Intercept Proxy, Repeater, Intruder attack payload modes (Sniper, Pitchfork, Cluster Bomb), Decoder, Sequencer, and BApp Store extensions (Turbo Intruder, Autorize).
2. 🛠️ [02-FFUF-Fuzzing-Mastery.md](./02-FFUF-Fuzzing-Mastery.md)
   - FFUF directory, file extension, VHost, parameter fuzzing, status code filters (`-mc`/`-fc`), byte size filters (`-fs`), and JSON outputs.
3. 🛠️ [03-Gobuster-Feroxbuster-Dirb-Master-Guide.md](./03-Gobuster-Feroxbuster-Dirb-Master-Guide.md)
   - Gobuster modes (`dir`, `dns`, `vhost`, `s3`), Feroxbuster recursive Rust fuzzing (`feroxbuster`), and Dirb wordlist paths.
4. 🛠️ [04-WPScan-and-CMS-Auditing-Suite.md](./04-WPScan-and-CMS-Auditing-Suite.md)
   - WPScan API token configuration, plugin/theme enumeration, user identification, password brute-forcing, and JoomScan/Droopescan integration.
5. 🛠️ [05-OWASP-ZAP-and-Proxy-Tools.md](./05-OWASP-ZAP-and-Proxy-Tools.md)
   - OWASP ZAP automated scanner, Mitmproxy terminal console (`mitmproxy`/`mitmweb`), and Caido proxy setup.
6. 🛠️ [06-Web-API-and-JWT-Security-Suite.md](./06-Web-API-and-JWT-Security-Suite.md)
   - Kiterunner API route brute-forcing (`kr scan`), `jwt-tool` signature forgery and `kid` parameter injection, and Arjun parameter discovery.
