# 🔍 Day 07 - GREP and FIND Commands

## Objective
To learn how to search for text inside files using GREP and search for files/directories using FIND.

---

## Quick Summary

| Command | Purpose |
|---------|---------|
| `grep` | Search **text inside** a file |
| `find` | Search **files or directories** by name/type |
| `grep -r` | Search text inside all files in a directory |

---

## GREP Command

**GREP** = Global Regular Expression Print  
Used to search for a pattern inside a file and display matching lines.

### Syntax
```bash
grep [options] pattern filename
```

### Examples

```bash
grep root /etc/passwd              # Search 'root' in /etc/passwd
grep prasad testfile.txt           # Search 'prasad' in testfile.txt
grep -i TEST testfile.txt          # Case-insensitive search
grep -n test testfile.txt          # Show line numbers with matches
grep -r prasad testdir/            # Search inside all files in directory
grep -c prasad testfile.txt        # Count number of matching lines
grep prasad file1.txt file2.txt    # Search in multiple files
grep -r root /etc/                 # Search 'root' inside all /etc/ files
```

### GREP Options

| Option | Description |
|--------|-------------|
| `-i` | Case-insensitive search |
| `-n` | Show line numbers |
| `-r` | Recursive search in directory |
| `-c` | Count matching lines |

---

## FIND Command

**FIND** is used to search for files and directories by name, type, or location.

### Examples

```bash
find / -name student1                  # Find file/dir named 'student1' from root
find / -type d -name testdir           # Search only directories
find / -type f -name testfile          # Search only files
```

### FIND Options

| Option | Description |
|--------|-------------|
| `-name` | Search by file/directory name |
| `-type d` | Search only directories |
| `-type f` | Search only files |

---

## GREP vs FIND

| | GREP | FIND |
|--|------|------|
| **Searches** | Text content inside files | Files/directories by name |
| **Example** | `grep root /etc/passwd` | `find / -name passwd` |
| **Recursive** | `grep -r` | Built-in (searches from path) |
