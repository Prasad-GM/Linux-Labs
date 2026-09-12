# 🔒 Day 16 - SSH Configuration

## Objective
To learn how to install, configure, and use OpenSSH for secure remote access to Linux servers.

---

## What is SSH?
**SSH (Secure Shell)** is a cryptographic network protocol for securely connecting to remote systems.

### What SSH Provides
- Encrypted remote login (command-line access)
- Secure file transfer
- Tunneling and port forwarding
- Remote command execution

### SSH Replaces
Older insecure protocols: Telnet, Rsh, FTP

### SSH Uses
- Port **22** by default
- Public-key cryptography
- Strong encryption (AES, ChaCha20, RSA, Ed25519)

---

## Why Use OpenSSH?
- Remote server access from anywhere
- Encrypted communication — data stays private
- Run commands on remote server without being physically there
- Secure file transfer via SCP/SFTP
- Server administration without physical presence

---

## SSH Server vs Client

| | Server | Client |
|--|--------|--------|
| Package | `openssh-server` | Built into Linux/Mac terminal |
| Service | `sshd` | N/A |
| Examples | OpenSSH, Dropbear | PuTTY, MobaXterm, Terminal |

---

## SSH Server Setup

### Step 1 — Install SSH Server
```bash
sudo dnf install -y openssh-server
```

### Step 2 — Start and Enable SSH
```bash
sudo systemctl start sshd
sudo systemctl enable sshd
```

### Step 3 — Check SSH Status
```bash
sudo systemctl status sshd
```

### Step 4 — Allow SSH Through Firewall
```bash
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --reload
```

### Step 5 — Verify SSH is Listening
```bash
ss -tulnp | grep ssh    # Should show port 22
```

---

## Connect to Server

### From Linux/Mac Terminal
```bash
ssh username@server-ip
```

### From Windows Command Prompt
```bash
ssh student1@192.168.137.128
```

### From PuTTY (Windows GUI)
- Enter IP address
- Port: 22
- Click Open

---

## SSH Configuration File
```bash
sudo vim /etc/ssh/sshd_config
```

### Common Configuration Changes
```bash
Port 2222               # Change default SSH port
PermitRootLogin no      # Disable root login
AllowUsers user1 user2  # Allow only specific users
```

```bash
# After editing, restart SSH:
sudo systemctl restart sshd
```

---

## SSH Key-Based Authentication (Passwordless Login)

```bash
# Step 1: Generate SSH key pair (on CLIENT)
ssh-keygen

# Step 2: Copy public key to server
ssh-copy-id student1@192.168.137.128

# Step 3: Login without password
ssh student1@192.168.137.128
```

---

## Final Workflow Summary

1. Install OpenSSH
2. Start & Enable service
3. Configure firewall
4. Test SSH connection
5. Secure SSH configuration
