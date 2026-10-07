# 🔬 Category 07: Reverse Engineering & Disassembly — Master Overview

> [!INFO] 📌 **Domain Definition & Scope**
> Reverse Engineering and Software Disassembly involves analyzing compiled binary executables (ELF, PE, Mach-O, APK, DEX), decompiling machine code into pseudo-C/Java source code, debugging running processes at the CPU register level, and analyzing malware/software vulnerabilities.

---

## 🏆 Tool Selection & Efficiency Matrix

| Assessment Task | Primary Tool (#1 Choice) | Secondary / Advanced Alternatives | Target Binary Format |
| :--- | :--- | :--- | :--- |
| **GUI Binary Decompilation & SRE** | **Ghidra** | IDA Pro, Cutter, Binary Ninja | ELF (Linux), PE (Windows), Mach-O (macOS) |
| **CLI Binary Disassembly & Scripting** | **Radare2 / Rizin** | Cutter (GUI wrapper for Rizin) | ELF, PE, Raw Shellcode |
| **Dynamic GDB Memory Debugging** | **GDB + GEF / Pwndbg** | EDB-Debugger, LLDB | x86, x64, ARM, MIPS Executables |
| **Android APK Decompilation & Reversing** | **JADX & APKTool** | Dex2jar, Frida, Objection | Android APK, DEX, Smali, JAR |

---

## 📂 Comprehensive Tool Master Guides in Category 07

1. 🛠️ [01-Ghidra-SRE-Framework-Mastery.md](./01-Ghidra-SRE-Framework-Mastery.md)
   - Ghidra headless/GUI decompiler, SLEIGH specification, project workspace setup, function renaming, structure parsing, and Python/Java SRE scripting.
2. 🛠️ [02-Radare2-and-Rizin-CLI-Framework.md](./02-Radare2-and-Rizin-CLI-Framework.md)
   - Radare2 (`r2`) & Rizin command matrices (`aaa`, `afl`, `pdf`, `pdf @ main`, `px @ esp`, `db`, `dc`), Visual Graph Mode (`VV`), and Cutter GUI integration.
3. 🛠️ [03-GDB-with-GEF-Exploit-Dev.md](./03-GDB-with-GEF-Exploit-Dev.md)
   - GDB enhanced with GEF (GDB Enhanced Features) / Pwndbg, register inspection, heap analysis (`heap`, `bins`), buffer overflow pattern generation (`pattern create`, `pattern offset`), and ROP gadget hunting (`rop`).
4. 🛠️ [04-APKTool-and-JADX-Android-Decompilation.md](./04-APKTool-and-JADX-Android-Decompilation.md)
   - APKTool binary decompilation (`apktool d`) / recompilation (`apktool b`), `AndroidManifest.xml` analysis, Smali code patch editing, and JADX Java GUI decompilation (`jadx-gui`).
