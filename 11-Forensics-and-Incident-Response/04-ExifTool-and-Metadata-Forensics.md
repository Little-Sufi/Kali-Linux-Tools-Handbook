# 🛠️ Tool Master Guide: ExifTool Metadata Extraction

> [!INFO] 📋 **Root Metadata**
> - **Tool Name**: ExifTool
> - **Category**: File Metadata Read/Write Utility
> - **License**: Open Source (GPL-1.0+)
> - **Installation Command**: `sudo apt update && sudo apt install -y libimage-exiftool-perl`
> - **Binary Path**: `/usr/bin/exiftool`
> - **Primary Objective**: Reads, writes, and modifies metadata information across image files, documents, audio, and video formats (EXIF, XMP, IPTC).

---

## 💻 1. Practical Operational Workflow

```bash
# 1. Extract all metadata from image file including GPS coordinates
exiftool sample_image.jpg

# 2. Strip all metadata from image file for operational privacy
exiftool -all= sample_image.jpg
```
