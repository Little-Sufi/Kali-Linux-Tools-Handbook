# 🛠️ Tool Master Guide: OWASP ZAP (ZAPROXY) & Open-Source Proxy Tools

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: OWASP ZAP (Zed Attack Proxy)
> - **Category**: Automated Open-Source Web Application Security Scanner & Proxy (#1 Open Source Choice)
> - **License**: Open Source (Apache-2.0)
> - **Installation Command**: `sudo apt update && sudo apt install -y zaproxy`
> - **Binary Path**: `/usr/bin/zaproxy`
> - **Default Daemon Port**: `http://127.0.0.1:8080` or `http://127.0.0.1:8090`
> - **API Key / Config Path**: `~/.ZAP/zap.properties`
> - **Primary Objective**: Provides an automated vulnerability scanner, active/passive web crawler, HTTP proxy daemon, and REST API integration for DevSecOps CI/CD security pipelines.

---

## ⚡ 1. Execution Architecture & Automation Modes

```
                                  ┌────────────────────────────────┐
                                  │      ZAP Core Engine Daemon    │
                                  └───────────────┬────────────────┘
                                                  │
                ┌─────────────────────────────────┼─────────────────────────────────┐
                │                                 │                                 │
                ▼                                 ▼                                 ▼
┌───────────────────────────────┐ ┌───────────────────────────────┐ ┌───────────────────────────────┐
│     GUI Desktop Mode          │ │     Headless Daemon / API     │ │    Docker / CI-CD Pipeline    │
│  (Interactive Penetration     │ │  (REST API Control & Automation│ │  (zap-baseline.py /           │
│   Testing & Manual Proxy)     │ │   via Port 8080 + API Key)    │ │   zap-full-scan.py Scripts)   │
└───────────────────────────────┘ └───────────────────────────────┘ └───────────────────────────────┘
```

---

## 📋 2. Headless CLI & Docker Automation Reference Matrix

| Script / Command | Target Parameter | Operational Function | Syntax Example |
| :--- | :--- | :--- | :--- |
| `zap-baseline.py` | `-t <target_url>` | Passive scan against target URL (suitable for CI/CD regression testing) | `zap-baseline.py -t https://target.company.com -g gen.conf` |
| `zap-full-scan.py` | `-t <target_url>` | Full active spider + active vulnerability scan against target URL | `zap-full-scan.py -t https://target.company.com -r report.html` |
| `zap-api-scan.py` | `-t <openapi.json>`| Automated REST API vulnerability audit using OpenAPI/Swagger spec | `zap-api-scan.py -t swagger.json -f openapi -r api_report.html` |
| `zaproxy -daemon` | `-port 8080` | Starts headless ZAP daemon accepting REST API queries | `zaproxy -daemon -port 8080 -config api.key=secretkey` |

---

## 💻 3. Operational Command Workflows

```bash
# 1. Execute Headless Passive Security Baseline Scan in Docker
docker run -v $(pwd):/zap/wrk/:rw -t zaproxy/zap-stable zap-baseline.py -t https://example.com -r baseline_report.html

# 2. Automated REST API Audit using Swagger Definition File
docker run -v $(pwd):/zap/wrk/:rw -t zaproxy/zap-stable zap-api-scan.py -t https://api.example.com/v1/swagger.json -f openapi -r api_security_audit.html
```
