# 🛠️ Tool Master Guide: Binwalk Firmware Analysis Engine

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: Binwalk
> - **Category**: Firmware Analysis & File Carving Engine (#1 IoT Choice)
> - **License**: Open Source (MIT)
> - **Installation Command**: `sudo apt update && sudo apt install -y binwalk sasquatch`
> - **Binary Path**: `/usr/bin/binwalk`
> - **Primary Objective**: Scans binary files for magic byte signatures, extracts embedded file systems (SquashFS, CramFS, JFFS2), and carves compressed archive files.

---

## 💻 1. Practical Operational Workflow

```bash
# 1. Scan firmware file for magic byte signatures and offsets
binwalk router_firmware.bin

# 2. Automatically extract all embedded filesystems and archives
binwalk -e --mats-only router_firmware.bin

# 3. Recursively extract all nested filesystems inside output directory
binwalk -e -M router_firmware.bin
```
