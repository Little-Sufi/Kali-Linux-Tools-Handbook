# 🛠️ Tool Master Guide: Burp Suite Professional & Community

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: Burp Suite (Community & Professional)
> - **Category**: Web Application Intercepting Proxy & Penetration Testing Suite (#1 Choice)
> - **License**: Freemium / Commercial (PortSwigger)
> - **Installation Command**: Pre-installed on Kali Linux (`sudo apt install -y burpsuite`)
> - **Binary Path**: `/usr/bin/burpsuite`
> - **Default Proxy Address**: `127.0.0.1:8080`
> - **CA Certificate Import URL**: `http://burp` (when proxy listener is active)
> - **Config Directory**: `~/.BurpSuite/`
> - **Primary Objective**: Intercepts, inspects, modifies, and automates HTTP/HTTPS and WebSocket traffic between web browsers and target web application servers.

---

## ⚡ 1. Architectural Component Breakdown

```
 ┌────────────────┐     ┌────────────────────────────────────────────────────────┐     ┌────────────────┐
 │  Web Browser   │     │                    Burp Suite Proxy                    │     │ Target Server  │
 │  (Firefox/     │────►│  ┌──────────────┐   ┌──────────────┐   ┌────────────┐  │────►│   (Nginx/      │
 │   Chrome)      │◄────│  │ Intercept    │   │ Match&Replace│   │ HTTP History│ │◄────│    Apache)     │
 └────────────────┘     │  └──────────────┘   └──────────────┘   └────────────┘  │     └────────────────┘
                        └────────────────────────────┬───────────────────────────┘
                                                     │
                                                     ▼
                        ┌────────────────────────────────────────────────────────┐
                        │                Core Auditing Modules                   │
                        │ ┌────────────┐  ┌────────────┐  ┌───────────────────┐  │
                        │ │ Repeater   │  │ Intruder   │  │ Extender (BApp)   │  │
                        │ └────────────┘  └────────────┘  └───────────────────┘  │
                        └────────────────────────────────────────────────────────┘
```

### Core Module Functions:
1. **Proxy**: Real-time traffic interception, response modification, regex match-and-replace rules, WebSocket inspection.
2. **Target**: Hierarchical site map tree, scope definition (in-scope vs out-of-scope targets), vulnerability issue tracking.
3. **Repeater**: Manual request editing and retransmission for testing input validation, SQLi, and logic flaws.
4. **Intruder**: Automated payload injection engine with 4 attack position modes.
5. **Decoder**: Instant URL, HTML, Base64, Hex, Gzip, and Hash encoding/decoding engine.
6. **Sequencer**: Statistical entropy calculation of session tokens (`PHPSESSID`, `JSESSIONID`, JWT).
7. **Extender (BApp Store)**: Python/Java extension integration engine (Turbo Intruder, Autorize, Logger++).

---

## 📋 2. Keyboard Shortcuts Reference Matrix

| Action / Operation | Shortcut (Linux / Windows) | Primary Function |
| :--- | :--- | :--- |
| **Send to Repeater** | `Ctrl + R` | Instantly forwards selected HTTP request to Repeater tab |
| **Send to Intruder** | `Ctrl + I` | Instantly forwards selected HTTP request to Intruder tab |
| **Toggle Intercept** | `Ctrl + Shift + I` | Toggles Proxy Intercept ON or OFF |
| **Forward Request** | `Ctrl + F` | Forwards currently intercepted HTTP request to target server |
| **URL Encode (Key)** | `Ctrl + U` | Encodes selected highlighted text in URL format (`%20`, `%27`) |
| **URL Decode** | `Ctrl + Shift + U` | Decodes URL-encoded highlighted text |

---

## 📋 3. Intruder Attack Position Payload Modes

1. **Sniper**: Targets a single parameter position at a time using one wordlist. Ideal for fuzzing single parameters.
2. **Battering Ram**: Replaces all specified payload positions with the *exact same* wordlist value simultaneously.
3. **Pitchfork**: Uses multiple wordlists in parallel (e.g. Wordlist 1 for Username, Wordlist 2 for Password in sync).
4. **Cluster Bomb**: Tests every possible permutation of multiple wordlists (e.g. 100 usernames x 100 passwords = 10,000 requests).

---

## 🔌 4. Essential BApp Store Extensions

- **Autorize**: Automates Broken Access Control (BAC) and privilege escalation vulnerability detection.
- **Turbo Intruder**: High-speed HTTP request engine using custom Python scripts for race condition testing.
- **Param Miner**: Discovers hidden HTTP headers, GET parameters, and unlinked cookies.
- **Hackvertor**: Multi-nested tag-based encoding converter (e.g. `<@hex_entities>payload<@/hex_entities>`).

---

## 💻 5. Practical Operational Workflows

### Scenario A: HTTPS Interception & Certificate Installation
```bash
# 1. Start Burp Suite and verify Proxy Listener is running on 127.0.0.1:8080
# 2. Open Firefox -> Settings -> Network Settings -> Manual Proxy: 127.0.0.1 Port 8080
# 3. Browse to http://burp -> Download "cacert.der" certificate file
# 4. In Firefox: Settings -> Privacy & Security -> Certificates -> View Certificates -> Import -> Select cacert.der -> Check "Trust this CA to identify web sites"
```

### Scenario B: Intruder Credential Brute-Force Workflow
```bash
# 1. Intercept HTTP POST /login request in Proxy -> Send to Intruder (Ctrl + I)
# 2. Under Positions tab: Select Cluster Bomb attack type
# 3. Highlight username parameter -> Click "Add §" -> Highlight password parameter -> Click "Add §"
# 4. Under Payloads tab: Set Payload Set 1 to Usernames list -> Set Payload Set 2 to RockYou wordlist
# 5. Start Attack -> Sort results by Response Length or Status Code to identify valid login
```
