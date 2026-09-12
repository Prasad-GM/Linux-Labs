# 📂 Day 17 - Samba Configuration

## Objective
To learn how to configure Samba for file sharing between Linux and Windows systems.

---

## What is Samba?
Samba is a service that allows **file and printer sharing between Linux and Windows** using the **SMB protocol**.

### Why Use Samba?
- Share files from Linux to Windows
- Centralized file server
- User-based secure access
- Lab and office file sharing

---

## Step-by-Step Samba Setup

### Step 1 — Install Samba
```bash
dnf install samba samba-client samba-common -y
systemctl start smb
systemctl enable smb
```

### Step 2 — Create Linux User
```bash
useradd student1
passwd student1
```

### Step 3 — Add Samba User
```bash
smbpasswd -a student1    # Add user to Samba database
smbpasswd -e student1    # Enable the Samba user
```

### Step 4 — Create Shared Folder
```bash
mkdir /sharedfolder
chown -R student1:student1 /sharedfolder
chmod -R 770 /sharedfolder
```

### Step 5 — Edit Samba Configuration
```bash
vi /etc/samba/smb.conf
```

Add at the bottom:
```ini
[student1]
    path = /sharedfolder
    valid users = student1
    writable = yes
    browseable = yes
    guest ok = no
```

### Step 6 — Check Config and Restart
```bash
testparm               # Checks configuration for errors
systemctl restart smb
```

### Step 7 — Configure Firewall
```bash
firewall-cmd --permanent --add-service=samba
firewall-cmd --reload
```

### Step 8 — SELinux Fix (If Access Denied)
```bash
setenforce 0                             # Temporary test
chcon -t samba_share_t /sharedfolder     # Set proper SELinux context
```

---

## Access From Windows

1. Press `Win + R`
2. Type: `\\192.168.137.128\student1`
3. Login using Samba username and password

---

## Final Workflow Summary

1. Install Samba
2. Start service
3. Create Linux user
4. Add Samba password
5. Create shared folder
6. Edit smb.conf
7. Restart service
8. Test from Windows
