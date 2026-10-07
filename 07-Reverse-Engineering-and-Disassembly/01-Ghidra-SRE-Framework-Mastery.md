# 🛠️ Tool Master Guide: Ghidra Software Reverse Engineering Framework

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: Ghidra (NSA Software Reverse Engineering Framework)
> - **Category**: Binary Decompiler & Reverse Engineering Suite (#1 Choice)
> - **License**: Open Source (Apache-2.0)
> - **Installation Command**: `sudo apt update && sudo apt install -y ghidra`
> - **Binary Path**: `/usr/bin/ghidra`
> - **Headless Script Path**: `/usr/share/ghidra/support/analyzeHeadless`
> - **Extensions Directory**: `/usr/share/ghidra/Ghidra/Extensions/`
> - **Primary Objective**: Analyzes compiled binary executables (x86, x64, ARM, MIPS, PowerPC), decompiles assembly machine code into high-level pseudo-C code, performs static analysis, parses data structures, and supports headless Python/Java SRE automation scripts.

---

## ⚡ 1. Ghidra Decompiler Pipeline Architecture

```
┌──────────────────────────────────────────────────────────────────────────┐
│                         Binary File (ELF / PE / Mach-O)                  │
└────────────────────────────────────┬─────────────────────────────────────┘
                                     │
                                     ▼
┌────────────────────────────────────────────────────────────────────────## 📋 2. Ghidra UI Windows & Shortcuts Matrix

| Window / Function | Key Shortcut | Primary SRE Function |
| :--- | :--- | :--- |
| **Decompiler View** | `Ctrl + Shift + E` | Displays decompiled pseudo-C code for selected assembly function |
| **Rename Symbol** | `L` | Renames selected variable, function name, or memory label |
| **Change Data Type** | `T` | Changes variable type (e.g. `undefined4` -> `int` or `char *`) |
| **Find Cross References**| `Ctrl + Shift + F` / `Ctrl + Shift + C` | Shows all functions calling or referencing selected address/variable |
| **Bookmark Location** | `Ctrl + D` | Adds comment or tag bookmark to current disassembly address |
| **Edit Structure** | `Shift + [ / ]` | Edits C structure member definitions and offsets |

---

## 💻 3. Operational Command & Scripting Workflows

### Scenario A: Static Vulnerability & Logic Analysis Workflow
```bash
# 1. Start Ghidra GUI Environment
ghidra &

# 2. In Ghidra Window:
# File -> New Project -> Non-Shared Project -> Name "Firmware_Analysis"
# File -> Import File -> Select "target_binary.elf" -> Accept Language Architecture Detection (x86_64:LE:64:default)
# Double-click target_binary.elf to open CodeBrowser -> Click "Yes" when prompted to analyze
# Enable default analysis options (Decompiler Parameter ID, Reference Analyzer, Demangler) -> Click "Analyze"
# In Symbol Tree panel: Expand "Functions" -> Click "main"
# In Decompiler window: Inspect decompiled C code, rename obfuscated variable names using key "L", retype struct pointers using key "T"
```

### Scenario B: Headless Automated Binary Scanning Scripting
```bash
# Execute headless Ghidra analysis on binary file using custom Python script
/usr/share/ghidra/support/analyzeHeadless ~/ghidra_projects AuditProj -import sample.elf -postScript /usr/share/ghidra/Features/Base/ghidra_scripts/FindCrypt.py
```
