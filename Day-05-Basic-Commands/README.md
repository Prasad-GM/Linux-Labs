# ⌨️ Day 05 - Basic Linux Commands

## Objective
To learn and practice essential Linux commands for navigation, file management, and system information.

---

## System Commands

| Task | Command |
|------|---------|
| Lock screen | `Super Key + L` |
| Log out | `gnome-session-quit` |
| Reboot | `reboot` |
| Shutdown | `poweroff` |

---

## Hostname Commands

```bash
hostname                          # View current hostname
hostname <new-name>               # Change hostname temporarily
hostnamectl set-hostname <name>   # Change hostname permanently
```

---

## Date and Time Commands

```bash
date                                      # View current date and time
timedatectl                               # Detailed date/time info
timedatectl set-time '10:15:25'           # Change time
timedatectl set-time '2025-05-25 10:15:25' # Set date and time
timedatectl list-timezones                # List all timezones
timedatectl set-timezone Asia/Kolkata     # Change timezone
cal                                        # View calendar
```

---

## Navigation Commands

```bash
whoami        # Displays current logged-in user
pwd           # Print working directory
cd /var/tmp   # Navigate to absolute path
cd ..         # Go back one level
cd ../..      # Go back two levels
cd            # Go to home directory
ls            # List files (blue = dir, white = file)
ls -l         # Long list with attributes
ls -a         # All files including hidden
ls -al        # All files with long list
```

---

## Absolute vs Relative Path

| | Absolute Path | Relative Path |
|--|--------------|---------------|
| **Definition** | Full path from root `/` | Path from current directory |
| **Starts with** | Always `/` | Does not start with `/` |
| **Example** | `/home/user/file.txt` | `documents/file.txt` |

---

## File Management Commands

```bash
# Create files
touch filename              # Create empty file
touch file1 file2 file3     # Create multiple files
touch filename{1..10}       # Create 10 files (file1 to file10)

# Read/Write files
cat filename                # Read file content
cat > file1                 # Create/overwrite file
cat >> file1                # Append to file
vim filename                # Open file in VIM editor

# Copy files
cp source destination       # Copy a file
cp file1 file2 /dir/        # Copy multiple files to directory

# Move/Rename files
mv file1 file2              # Rename file1 to file2
mv file1 /destination/      # Move file to another location
mv dir1 dir2                # Rename dir1 to dir2 (if dir2 doesn't exist)

# Delete files
rm filename                 # Remove a file
rm -r directory             # Remove directory
rm -rvf directory           # Force remove directory
rm -rvf dir*                # Remove all dirs starting with "dir"
rmdir directory             # Remove empty directory
```
