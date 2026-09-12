# 🔗 Day 08 - Hard Links and Soft Links

## Objective
To understand the difference between hard links and soft links (symbolic links) in Linux, and how to create and verify them.

---

## What is an Inode?
An **inode** stores vital information about a file:
- File type (regular, directory, symlink)
- Permissions (read, write, execute)
- Ownership (UID and GID)
- File size in bytes
- Timestamps (access, modify, change)
- Link count (number of hard links)
- Data block pointers (where actual data is stored)

---

## Hard Link

### Definition
A hard link is **another name (directory entry) for the same inode**.  
Both the original file and the hard link share the **same inode number** and the same data.

### Command
```bash
ln original_file hardlink_file

# Example:
touch file1
ln file1 file1_hard
ls -li    # Check inode numbers
```

### Key Points
- Works only for **files** (not directories)
- Cannot cross filesystems
- Shares the **same inode number**
- If original file is deleted, the hard link **still works**

---

## Soft Link (Symbolic Link)

### Definition
A soft link is like a **shortcut** that points to the original file path.  
It has a **different inode number**.

### Command
```bash
ln -s original_file softlink_file

# Example:
touch file2
ln -s file2 file2_soft
ls -l     # Check the link
```

### Key Points
- Can link **files or directories**
- Can cross filesystems
- Has a **different inode number**
- If original file is deleted, soft link becomes **broken**

---

## Hard Link vs Soft Link

| Feature | Hard Link | Soft Link |
|---------|-----------|-----------|
| Inode | Same as original | Different inode |
| Cross filesystem | ❌ No | ✅ Yes |
| Link directories | ❌ No | ✅ Yes |
| If original deleted | ✅ Still works | ❌ Becomes broken |
| Command | `ln file link` | `ln -s file link` |

### Simple Explanation
- **Hard link** = Two names for the same file data
- **Soft link** = A shortcut pointing to another file
