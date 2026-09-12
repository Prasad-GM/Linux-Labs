# 🌍 Day 18 - Apache Web Server

## Objective
To learn how to install, configure, and serve web content using Apache (httpd) on a Linux server.

---

## What is Apache?
**Apache HTTP Server** is a popular open-source web server used to serve websites and web applications over the internet or local network.

### Why Use Apache on Linux?
1. **Host Websites** — Serve web pages (HTML, PHP, etc.)
2. **Serve Web Apps** — Run platforms like WordPress, Laravel
3. **Local Testing** — Test websites before deployment
4. **Flexible** — Add modules for security, redirects, SSL
5. **Enterprise Use** — Stable and supports high traffic

---

## Step-by-Step Apache Setup

### Step 1 — Install Apache
```bash
sudo dnf install -y httpd
```

### Step 2 — Start and Enable the Service
```bash
sudo systemctl enable httpd
sudo systemctl start httpd
sudo systemctl status httpd
```

### Step 3 — Allow HTTP Through Firewall
```bash
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --reload
```

### Step 4 — Create a Test Web Page
```bash
echo "Hello from Apache on RHEL!" | sudo tee /var/www/html/index.html
```

### Step 5 — Find Server IP
```bash
hostname -I
```

### Step 6 — Test From Browser
```
http://192.168.1.100
```

---

## Apache Key Concepts

| Concept | Details |
|---------|---------|
| **DocumentRoot** | Default web directory: `/var/www/html` |
| **Index File** | Apache serves `index.html` by default |
| **Config File** | `/etc/httpd/conf/httpd.conf` |
| **Default Port** | 80 (HTTP) |

### URL Mapping
```
http://server_IP/test.html  →  /var/www/html/test.html
```

---

## Useful Commands

```bash
sudo systemctl restart httpd        # Restart Apache
sudo systemctl stop httpd           # Stop Apache
sudo systemctl status httpd         # Check status
curl http://localhost               # Test locally via terminal
```
