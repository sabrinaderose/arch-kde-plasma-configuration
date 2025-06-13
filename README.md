# 🖥️ Arch Linux KDE Daily Driver Setup

> [!NOTE]
> This project documents the **final successful rebuild** of Arch Linux with KDE Plasma, used as a secure, daily driver after two failed attempts. It’s designed for real-world productivity, documentation, and portfolio development.

---

## 📘 Summary

This is a **stable, secure**, and practical Arch setup running **KDE Plasma (X11)** on an NVIDIA GPU. It's optimized for:

- GitHub project documentation  
- LPI Linux Essentials prep  
- Real-world, daily driver productivity  
- Custom theming (Neo-Y2K + Lain aesthetic) [WiP]

---

## 🛠️ System Configuration

### 💾 Disk Layout

```text
/dev/sda1: EFI (GRUB)
/dev/sda2: Arch Root (/)
/dev/sda3: /home
/dev/sdb: Nobara Linux (secondary SSD)
/dev/sdb1: Nobara EFI partition
```

---

### 🚀 Bootloader Setup

```bash
grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB
grub-mkconfig -o /boot/grub/grub.cfg
```

- ✅ Chose GRUB over rEFInd for stronger multi-boot detection
- 🔍 `os-prober` confirmed working with Nobara and Windows

---

## 📦 Core Packages Installed

```bash
pacman -S neovim dolphin konsole firefox librewolf timeshift rkhunter lynis ufw pipewire-pulse pavucontrol git ssh kvantum qt5ct sddm
```

### 🧰 AUR Helpers

```bash
pacman -S yay
yay -S topgrade
```

---

## 🔐 Security Hardening Tools

| Tool       | Purpose                   |
|------------|---------------------------|
| Timeshift  | Snapshot and rollback     |
| rkhunter   | Rootkit detection         |
| lynis      | Security auditing         |
| ufw        | Firewall configuration    |

---

## 🎨 Ricing Plans (Neo-Y2K / Lain Aesthetic)

> [!TIP]
> The goal is to create a fully themed cyber-aesthetic inspired by *Serial Experiments Lain* and early 2000s tech nostalgia. [WiP]

- **Wallpaper**: [`wallhaven.cc/w/exkqk8`](https://wallhaven.cc/w/exkqk8)
- **Kvantum**: Full Qt theming
- **Login**: Custom SDDM theme (planned)
- **WM**: KDE Plasma (X11); Wayland still unstable with NVIDIA
- **Fallback WM**: Exploring `i3` alongside KDE tools
- **System Sounds**: Retro techno style

---

## 🧠 Lessons Learned

- ✅ KDE Plasma is modular and compatible with NVIDIA — unlike Hyprland
- 🧱 Building from failure creates long-term confidence and control
- 📚 Documenting terminal history and configs is *not optional*

---

## 🧪 Future To-Dos

> [!WARNING]
> This setup is fully functional but still undergoing aesthetic finalization.

- [ ] Apply matching SDDM and GRUB themes
- [ ] Convert chat logs and terminal history into wiki-style GitHub pages
- [ ] Finalize Neo-Y2K ricing for showcase
- [ ] Integrate all repos into WGU resume and job applications
