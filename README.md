# Arch Linux KDE Daily Driver – Secure & Stable Configuration

**Author:** [sabrinaderose](https://github.com/sabrinaderose)  
**Date:** June 15, 2025  
**Repository:** https://github.com/sabrinaderose/arch-kde-plasma-configuration  
**Category:** Linux Desktop Setup | GRUB Troubleshooting | System Hardening  
**Certifications Aligned:** Indirect alignment with Linux+, Security+, and Cloud+ concepts

---

## 🎯 Objective

Following prior system instability with Hyprland + NVIDIA and Windows ISO damage, this project aimed to create a **daily-driver Arch Linux system** using **KDE Plasma**, prioritizing:

- Visual customization (ricing)
- Bootloader repair and dual-boot setup
- Integration of security auditing tools
- GitHub SSH authentication for development workflows

This was not just a desktop experiment — it was a full system rebuild and hardening initiative, focused on transforming a fresh Arch install into a production-grade work environment.

---

## 🛠️ System Environment

### Primary Workstation
- **CPU:** AMD Ryzen 7 5700G @ 3.80GHz  
- **GPU:** NVIDIA RTX 3060 (12GB VRAM)  
- **RAM:** 32GB DDR4  
- **Storage:** 2x 1TB SSDs  
- **Boot Type:** UEFI  
- **Networking:** Wi-Fi  

### Bootloader
- GRUB (with custom entry for Nobara Linux)

### OS & Kernel
- Arch Linux (rolling, June 2025)  
- Kernel 6.9.x.arch1-1  
- KDE Plasma Desktop (X11 fallback for NVIDIA stability)

---

## 🧰 Software Stack

- **Desktop & Tools:** `konsole`, `dolphin`, `firefox`, `librewolf`, `neovim`, `yay`  
- **Security:** `ufw`, `rkhunter`, `lynis`, `timeshift`  
- **Networking:** `networkmanager`, `resolvectl`  
- **Version Control:** SSH key generation and GitHub integration

---

## 🚧 Setup Goals & Risks

### Project Goals
- Stable KDE Plasma experience with NVIDIA support  
- Secure bootloader with multi-boot capability (Arch + Nobara)  
- Hardened system with built-in auditing and backup tools  
- Personal GitHub connected via SSH for development usage  

### Risks & Constraints
- GRUB failing to detect Nobara Linux  
- KDE and NVIDIA incompatibilities with Wayland (used X11 fallback)  
- Network resolution issues triggered by Spicetify patching

---

## ⚙️ Configuration & Execution

### 🧱 Disk & Package Setup
- Partitioned SSD into `/boot`, `/`, and `/home`  
- Installed base system + KDE packages via `pacman`  
- Enabled system services (firewall, display manager, etc.)

### 🔐 Security & Networking
- Enabled `ufw` and ran full system audits using `rkhunter` and `lynis`  
- Fixed broken DNS via `resolvectl` after Spotify theming patch  
- Created SSH keypair and added public key to GitHub account

### 🧪 Testing & Validation
- GRUB boot entries confirmed (including manual Nobara fallback)  
- Plasma desktop ran stable with NVIDIA under X11  
- `ssh -T git@github.com` test successful  
- Full audit logs confirmed minimal security risks post-install

---

## 🧠 Lessons Learned

- Multi-boot environments often require manual GRUB entry injection  
- KDE with X11 is more stable than Wayland with NVIDIA (at this time)  
- Network stack can be corrupted by third-party patches (e.g., Spicetify)  
- Visual customization should be decoupled from core system utilities  
- Always validate chroot paths and backup configs for recovery

---

## 📂 Important Logs & Artifacts

| File/Command             | Purpose                                  |
|--------------------------|-------------------------------------------|
| `/etc/default/grub`      | Bootloader customization                 |
| `resolvectl`             | DNS reset after patch failure            |
| `~/.ssh/id_ed25519.pub`  | GitHub SSH key                           |
| `ufw status`, `rkhunter` | Security validation outputs              |

---

## 🧾 STAR Format Summary (For Interviews)

**Situation:** Rebuilt Arch Linux after prior system corruption and Hyprland/NVIDIA failures  
**Task:** Create a secure, dual-boot-capable, and visually refined Linux environment for daily use  
**Action:** Configured KDE, resolved DNS and GRUB issues, implemented system auditing tools, and integrated GitHub with SSH  
**Result:** Functional, hardened Arch Linux desktop now used as a primary OS for both development and personal use

---

## ✅ Outcome

- **Status:** ✔️ Success  
- **GUI:** KDE Plasma (X11)  
- **Bootloader:** GRUB with working multi-boot  
- **Networking:** DNS manually restored post-conflict  
- **Security:** Hardened with firewall and audit tooling  
- **Version Control:** GitHub authenticated over SSH

---

## 📚 References

- Arch Wiki – KDE, GRUB, and systemd articles  
- GitHub Docs – SSH key setup for development  
- rkhunter + lynis documentation  
- YouTube tutorials on KDE theming and ricing  

---

## 🧩 Final Note

This wasn’t just a setup — it was a **hands-on recovery and configuration project** that bridged troubleshooting, desktop customization, and system security. For any entry-level Linux or sysadmin role, this represents production-relevant experience beyond basic coursework.
