# 🖥️ Day 19 - Cockpit and Webmin

## Objective
To learn how to set up Cockpit and Webmin — web-based Linux server management tools that allow administration via a browser.

---

## What is Cockpit?
**Cockpit** is a web-based management interface for Linux servers.  
Manage the server from a browser instead of only the command line.

### Why is it Useful?
- Easy for beginners
- Good for quick monitoring
- No need to remember many commands
- Works in real time

### What Can You Do with Cockpit?
- View system health (CPU, RAM, storage)
- Manage users
- Manage services
- View logs
- Configure networking and firewall
- Manage virtual machines (KVM)
- Update the system
- Check running processes
- File browser

**Access:** `https://server-ip:9090`

---

## Cockpit Setup

### Step 1 — Install Cockpit
```bash
sudo dnf install -y cockpit
```

### Step 2 — Start and Enable Service
```bash
sudo systemctl start cockpit
sudo systemctl enable cockpit
```

### Step 3 — Open Firewall Port
```bash
sudo firewall-cmd --permanent --add-service=cockpit
sudo firewall-cmd --reload
```

### Step 4 — Access Cockpit via Browser
```
https://<your-server-ip>:9090
```
Login using your RHEL system username and password.

### Cockpit Workflow Summary
1. Install Cockpit
2. Start service
3. Enable service
4. Configure firewall
5. Access via browser (Port 9090)

---

## What is Webmin?
**Webmin** is a web-based Linux system administration tool.  
Manage users, services, packages, and firewall via browser.  
**Default Port:** 10000

### Why Use Webmin?
- Web-based server management
- Manage users & groups
- Manage services (Apache, DNS, Samba)
- Package management
- Firewall configuration
- Beginner-friendly administration

---

## Webmin Setup

### Step 1 — Install Dependencies
```bash
dnf install wget perl -y
```

### Step 2 — Download Webmin
```bash
wget https://www.webmin.com/download/rpm/webmin-current.rpm
```

### Step 3 — Install Webmin
```bash
dnf install webmin-current.rpm -y
```

### Step 4 — Start and Enable Service
```bash
systemctl start webmin
systemctl enable webmin
systemctl status webmin
```

### Step 5 — Configure Firewall
```bash
firewall-cmd --permanent --add-port=10000/tcp
firewall-cmd --reload
```

### Step 6 — Verify Port
```bash
ss -tulnp | grep 10000
```

### Step 7 — Access Webmin via Browser
```
https://192.168.137.128:10000
```
Login using your Linux username and password.

### Step 8 — SELinux Check (If Needed)
```bash
getenforce
setenforce 0    # Temporary test only
```

---

## Cockpit vs Webmin

| Feature | Cockpit | Webmin |
|---------|---------|--------|
| Default Port | 9090 | 10000 |
| Protocol | HTTPS | HTTPS |
| Maintained by | Red Hat | Community |
| Built into RHEL | ✅ Yes | ❌ No (external) |
| Best For | Quick monitoring | Deep administration |
