# 🛠️ Tool Master Guide: Web API & JWT Security Suite (`jwt-tool`, `Kiterunner`, Postman)

> [!INFO] 📋 **Root Metadata**
> - **Category**: REST / GraphQL API Endpoint Enumeration & JSON Web Token (JWT) Security Suite
> - **Tools Covered**: `jwt-tool`, `Kiterunner` (`kr`), Postman, `GraphQLmap`
> - **Installations**:
>   - `jwt-tool`: `git clone https://github.com/ticarpi/jwt_tool.py.git && cd jwt_tool.py && python3 -m pip install -r requirements.txt`
>   - `Kiterunner`: `sudo apt install -y kiterunner` or binary install from asset releases
> - **Primary Objective**: Audits RESTful and GraphQL API endpoints for hidden routes, Broken Object Level Authorization (BOLA/IDOR), missing authentication, and tests JSON Web Tokens (JWT) for cryptographic signature vulnerabilities.

---

## 📋 1. `jwt-tool` Attack Vector Reference Matrix

| Attack Vector | Command Flag | Operational Mechanism |
| :--- | :--- | :--- |
| **"none" Algorithm Bypass** | `-X a` | Strips JWT signature and sets algorithm header to `"alg": "none"` |
| **HMAC Secret Key Brute-Force**| `-d wordlist.txt`| Brute-forces symmetric HS256 secret key signature using wordlist |
| **RS256 to HS256 Key Confusion**| `-X k -pk public.pem`| Signs token using public key as HMAC secret key to trick loose validators |
| **Claims Manipulation** | `-I -hc admin -v true` | Modifies payload claims (e.g. `"role": "admin"`) while keeping signature intact |

---

## 💻 2. Practical Operational Workflows

### Scenario A: Kiterunner API Route & Endpoint Discovery
```bash
# Perform high-speed API route discovery using schema dataset (routes-large.kite)
kr scan https://api.target.com/ -w routes-large.kite --max-parallel 50 -o json -f api_routes.json
```

### Scenario B: Automated JWT Signature Vulnerability Audit
```bash
# 1. Audit JWT for "none" algorithm and common header injection vulnerabilities
python3 jwt_tool.py "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..." -M at

# 2. Brute-force HMAC Secret Key with RockYou
python3 jwt_tool.py "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..." -d /usr/share/wordlists/rockyou.txt
```
