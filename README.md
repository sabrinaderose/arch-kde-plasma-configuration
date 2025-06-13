# 🖥️ Arch Linux KDE Daily Driver Setup

> [!NOTE]
> Final successful setup of Arch Linux with KDE Plasma as a stable, secure daily driver. Built after lessons from two prior failures.

---

## 📘 Summary

This README documents a successful rebuild of **Arch Linux with KDE Plasma**, following:
- A failed Hyprland/NVIDIA setup → [arch-linux-hyprland-nvidia-failure](https://github.com/sabrinaderose/arch-linux-hyprland-nvidia-failure)
- A full system wipe from Windows ISO imaging tools → [arch-linux-nuke-and-recovery](https://github.com/sabrinaderose/arch-linux-nuke-and-recovery)

---

## 🖥️ Disk Layout

```bash
lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda      8:0    0 931.5G  0 disk 
├─sda1   8:1    0   512M  0 part /boot
├─sda2   8:2    0    80G  0 part /
└─sda3   8:3    0   150G  0 part /home
sdb      8:16   0 931.5G  0 disk 
├─sdb1   8:17   0   600M  0 part  # Nobara EFI
├─sdb2   8:18   0   250G  0 part  # Nobara root
└─sdb3   8:19   0   200G  0 part  # Reserved
```

---

## 🧪 Core Packages Installed

```bash
pacman -Syu konsole dolphin firefox librewolf timeshift yay neovim ufw rkhunter lynis
```

---

## 🔐 Security Tools

```bash
# Firewall setup
sudo systemctl enable --now ufw
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw enable

# Rootkit Hunter
sudo rkhunter --update
sudo rkhunter --checkall

# Lynis audit
sudo lynis audit system
```

---

## 🧩 Bootloader: GRUB Configuration

```bash
# Regenerate GRUB menu
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

> [!WARNING]
> Nobara was not detected correctly by GRUB despite `os-prober`. Manual entry was required.

```bash
menuentry "Nobara Linux (Manual Entry)" {
    insmod part_gpt
    insmod btrfs
    search --no-floppy --fs-uuid --set=root dab12f8e-cf93-49e0-b396-9828b8c34865
    linux /boot/vmlinuz-6.15.2-200.nobara.fc42.x86_64 root=UUID=dab12f8e-cf93-49e0-b396-9828b8c34865 quiet splash
    initrd /boot/initramfs-6.15.2-200.nobara.fc42.x86_64.img
}
```

> Manual repair via chroot failed due to missing `/bin/bash` and critical binaries. Nobara was marked unstable and untouched.

---

## 📡 DNS Fix After Spotify Patching

```bash
# DNS broke after using spicetify tool
sudo resolvectl dns eth0 1.1.1.1
sudo resolvectl domain eth0 '~.'
```

---

## 🔑 SSH and GitHub Integration

```bash
ssh-keygen -t ed25519 -C "[censored]"
# Add public key to GitHub profile

ssh -T git@github.com
# Output should confirm: authenticated, but no shell access
```

---

## 🎨 Theming / Ricing Plans [WIP]

> [!TIP]
> Neo-Y2K aesthetic inspired by *Serial Experiments Lain*

- **Global Theme**: Neo-Y2K, Lain-inspired
- **SDDM**: Custom login theming in progress
- **Kvantum**: Full Qt theming engine
- **Wallpapers**: Pulled from Wallhaven (`exkqk8`)
- **Panel/Dock**: Custom Plasma panel; fallback floating dock
- **Sound**: Retro-tech audio aesthetic

---

## 📦 Known Issues

- ❗ KDE + NVIDIA has slight stuttering on Wayland; defaulting to X11
- ❌ Latte-dock fails to build:
```text
CMake Error at CMakeLists.txt:2 (cmake_minimum_required):
  Compatibility with CMake < 3.5 has been removed from CMake.
```

---

## 🧠 Lessons Learned

- Do not rely on experimental distros (e.g., Nobara Steam Edition) in multiboot configs
- Some scripts (like Spicetify) can break essential system configs (e.g., DNS)
- Always validate a chroot environment before attempting repair
- Recovery and rebuild are part of the story — not failure

---

## 🔗 Related Repositories

- [`arch-linux-hyprland-nvidia-failure`](https://github.com/sabrinaderose/arch-linux-hyprland-nvidia-failure)
- [`arch-linux-nuke-and-recovery`](https://github.com/sabrinaderose/arch-linux-nuke-and-recovery)

- [ ] Convert chat logs and terminal history into wiki-style GitHub pages
- [ ] Finalize Neo-Y2K ricing for showcase
- [ ] Integrate all repos into WGU resume and job applications
