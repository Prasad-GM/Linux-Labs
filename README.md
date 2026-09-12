🐧 Linux Server Administration & Web Infrastructure
![Linux](https://img.shields.io/badge/OS-RHEL%20%2F%20Rocky%20Linux-red?style=for-the-badge&logo=redhat)
![VMware](https://img.shields.io/badge/Platform-VMware-blue?style=for-the-badge&logo=vmware)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)
![RHCSA](https://img.shields.io/badge/Cert-RHCSA%20EX200-red?style=for-the-badge&logo=redhat)
---
📌 Project Overview
This repository documents a hands-on Linux Server Administration project built and tested in a VMware virtualized environment. It covers real-world system administration tasks including user management, file permissions, web services, SSH configuration, Samba file sharing, and storage management — aligned with Red Hat Certified System Administrator (RHCSA EX200) objectives.
> Built as part of professional development at **Cordinal Tech Solution** as a System Administrator & Technical Trainer.
---
🎯 Project Objectives
Deploy and administer RHEL / Rocky Linux server environments
Configure and manage web, file sharing, and remote access services
Implement user/group management, file permissions, and ACL
Set up SSH key-based authentication for secure remote access
Manage storage, partitioning, and persistent mounts
Administer packages using DNF / YUM / RPM
Monitor and manage the server via Cockpit web dashboard
---
🛠️ Tools & Technologies
Category	Tools
Operating System	RHEL 9 / Rocky Linux 9
Virtualization	VMware Workstation
Web Server	Apache (httpd)
File Sharing	Samba (SMB Protocol)
Remote Access	OpenSSH
Package Manager	DNF / YUM / RPM
Monitoring	Cockpit, Webmin
Editor	VIM
Firewall	firewalld
Storage	XFS, fdisk, /etc/fstab
Access Control	chmod, chown, ACL (setfacl/getfacl)
---
📁 Project Structure
```
Linux-Labs/
├── Day-01-What-is-OS/
├── Day-02-Unix-and-Linux-History/
├── Day-03-Linux-Architecture-and-Distros/
├── Day-04-Linux-File-System/
├── Day-05-Basic-Commands/
├── Day-06-VIM-Editor/
├── Day-07-GREP-and-FIND/
├── Day-08-Hard-and-Soft-Links/
├── Day-09-Pipelines/
├── Day-10-Local-Users-and-Groups/
├── Day-11-File-Permissions/
├── Day-12-Special-Permissions-and-ACL/
├── Day-13-Storage-and-Mounting/
├── Day-14-Networking/
├── Day-15-Package-Management/
├── Day-16-SSH-Configuration/
├── Day-17-Samba-Configuration/
├── Day-18-Apache-Web-Server/
└── Day-19-Cockpit-and-Webmin/
```
---
🔧 Key Implementations
👥 User & Group Management
Created and managed local users with custom UIDs, home directories, and shells
Configured primary and secondary groups
Implemented password aging policies via `/etc/shadow` and `chage`
Managed sudo privileges via `/etc/sudoers` and wheel group
🔐 File Permissions & ACL
Applied standard `rwx` permissions using symbolic and numeric methods
Configured SUID, SGID, and Sticky Bit for shared directory security
Implemented Access Control Lists (ACL) using `setfacl` / `getfacl` for granular access control
Managed `umask` for default permission policies
🔒 SSH Configuration
Installed and configured OpenSSH server on Rocky Linux
Set up key-based authentication (passwordless login) using `ssh-keygen` and `ssh-copy-id`
Hardened SSH by disabling root login and restricting allowed users via `/etc/ssh/sshd_config`
Configured firewall rules to allow SSH traffic
🌍 Apache Web Server
Installed and configured Apache httpd on RHEL
Served custom web pages from `/var/www/html`
Configured firewall to allow HTTP traffic on port 80
Tested web access from browser via server IP
📂 Samba File Sharing
Configured Samba for cross-platform file sharing between Linux and Windows
Created dedicated Samba users and shared directories with proper ownership and permissions
Configured `/etc/samba/smb.conf` for secure, user-based access
Fixed SELinux context using `chcon` for Samba shares
Tested access from Windows via `\\server-ip\sharename`
💾 Storage & Mounting
Added and detected new virtual disks using `lsblk`
Created partitions using `fdisk`
Formatted with XFS filesystem using `mkfs.xfs`
Mounted volumes and configured persistent mounts via `/etc/fstab` using UUID
Verified with `df -h`, `findmnt`, and post-reboot checks
📦 Package Management
Managed software using RPM, YUM, and DNF
Installed, updated, and removed packages
Understood dependency resolution and repository management
🖥️ Server Monitoring
Set up Cockpit web dashboard for real-time server monitoring (port 9090)
Installed and configured Webmin for full server administration via browser (port 10000)
---
📊 Lab Environment
Component	Details
Host OS	Windows 11
Hypervisor	VMware Workstation
Guest OS	Rocky Linux 9 / RHEL 9
RAM allocated	2–4 GB per VM
Storage	40 GB base + 20 GB additional disk (storage lab)
Network	NAT / Bridged
---
📚 Topics Covered (Day-wise)
Day	Topic
Day 01	What is an Operating System?
Day 02	Unix and Linux History
Day 03	Linux Architecture and Distributions
Day 04	Linux File System and FHS
Day 05	Basic Linux Commands
Day 06	VIM Editor
Day 07	GREP and FIND Commands
Day 08	Hard Links and Soft Links
Day 09	Pipelines and Command Integration
Day 10	Local Users and Groups
Day 11	File Permissions
Day 12	Special Permissions and ACL
Day 13	Storage and Mounting Volumes
Day 14	Networking Commands
Day 15	Package Management (RPM, YUM, DNF)
Day 16	SSH Configuration
Day 17	Samba File Sharing
Day 18	Apache Web Server
Day 19	Cockpit and Webmin
---
🏆 Certification Target
Field	Details
Certification	Red Hat Certified System Administrator (RHCSA)
Exam Code	EX200
Passing Score	210 / 300
Portal	https://rol.redhat.com/rol/app/
---
👨‍💻 Author
Prasad G M
System Administrator & Technical Trainer
📧 prasad.12gm@gmail.com
🔗 LinkedIn
