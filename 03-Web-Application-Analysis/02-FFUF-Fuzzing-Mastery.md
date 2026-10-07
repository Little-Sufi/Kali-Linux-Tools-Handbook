# 🛠️ Tool Master Guide: FFUF (Fuzz Faster U Fool)

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: FFUF (Fuzz Faster U Fool)
> - **Category**: High-Speed Web Directory & Parameter Fuzzer (#1 Choice)
> - **License**: Open Source (MIT)
> - **Installation Command**: `sudo apt update && sudo apt install -y ffuf` or `go install github.com/ffuf/ffuf/v2@latest`
> - **Binary Path**: `/usr/bin/ffuf` or `~/go/bin/ffuf`
> - **Configuration File**: `~/.config/ffuf/ffufrc`
> - **Primary Objective**: Delivers ultra-high-speed web path discovery, virtual host identification, GET/POST parameter fuzzing, and custom HTTP header injection leveraging Go routines and channels.

---

## ⚡ 1. Execution Engine & Multi-Wordlist Mechanics

FFUF uses a concurrent Go worker engine:

```
┌──────────────────────────────────────────────────────────────────────────┐
│                   Target Specifier (-u URL with FUZZ)                    │
└────────────────────────────────────┬─────────────────────────────────────┘
                                     │
                                     ▼
┌──────────────────────────────────────────────────────────────────────────┐
│              Multi-Threaded Go Routines (Worker Threads -t)              │
│  ┌──────────────────────┐   ┌────────────────────────┐   ┌────────────┐  │
│  │ Wordlist Stream (-w) │──►│ Raw HTTP Request Engine│──►│ Response   │  │
│  │ (FUZZ / W1 / W2)     │   │ (GET / POST / HEAD)    │   │ Parser     │  │
│  └──────────────────────┘   └────────────────────────┘   └─────┬──────┘  │
└────────────────────────────────────────────────────────────────┼─────────┘
                                                                 │
                                                                 ▼
                                                ┌──────────────────────────┐
                                                │   Matcher / Filter Engine│
                                                │   (-mc/-fc, -fs, -mr)    │
                                                └──────────────────────────┘
```

---

## 📋 2. Exhaustive Flag & Parameter Reference Matrix

| Flag Category | Flag / Parameter | Description & Technical Function | Syntax Example |
| :--- | :--- | :--- | :--- |
| **Target Specs** | `-u <url>` | Target URL containing the `FUZZ` placeholder | `ffuf -u http://10.10.10.50/FUZZ -w list.txt` |
| | `-w <path[:KEY]>` | Path to wordlist file. Can define custom keywords (`-w list.txt:W1`) | `ffuf -u http://W1/W2 -w hosts.txt:W1 -w paths.txt:W2` |
| | `-e <exts>` | Comma-separated file extensions to append to `FUZZ` | `-e .php,.html,.txt` |
| | `-dirsearch-compat`| Appends `%EXT%` matching dirsearch behavior | `-dirsearch-compat` |
| **Response Matchers**| `-mc <codes>`| Match specific HTTP response status codes (default: 200,204,301,302,307,401,403) | `-mc 200,301,302` |
| | `-ms <size>` | Match responses matching exact byte size | `-ms 1492` |
| | `-mw <words>`| Match responses matching exact word count | `-mw 42` |
| | `-mr <regex>`| Match responses containing regular expression pattern | `-mr "admin_token"` |
| **Response Filters** | `-fc <codes>`| Filter out specific HTTP response status codes | `-fc 404,403` |
| | `-fs <size>` | Filter out responses matching exact byte size | `-fs 1492` |
| | `-fw <words>`| Filter out responses matching exact word count | `-fw 42` |
| | `-fr <regex>`| Filter out responses matching regular expression pattern | `-fr "Not Found"` |
| **Performance** | `-t <threads>`| Number of concurrent thread workers (default: 40) | `-t 100` |
| | `-rate <reqs>` | Maximum number of requests per second | `-rate 200` |
| | `-p <delay>` | Delay in seconds between requests | `-p 0.1` |
| | `-recursion` | Automatically recurses into discovered subdirectories | `-recursion -recursion-depth 2` |
| **HTTP Headers** | `-H <header>`| Custom HTTP header (can use `FUZZ` inside headers) | `-H "Cookie: PHPSESSID=xyz"` |
| | `-X <method>`| Specifies HTTP Method (GET, POST, PUT, DELETE) | `-X POST -d "user=admin&pass=FUZZ"` |
| **Output** | `-o <file>` | Output file destination path | `-o results.json -of json` |
| | `-of <format>`| Output format (`json, html, md, csv, ejson`) | `-of html -o report.html` |

---

## 💻 3. Practical Operational Workflows

### Scenario A: Recursive Web Path & Extension Fuzzing
```bash
# Perform recursive directory discovery appending .php and .txt extensions
ffuf -u http://10.10.10.50/FUZZ -w /usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt -e .php,.txt -recursion -recursion-depth 2 -mc 200,301,302 -o ffuf_dirs.json -of json
```

### Scenario B: Virtual Host (VHOST) Subdomain Discovery
```bash
# Discover hidden subdomains on target IP by fuzzing HTTP Host header (Filtering out static response size 1492)
ffuf -u http://10.10.10.50 -H "Host: FUZZ.example.com" -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -fs 1492 -o vhosts.txt
```

### Scenario C: POST Parameter Name & Value Fuzzing
```bash
# Fuzz hidden POST form parameters
ffuf -u http://10.10.10.50/login.php -X POST -d "FUZZ=test" -H "Content-Type: application/x-www-form-parser" -w /usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt -fs 0
```
