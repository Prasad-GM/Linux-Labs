# 🏗️ Day 03 - Linux Architecture and Distributions

## Objective
To understand the architecture of Linux, the role of the kernel, shells, terminals, and the major Linux distribution families.

---

## Linux Architecture

### The Kernel
The kernel is the **core component** of the OS sitting between hardware and software.

Responsibilities:
- **Process Management** — controls running programs
- **Memory Management** — allocates RAM
- **Device Management** — communicates with hardware
- **File System Management** — handles file storage
- **System Security & Permissions** — enforces access control

---

## Terminal vs Shell

| | Terminal | Shell |
|--|----------|-------|
| **What it is** | A program/emulator that opens a window for typing | The command interpreter running inside the terminal |
| **Role** | Provides the text input/output interface | Processes and runs your commands |
| **Examples** | GNOME Terminal, Konsole, xterm, TTY | Bash, Zsh, Fish, Sh |

---

## Major Linux Families

| Family | Package Type | Examples | Known For |
|--------|-------------|---------|-----------|
| Debian | .deb | Ubuntu, Kali, Mint | Stability, huge repos |
| Red Hat (RHEL) | .rpm | RHEL, Fedora, Rocky | Enterprise use |
| SUSE | .rpm | openSUSE, SLES | Enterprise + YaST |
| Arch | Pacman | Arch, Manjaro | Rolling release |
| Slackware | pkgtool | Slackware, Salix | Simplicity |
| Gentoo | Portage | Gentoo | Source-based |

---

## Desktop Environments

| DE | Best For |
|----|----------|
| **GNOME** | Modern, clean UI (default in RHEL) |
| **KDE Plasma** | Endless customization |
| **Xfce / Trinity** | Reviving old machines |
| **Pantheon** | macOS lovers |
| **LXQt** | Ultra-lightweight |

---

## Supported File Systems by Distro

| Distro | Default FS |
|--------|-----------|
| RHEL / Rocky | XFS ✅ |
| Ubuntu / Debian | ext4 ✅ |
| Fedora | Btrfs ✅ |
| openSUSE | Btrfs ✅ |
