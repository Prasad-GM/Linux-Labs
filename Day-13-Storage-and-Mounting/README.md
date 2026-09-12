# 💾 Day 13 - Storage and Mounting a New Volume

## Objective
To learn how to add a new virtual disk in VMware, partition it, format it with XFS, mount it, and make it persistent using `/etc/fstab`.

---

## Important Linux Storage Device Names

| Name | Meaning | Example | Represents |
|------|---------|---------|-----------|
| `nvme` | NVMe SSD | `/dev/nvme0n1` | NVMe SSD |
| `sd` | SCSI disk | `/dev/sda` | HDD/SSD/SATA |
| `sr` | CD-ROM | `/dev/sr0` | DVD drive |
| `mmcblk` | MMC block | `/dev/mmcblk0` | SD card |
| `vd` | Virtio disk | `/dev/vda` | KVM/QEMU virtual disk |

---

## 7-Step Formula (Memorize This!)

```
1. lsblk          → Find the disk
2. fdisk          → Partition it
3. mkfs.xfs       → Format it
4. mkdir          → Create mount point
5. mount          → Mount it
6. df -h/findmnt  → Verify
7. /etc/fstab     → Make it permanent
```

---

## Step-by-Step Lab

### STEP 1 — Add Disk in VMware
`VM → Settings → Add → Hard Disk → SCSI → New virtual disk → 20 GB → Finish`

### STEP 2 — Become Root
```bash
sudo -i
```

### STEP 3 — Find the New Disk
```bash
lsblk
# Look for new disk (e.g., /dev/sdb) by size
# Do NOT assume the name — always check lsblk output
```

### STEP 4 — Check Filesystems
```bash
lsblk -f
# New disk should show blank FSTYPE (no filesystem yet)
```

### STEP 5 — Create a Partition
```bash
fdisk /dev/sdb
# Inside fdisk:
# n → new partition
# p → primary
# Enter → default partition number
# Enter → default first sector
# Enter → default last sector (uses full disk)
# w → write and exit
```

### STEP 6 — Verify Partition
```bash
lsblk
# You should now see /dev/sdb1 under /dev/sdb
```

### STEP 7 — Create XFS Filesystem
```bash
mkfs.xfs /dev/sdb1
# WARNING: This formats the partition — destroys existing data
```

### STEP 8 — Verify Filesystem
```bash
lsblk -f
# Confirm FSTYPE = xfs for /dev/sdb1
```

### STEP 9 — Create Mount Point
```bash
mkdir /data
```

### STEP 10 — Mount the Volume
```bash
mount /dev/sdb1 /data
```

### STEP 11 — Verify Mount
```bash
df -h
findmnt /data
```

### STEP 12 — Test Storage
```bash
echo "Rocky Linux storage test" > /data/test.txt
cat /data/test.txt
```

### STEP 13 — Get UUID
```bash
lsblk -f
# Copy the UUID of /dev/sdb1 — use YOUR UUID, not an example
```

### STEP 14 — Edit /etc/fstab
```bash
vi /etc/fstab
# Add this line at the bottom:
UUID=YOUR-UUID /data xfs defaults 0 0
```

### Understanding /etc/fstab Fields
```
UUID=xxxx  /data  xfs  defaults  0  0
   1         2     3      4      5  6
```
| Field | Meaning |
|-------|---------|
| 1. UUID | Which device/filesystem to use |
| 2. /data | Where to mount it |
| 3. xfs | Filesystem type |
| 4. defaults | Standard mount options |
| 5. 0 | Dump backup field (0 = disable) |
| 6. 0 | Filesystem check order (0 = skip) |

### STEP 15 — Test fstab (IMPORTANT — Do NOT reboot yet!)
```bash
systemctl daemon-reload    # Reload systemd config
mount -a                   # Mount all filesystems in fstab
findmnt /data              # Verify — if no error, you're good!
```

### STEP 16 — Reboot and Verify
```bash
reboot
# After boot:
lsblk
df -h
findmnt /data
# If /data is mounted → Success! Persistent mount is working!
```

---

## Complete Lab — Commands Only

```bash
sudo -i
lsblk
lsblk -f
fdisk /dev/sdb          # n → p → Enter → Enter → Enter → w
lsblk
mkfs.xfs /dev/sdb1
lsblk -f
mkdir /data
mount /dev/sdb1 /data
df -h
findmnt /data
echo "Hello Rocky Linux" > /data/test.txt
cat /data/test.txt
lsblk -f                # Copy UUID
vi /etc/fstab           # Add: UUID=YOUR-UUID /data xfs defaults 0 0
systemctl daemon-reload
mount -a
findmnt /data
reboot
```
