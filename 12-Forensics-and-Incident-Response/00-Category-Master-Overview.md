# 🔬 Category 12: Digital Forensics & Incident Response — Master Overview

> [!INFO] 📌 **Domain Definition & Scope**
> Digital Forensics and Incident Response (DFIR) tools analyze physical RAM memory dumps, recover deleted disk files, inspect file metadata, extract artifact timelines, and perform malware behavioral triage.

---

## 🏆 Tool Selection & Efficiency Matrix

| Assessment Task | Primary Tool (#1 Choice) | Secondary / Advanced Alternatives | Category / Type |
| :--- | :--- | :--- | :--- |
| **RAM Memory Forensics & Artifact Extraction**| **Volatility 3** | Rekall | Memory Forensics |
| **Digital Hard Drive Image Analysis** | **Autopsy / Sleuth Kit** | FTK Imager | Disk Forensics Platform |
| **Embedded Firmware Extraction** | **Binwalk** | Firmware Analysis Toolkit | IoT Firmware Analysis |

---

## 📂 Comprehensive Tool Master Guides in Category 12

1. 🛠️ [01-Volatility-3-Memory-Forensics-Mastery.md](./01-Volatility-3-Memory-Forensics-Mastery.md)
   - Volatility 3 plugin reference (`windows.pstree`, `windows.malfind`, `windows.hashdump`, `windows.dumpfiles`).
2. 🛠️ [02-Autopsy-and-Sleuth-Kit-Disk-Forensics.md](./02-Autopsy-and-Sleuth-Kit-Disk-Forensics.md)
   - Autopsy web platform setup, disk image processing, and forensic timeline analysis.
3. 🛠️ [03-Binwalk-Firmware-Analysis.md](./03-Binwalk-Firmware-Analysis.md)
   - Scanning raw binary firmware and automatically extracting embedded SquashFS file systems.
