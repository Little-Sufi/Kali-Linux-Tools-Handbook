# 🛠️ Tool Master Guide: Radare2 & Rizin CLI Frameworks

> [!INFO] 📋 **Root Metadata**
> - **Category**: Command-Line Binary Disassembler & Hex Editor Frameworks
> - **Tools Covered**: Radare2 (`r2`), Rizin (`rizin`), Cutter (GUI)
> - **Installations**: `sudo apt update && sudo apt install -y radare2 rizin cutter`
> - **Binary Paths**: `/usr/bin/r2`, `/usr/bin/rizin`, `/usr/bin/cutter`
> - **Config Files**: `~/.radare2rc`, `~/.rizinrc`
> - **Primary Objective**: Provides scriptable CLI disassembly, hex editing, patch generation, binary diffing, and control-flow graph visualization.

---

## 📋 1. Core Radare2 / Rizin Command Matrix

| Command | Category | Technical Description |
| :--- | :--- | :--- |
| `aaa` | **Analysis** | Performs auto-analysis of functions, flags, calls, and cross-references |
| `afl` | **Function List** | Lists all functions analyzed in binary |
| `pdf @ main` | **Print Disassembly** | Prints disassembly graph/code for function `main` |
| `px 64 @ rsp` | **Print Hex** | Prints hex dump of 64 bytes at stack pointer register `rsp` |
| `VV` | **Visual Graph** | Switches to interactive visual control-flow execution graph mode |
| `wa nop @ 0x08048450`| **Write Patch** | Writes assembly instruction NOP (`0x90`) directly to address |
| `iI` | **Binary Header** | Displays binary architecture, protections (NX, Canary, PIE), and machine type |

---

## 💻 2. Operational Command Workflow

```bash
# 1. Open binary in write/patch mode (-w) and run analysis
r2 -w ./binary.elf

# 2. Execute analysis inside r2 shell
[0x00000000]> aaa
[0x00000000]> iI
[0x00000000]> afl
[0x00000000]> pdf @ main

# 3. Patch conditional jump to NOPs to bypass license check
[0x00000000]> wa nop @ 0x08048450
[0x00000000]> wa nop @ 0x08048451
[0x00000000]> q
```
