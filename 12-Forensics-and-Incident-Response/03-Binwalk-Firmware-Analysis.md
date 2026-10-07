# 🛠️ Binwalk — Embedded Firmware Analysis & Extraction

> [!INFO] 📌 **Tool Metadata**
> - **Category**: Firmware Extraction & Binary Carving Tool (#1 Choice for IoT)
> - **License**: Open Source (MIT)
> - **Installation**: Pre-installed on Kali Linux (`binwalk`)
> - **Primary Objective**: Searching raw binary images for embedded file systems (SquashFS, CramFS), compressed archives, and executable code.

---

## 💻 Practical Command Workflows

```bash
# 1. Scan binary firmware file for signature headers
binwalk router_firmware.bin

# 2. Automatically extract embedded file systems and compressed files
binwalk -e --matryoshka router_firmware.bin
```
