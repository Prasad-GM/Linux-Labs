# 🛡️ Day 12 - Special Permissions and ACL

## Objective
To understand SUID, SGID, Sticky Bit, and Access Control Lists (ACL) for advanced permission management in Linux.

---

## Special Permissions

Apart from normal `r`, `w`, `x` permissions, Linux has three special permissions:

| Permission | Numeric Value | Applied To |
|-----------|--------------|-----------|
| SUID | 4 | Files |
| SGID | 2 | Files & Directories |
| Sticky Bit | 1 | Directories |

---

## SUID (Set User ID)

### Definition
When SUID is set on an executable file, **any user running it gets the file owner's permissions** — not their own.

### Real-World Example
The `passwd` command:
- Normal users can't write to `/etc/shadow` (owned by root)
- But `passwd` has SUID set → it runs with root privileges → can update the password

### Symbol
```
-rwsr-xr-x   → The 's' in user execute position = SUID
```

### Commands
```bash
chmod u+s file         # Set SUID (symbolic)
chmod 4755 file        # Set SUID (numeric)
ls -l file             # Check for 's' in owner execute position
```

---

## SGID (Set Group ID)

### Definition
- On **files** → file executes with the group's permissions, not user's group
- On **directories** → new files created inside inherit the **directory's group**, not the user's primary group

### Use Case
Shared project directories where all team files should belong to the same group.

### Symbol
```
drwxrwsr-x   → The 's' in group execute position = SGID
```

### Commands
```bash
chmod g+s directory    # Set SGID (symbolic)
chmod 2755 directory   # Set SGID (numeric)
```

---

## Sticky Bit

### Definition
Applied to directories — ensures that **only the file owner can delete or rename their files**, even if others have write permissions on the directory.

### Use Case
`/tmp` directory — everyone can write, but can only delete their own files.

### Symbol
```
drwxrwxrwt   → The 't' at the end = Sticky Bit
```

### Commands
```bash
chmod +t /shared            # Set sticky bit (symbolic)
chmod 1777 /shared          # Set sticky bit (numeric)
ls -ld /shared              # Verify — look for 't' at end
```

---

## Special Permission Numeric Summary

| Number | Meaning |
|--------|---------|
| 1 | Sticky Bit |
| 2 | SGID |
| 3 | SGID + Sticky |
| 4 | SUID |
| 5 | SUID + Sticky |
| 6 | SUID + SGID |
| 7 | SUID + SGID + Sticky |

---

## Access Control List (ACL)

ACL provides **additional, flexible permissions** beyond the standard user/group/other model.  
It lets you give specific permissions to any user or group on any file/directory.

### ACL Commands

```bash
# Add permission for a specific user
setfacl -m u:username:rwx /path/to/file

# Add permission for a specific group
setfacl -m g:groupname:rwx /path/to/file

# Set default ACL (files inside directory inherit it)
setfacl -dm u:john:rwx /project/data

# Remove ACL for a specific user
setfacl -x u:user /path/to/file

# Remove all ACL entries
setfacl -b /path/to/file

# View ACL entries
getfacl /path/to/file
```
