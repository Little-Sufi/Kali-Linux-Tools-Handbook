# 🛠️ Tool Master Guide: Autopsy & Sleuth Kit Digital Forensics Suite

> [!INFO] 📋 **Root Metadata**
> - **Category**: Digital Forensics & Disk Image Analysis Suite (#1 Choice)
> - **Tools Covered**: Autopsy (GUI), Sleuth Kit (`mmls`, `fls`, `icat`, `img_stat`)
> - **Installations**: `sudo apt update && sudo apt install -y autopsy sleuthkit`
> - **Binary Paths**: `/usr/bin/autopsy`, `/usr/bin/mmls`, `/usr/bin/fls`, `/usr/bin/icat`
> - **Primary Objective**: Analyzes raw disk images (RAW, E01, VHD), recovers deleted files, analyzes partition tables, and indexes web history, email artifacts, and registry hives.

---

## 📋 1. Sleuth Kit CLI Utility Reference Matrix

| CLI Utility | Operational Function | Syntax Example |
| :--- | :--- | :--- |
| `mmls` | Displays partition layout and sector offsets of raw disk image | `mmls target_disk.raw` |
| `fls` | Lists directory entries and inode numbers within disk partition | `fls -o 2048 target_disk.raw` |
| `icat` | Extracts file contents by specifying its inode number | `icat -o 2048 target_disk.raw 12845 > recovered_file.txt` |
| `srch_strings` | Extracts ASCII and Unicode strings from unallocated space | `srch_strings -a target_disk.raw > strings.txt` |

---

## 💻 2. Practical Operational Workflow

```bash
# 1. Inspect partition table of disk image to find starting sector offset
mmls disk_image.raw

# 2. List all files (including deleted files demarcated with '*')) at sector offset 2048
fls -r -o 2048 disk_image.raw

# 3. Recover deleted secret file at inode 14205
icat -o 2048 disk_image.raw 14205 > recovered_secret.docx
```
