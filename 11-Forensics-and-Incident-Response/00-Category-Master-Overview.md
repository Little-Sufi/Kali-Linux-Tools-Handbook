# 🔍 Category 11: Forensics & Incident Response — Master Overview

> [!INFO] 📌 **Domain Definition & Scope**
> Forensics & Incident Response involves analyzing physical raw disk images, volatile RAM memory dumps, compiled IoT firmware binaries, and digital file artifacts to investigate security breaches, perform malware reverse engineering, and extract court-admissible digital evidence.

---

## 🏆 Tool Selection & Efficiency Matrix

| Assessment Task | Primary Tool (#1 Choice) | Secondary / Advanced Tool | Target Artifact Type |
| :--- | :--- | :--- | :--- |
| **GUI Disk Image & Artifact Forensics** | **Autopsy & Sleuth Kit (`fls`, `mmls`)** | Guymager, FTK Imager | E01, RAW (.dd/.img) Disk Images |
| **Volatile RAM Memory Forensics** | **Volatility 3** | LiME, WinDbg | Windows/Linux RAM dumps (.raw/.vmem) |
| **Firmware Carving & Binary Extraction** | **Binwalk** | Firmware Mod Kit (FMK), Sasquatch | Router/IoT Firmware (.bin/.rom) |
| **File Metadata & EXIF Extraction** | **ExifTool** | Exiv2, Strings | JPEG, PNG, PDF, DOCX, ELF, PE |

---

## 📂 Comprehensive Tool Master Guides in Category 11

1. 🛠️ [01-Autopsy-and-Sleuth-Kit-Digital-Forensics.md](./01-Autopsy-and-Sleuth-Kit-Digital-Forensics.md)
   - Autopsy digital forensics platform, Sleuth Kit CLI utilities (`mmls`, `fls`, `icat`), partition table carving, deleted file recovery, and timeline analysis.
2. 🛠️ [02-Volatility3-Memory-Forensics-Framework.md](./02-Volatility3-Memory-Forensics-Framework.md)
   - Volatility 3 memory analysis engine, symbol tables, process listing (`windows.pslist`), command line extraction (`windows.cmdline`), network connections (`windows.netscan`), and malware DLL injection detection (`windows.malfind`).
3. 🛠️ [03-Binwalk-and-Firmware-Analysis-Suite.md](./03-Binwalk-and-Firmware-Analysis-Suite.md)
   - Binwalk firmware analysis tool, magic byte signatures, automated filesystem extraction (`-e`, `--dd=".*"`), and SquashFS/CramFS file carving.
4. 🛠️ [04-ExifTool-and-Metadata-Forensics.md](./04-ExifTool-and-Metadata-Forensics.md)
   - ExifTool metadata reader, GPS coordinate extraction, author/software history auditing, and metadata stripping workflows.
