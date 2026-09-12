# 📦 Day 15 - Package Management

## Objective
To understand Linux package management — what packages, repositories, dependencies, and metadata are, and how to use RPM, YUM, and DNF to manage software.

---

## Key Concepts

### What is a Package?
A bundle containing:
- The actual software
- Configuration files
- Metadata
- Dependency information
- Install/uninstall scripts

### Linux Package Formats
| Format | Used By |
|--------|---------|
| `.deb` | Debian, Ubuntu |
| `.rpm` | Fedora, Rocky, RHEL |
| `.pkg.tar.zst` | Arch |

### What is a Repository?
A central server where packages are stored and distributed.
- Contains packages, metadata, and update files
- Cryptographically signed for security
- Examples: Rocky Linux BaseOS, AppStream, Flathub

### What are Dependencies?
Software components required by an application to work.  
Example: VLC needs audio libraries, video codecs, and GUI libraries.  
The package manager installs these **automatically**.

### What is Metadata?
Data *about* the package — not the software itself.  
Includes: name, version, dependencies, description, checksums, architecture.

---

## Package Managers Comparison

| Tool | Who is it? | Handles Dependencies? | Used In |
|------|-----------|----------------------|---------|
| RPM | Manual tool | ❌ No | All Red Hat systems |
| YUM | Old helper | ✅ Yes | RHEL 6/7 |
| DNF | New helper | ✅ Yes | RHEL 8/9, Fedora |

> In RHEL 8+, `yum` is actually an alias for `dnf`

---

## Native Package Managers

| Distro | Package Manager | Command |
|--------|----------------|---------|
| Ubuntu / Debian | APT | `apt install` |
| Fedora / RHEL / Rocky | DNF | `dnf install` |
| CentOS (older) | YUM | `yum install` |
| Arch Linux | Pacman | `pacman -S` |
| openSUSE | Zypper | `zypper install` |

---

## 1️⃣ RPM Commands (Low-Level)

```bash
sudo rpm -ivh package.rpm    # Install
sudo rpm -e package-name     # Remove
sudo rpm -qa                 # List all installed packages
```

---

## 2️⃣ YUM Commands (RHEL 6/7)

```bash
sudo yum install <package>
sudo yum update <package>
sudo yum remove <package>
```

---

## 3️⃣ DNF Commands (RHEL 8/9) ⭐

```bash
sudo dnf install <package>
sudo dnf update <package>
sudo dnf remove <package>
sudo dnf update                        # Update all packages
sudo dnf install epel-release          # Install extra packages repo
```

---

## Practical Examples

### Red Hat Family
```bash
sudo dnf install htop fastfetch vlc
sudo dnf remove htop fastfetch vlc
sudo dnf update htop fastfetch vlc
```

### Debian Family
```bash
sudo apt install htop fastfetch vlc
sudo apt remove htop fastfetch vlc
sudo apt update
```

---

## Universal App Stores (Cross-Distro)

| Store | Description |
|-------|-------------|
| **Flatpak + Flathub** | Most popular universal Linux app store |
| **Snap Store** | Created by Canonical (Ubuntu) |
| **AppImageHub** | Portable apps, no install needed |
