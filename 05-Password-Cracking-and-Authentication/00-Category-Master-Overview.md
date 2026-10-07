# 🔑 Category 05: Password Cracking & Authentication — Master Overview

> [!INFO] 📌 **Domain Definition & Scope**
> Password Cracking and Authentication testing encompasses recovering plain-text credentials from stored cryptographic hashes (GPU/CPU offline cracking), testing online network authentication services for weak passwords (multi-threaded login brute-forcing), and hijacking unauthenticated local network broadcasts (LLMNR/NBT-NS poisoning).

---

## 🏆 Tool Selection & Efficiency Matrix

| Assessment Task | Primary Tool (#1 Choice) | Secondary / Advanced Alternatives | Acceleration Engine |
| :--- | :--- | :--- | :--- |
| **GPU-Accelerated Offline Hash Cracking** | **Hashcat** | John the Ripper, Ophcrack | OpenCL / CUDA GPU Cores |
| **CPU Hash & File Archive Password Recovery**| **John the Ripper** | Hashcat | Multi-threaded CPU (`*2john`) |
| **Online Multi-Protocol Service Brute-Force**| **Hydra** | Medusa, Ncrack, Crowbar | Network Sockets |
| **Local Network LLMNR/NBT-NS Poisoning** | **Responder** | Inveigh, Metasploit | Raw Layer-2/3 Network Packets |
| **RDP & SSH Private Key Password Testing** | **Crowbar** | Hydra, Ncrack | RDP NLA & OpenSSH |

---

## 📂 Comprehensive Tool Master Guides in Category 05

1. 🛠️ [01-Hashcat-GPU-Cracking-Mastery.md](./01-Hashcat-GPU-Cracking-Mastery.md)
   - Hashcat hash mode reference matrix (`-m 0`, `-m 1000`, `-m 1800`, `-m 13100`, `-m 22000`), attack modes (`-a 0`, `-a 3`, `-a 6`), custom rules (`best64.rule`), and mask generation syntax.
2. 🛠️ [02-John-the-Ripper-Complete-Guide.md](./02-John-the-Ripper-Complete-Guide.md)
   - John the Ripper formats (`--format`), rules engines (`--rules`), and helper script extractions (`ssh2john`, `zip2john`, `rar2john`, `pdf2john`, `keepass2john`, `office2john`, `unshadow`).
3. 🛠️ [03-Hydra-and-Medusa-Online-Bruteforce.md](./03-Hydra-and-Medusa-Online-Bruteforce.md)
   - Hydra parallel network login attacks against SSH, FTP, RDP, SMB, and HTTP POST forms, with Medusa and Ncrack comparisons.
4. 🛠️ [04-Responder-and-LLMNR-Poisoning.md](./04-Responder-and-LLMNR-Poisoning.md)
   - Responder LLMNR/NBT-NS/mDNS poisoning, Rogue WPAD server configuration, NetNTLMv2 hash capturing, and `ntlmrelayx.py` SMB relaying.
5. 🛠️ [05-Crowbar-and-RDP-Bruteforce.md](./05-Crowbar-and-RDP-Bruteforce.md)
   - Crowbar specialized RDP (NLA authentication), SSH private key passphrase, and VNC brute-force commands.
