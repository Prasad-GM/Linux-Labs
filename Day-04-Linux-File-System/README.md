# 📁 Day 04 - Linux File System

## Objective
To understand what a file system is, how Linux organizes files using FHS, and the purpose of each key directory.

---

## What is a File System?
A file system is a method used by an OS to **store, organize, retrieve, and manage data** on storage devices (HDD, SSD, USB).

### Key Functions
- **Data Organization** — organizes data into files and directories
- **File Naming** — defines naming conventions and extensions
- **Storage Management** — manages read/write operations
- **Security** — provides access control and permissions
- **Data Integrity** — ensures data is written in a recoverable way

---

## Common File System Types

| Type | Common Use | Max File Size |
|------|-----------|---------------|
| FAT32 | USB drives, SD cards | 4 GB |
| exFAT | Flash drives, large files | Over 4 GB |
| NTFS | Windows default | 16 TB |
| ext4 | Linux (Ubuntu/Debian default) | 16 TB |
| XFS | Linux (RHEL/Rocky default) | 8 EB |

---

## Linux File System Hierarchy (FHS)

Linux uses a **hierarchical file system** starting from a single root `/`.  
Maintained by the **Linux Foundation**.

```
/
├── bin      → Essential command binaries
├── boot     → Bootloader, kernel files
├── dev      → Device files (hardware access)
├── etc      → System configuration files
├── home     → User home directories
├── lib      → Shared library files
├── media    → Removable media (USB, CD)
├── mnt      → Temporary mount point
├── opt      → Optional third-party tools
├── root     → Home directory of root user
├── sbin     → System administration binaries
├── tmp      → Temporary files (cleared on boot)
├── usr      → Executables, libraries, man files
└── var      → Variable data (logs, mail, web apps)
```

---

## Important Special Directories

| Directory | Purpose |
|-----------|---------|
| `/etc/shadow` | Stores hashed (encrypted) passwords — only root can read |
| `/etc/skel` | Template directory for new user home folders |
| `/var/spool/mail` | Local email storage for each user |

---

## Partitioning

| OS | Common Partitions |
|----|------------------|
| Windows | C: (OS), System Reserved (boot) |
| Linux | `/` (root), `/home` (user files), swap |

- **Automatic Partitioning** — OS installer sets up partitions
- **Manual Partitioning** — You create and manage partitions yourself
