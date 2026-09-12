# 🌐 Day 14 - Networking in Linux

## Objective
To learn basic network configuration, management, and firewall commands using nmcli and firewalld in Linux.

---

## Basic Network Commands

| Task | Command |
|------|---------|
| Show IP address info | `ip a` / `ip addr` |
| Show network interface status | `nmcli device status` |
| Bring interface up | `nmcli device connect eth0` |
| Bring interface down | `nmcli device disconnect eth0` |
| Set static IP | `nmcli con mod eth0 ipv4.addresses 192.168.1.100/24` |
| Set gateway | `nmcli con mod eth0 ipv4.gateway 192.168.1.1` |
| Set DNS | `nmcli con mod eth0 ipv4.dns 8.8.8.8` |
| Set DHCP | `nmcli con mod eth0 ipv4.method auto` |

---

## Network Status and Info

```bash
nmcli connection show                     # Show all connections
nmcli connection show eth0                # Show details of a connection
ping google.com                           # Ping a remote host
nmcli connection delete <ens160>          # Delete a connection profile

# Create a new DHCP connection profile
nmcli connection add type ethernet ifname <ens160> con-name <ens160> ipv4.method auto ipv6.method ignore
```

---

## Network Manager Service

```bash
systemctl restart NetworkManager    # Restart NetworkManager
systemctl status NetworkManager     # Check status
systemctl enable NetworkManager     # Enable at boot
```

---

## Create a DHCP Connection (Lab Steps)

```bash
# Step 1: Create correct DHCP connection using the REAL interface
sudo nmcli con add type ethernet ifname ens192 con-name ens192 ipv4.method auto autoconnect yes

# Step 2: Bring the connection up
sudo nmcli con up ens192
```

---

## Firewalld Commands

```bash
firewall-cmd --state                               # Check firewall status
firewall-cmd --list-all                            # View allowed ports/services
firewall-cmd --add-port=80/tcp --permanent         # Open port 80
firewall-cmd --add-service=http --permanent        # Allow HTTP service
firewall-cmd --permanent --add-service=ssh         # Allow SSH
firewall-cmd --reload                              # Apply firewall changes
```

---

## Useful Networking Tools

| Tool | Purpose |
|------|---------|
| `nmtui` | Text-based UI for network settings |
| `ss -tuln` | Show open/listening ports |
| `ethtool eth0` | Get interface hardware info |
| `tcpdump` | Capture and analyze network packets |
| `ss -tulnp \| grep ssh` | Confirm SSH is listening on port 22 |
