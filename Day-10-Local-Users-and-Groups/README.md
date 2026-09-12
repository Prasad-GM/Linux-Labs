# 👥 Day 10 - Local Users and Groups

## Objective
To learn how to create, modify, and delete users and groups in Linux, and understand UID ranges and group types.

---

## Understanding Users

Users can be:
- **People** — accounts tied to real users
- **System accounts** — accounts used by applications/services

### UID Ranges

| UID Range | Purpose |
|-----------|---------|
| `0` | Reserved for **root** user |
| `1–200` | System users assigned statically by Red Hat |
| `201–999` | System users for processes (no files owned) |
| `1000+` | Regular users |

### User Info File
```bash
cat /etc/passwd    # Contains 7 fields per user
```
Fields: `username:password:UID:GID:comment:home_dir:shell`

---

## User Management Commands

### Create Users
```bash
useradd user1                        # Create new user
useradd -c "comment" user2           # Create user with comment
useradd -d /opt/user3 user3          # Custom home directory
useradd -M user4                     # Create user without home directory
useradd -N user5                     # Create user without primary group
useradd -s /sbin/nologin db_admin    # Create user that cannot login
useradd -u 2056 user7                # Create user with specific UID
```

### Modify Users
```bash
usermod -l new_name old_name         # Rename user
usermod -aG devs rahul               # Add user to secondary group
usermod -g newgroup rahul            # Change primary group
usermod -c "IT" rahul                # Change comment
usermod -e 2025-06-01 rahul          # Set account expiry date
usermod -e "" rahul                  # Remove account expiry
usermod -L username                  # Lock user account
usermod -U username                  # Unlock user account
```

### Delete Users
```bash
userdel user1                        # Delete user
cat /etc/passwd                      # Verify deletion
```

### View User Info
```bash
id                    # View current user info
id prasad             # View specific user info
chage -l rahul        # View password aging info
```

---

## Group Management

### Group Types
- **Primary Group** — Each user has one; files created by user belong to this group
- **Secondary Groups** — User can belong to multiple; provides access to shared resources

### Group Commands
```bash
groupadd HR                          # Create a group
groupadd -g 3000 account             # Create group with specific GID
groupmod -g 1050 account             # Change group GID
groupmod -n newgroup account         # Rename a group

usermod -aG HR,IT user3              # Add user to multiple groups
gpasswd -d user1 HR                  # Remove user from group
gpasswd -M user2,user3 mygroup       # Add multiple users to a group

cat /etc/group                       # View all groups
```

---

## Super User Access

### Root User
- Full access to the system
- Can override normal privileges
- Similar to Administrator in Windows

### Switch Users
```bash
su username           # Switch user (non-login shell)
su - username         # Switch user (login shell)
```

### Sudo
```bash
sudo command          # Run command as root
cat /etc/sudoers      # View sudo configuration
```
> In RHEL 9, all members of the **wheel** group can use sudo.

---

## Important Files

| File | Purpose |
|------|---------|
| `/etc/passwd` | User account info |
| `/etc/shadow` | Encrypted passwords |
| `/etc/group` | Group info |
| `/etc/sudoers` | Sudo permissions |
| `/etc/skel` | Default files for new users |
| `/etc/login.defs` | UID ranges and password policy |
