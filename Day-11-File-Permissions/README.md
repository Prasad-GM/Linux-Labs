# 🔐 Day 11 - File Permissions

## Objective
To understand Linux file permissions, how to read them, and how to modify them using symbolic and numeric methods.

---

## What are Permissions?
Permissions control **who can access files and directories**.  
Every file has three categories:
- **User (u)** — the file owner
- **Group (g)** — the group owner
- **Others (o)** — everyone else

### Permission Types

| Symbol | Permission | On File | On Directory |
|--------|-----------|---------|-------------|
| `r` | Read | View file content | List directory contents |
| `w` | Write | Modify file | Create/delete files inside |
| `x` | Execute | Run as a command | Access directory contents |

---

## Reading Permissions

```
d  rwx  r-x  r-x  .  2  root  root  6  Feb 20 10:51  dir1
│   │    │    │                                          │
│   │    │    │                                          └─ Name
│   │    │    └─ Other permissions
│   │    └─ Group permissions
│   └─ Owner permissions
└─ Type (d=directory, -=file, l=link)
```

---

## Permission Precedence
1. If **UID matches** → Owner permissions apply
2. If **GID matches** → Group permissions apply
3. If **neither matches** → Other permissions apply

---

## Changing Permissions — chmod

### Symbolic Method

```bash
chmod u+x file       # Add execute for owner
chmod g-w file       # Remove write for group
chmod o=r file       # Set read-only for others
chmod a+x file       # Add execute for all (user, group, others)
chmod u+x,g-w file   # Multiple changes at once
```

Symbols:
- `u` = user, `g` = group, `o` = other, `a` = all
- `+` = add, `-` = remove, `=` = set exactly

### Numeric Method

| Value | Permission |
|-------|-----------|
| `0` | No permission |
| `1` | Execute |
| `2` | Write |
| `3` | Write + Execute |
| `4` | Read |
| `5` | Read + Execute |
| `6` | Read + Write |
| `7` | Full control (Read + Write + Execute) |

```bash
chmod 755 file    # rwxr-xr-x
chmod 644 file    # rw-r--r--
chmod 777 file    # rwxrwxrwx
chmod 700 file    # rwx------
```

---

## Changing Ownership

```bash
chown user file             # Change file owner
chown user:group file       # Change owner and group
chgrp groupname file        # Change only group ownership
chown -R user /directory    # Recursively change ownership
```

> ⚠️ Only **root** can change file ownership. Group ownership can be changed by root or the file's owner.

---

## umask — Default Permissions

`umask` defines what permissions are **removed** from newly created files/directories.

```
Effective Permissions = Default Permissions - umask
```

| umask | New File | New Directory |
|-------|---------|--------------|
| `022` | `644` (rw-r--r--) | `755` (rwxr-xr-x) |
| `027` | `640` (rw-r-----) | `750` (rwxr-x---) |
| `077` | `600` (rw-------) | `700` (rwx------) |

```bash
umask           # View current umask
umask 022       # Set umask temporarily
```
