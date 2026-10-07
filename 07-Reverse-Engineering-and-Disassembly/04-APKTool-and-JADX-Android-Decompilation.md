# 🛠️ Tool Master Guide: APKTool & JADX Android Decompilation Suite

> [!INFO] 📋 **Root Metadata**
> - **Category**: Android APK Reverse Engineering & Smali Decompilation Suite
> - **Tools Covered**: `apktool`, `jadx`, `jadx-gui`
> - **Installations**: `sudo apt update && sudo apt install -y apktool jadx Uber-apk-signer`
> - **Binary Paths**: `/usr/bin/apktool`, `/usr/bin/jadx`, `/usr/bin/jadx-gui`
> - **Primary Objective**: Decompiles Android APK archives into Smali assembly code and readable Java source code, enabling binary patching, resource inspection, and dynamic debugging.

---

## 📋 1. Android Reverse Engineering Toolchain Matrix

| Utility Name | Primary Function | Command Syntax |
| :--- | :--- | :--- |
| **jadx-gui** | Java source code visual decompiler | `jadx-gui target.apk` |
| **apktool** | Smali bytecode decompiler & APK packager | `apktool d target.apk` |
| **uber-apk-signer**| Aligns and signs modified APK file | `uber-apk-signer --apks patched.apk` |

---

## 💻 2. Practical Operational Workflow

```bash
# Step 1: Inspect Java Source Code using JADX GUI
jadx-gui target_app.apk &

# Step 2: Decompile APK into Smali bytecode and raw resources via APKTool
apktool d target_app.apk -o output_dir/

# Step 3: Modify Smali code or AndroidManifest.xml inside output_dir/
# Step 4: Rebuild modified APK from output directory
apktool b output_dir/ -o patched_app.apk

# Step 5: Align and Sign patched APK with test key
uber-apk-signer --apks patched_app.apk
```
