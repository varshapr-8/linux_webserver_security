# Linux Web Server Setup & Security Hardening
**Platform:** CentOS Linux | **Tools:** Apache, firewalld, SSH, useradd, chage

## Project Overview
Deployed and secured a complete Apache web server 
on CentOS Linux from scratch, implementing 
industry standard security practices.

## What I Built
A production-ready secured Linux web server with:
- Running Apache web server with virtual host
- Department based user access control
- Hardened SSH configuration
- Firewall rules for web traffic only
- Password expiry policies for all users

## Tasks Completed

### Task 1 — Apache Web Server
- Installed Apache HTTP Server using yum
- Configured virtual host with custom document root
- Enabled service to start automatically on reboot

### Task 2 — Website Hosting
- Created website directory /var/www/mywebsite
- Configured virtual host in /etc/httpd/conf.d/
- Verified website accessible via browser

### Task 3 — Firewall Configuration
- Configured firewalld to allow HTTP and HTTPS
- Blocked all unnecessary ports
- Verified rules with firewall-cmd --list-all

### Task 4 — User & Group Management
- Created 3 department groups
  (developers, designers, managers)
- Created users and assigned to groups
- Created department folders with proper
  ownership and permissions (chmod 770)
- Verified access control working correctly

### Task 5 — SSH Hardening
- Disabled root login (PermitRootLogin no)
- Limited auth attempts (MaxAuthTries 3)
- Set login grace time (LoginGraceTime 60)
- Added warning banner for legal protection

### Task 6 — Password Policy
- Set 90 day password expiry (chage -M 90)
- Forced password change on first login
- Set 14 day warning before expiry
- Configured global policy in /etc/login.defs

## Commands Reference

### Apache
\```bash
yum install httpd -y
systemctl start httpd
systemctl enable httpd
systemctl status httpd
\```

### Firewall
\```bash
firewall-cmd --permanent --add-service=http
firewall-cmd --permanent --add-service=https
firewall-cmd --reload
firewall-cmd --list-all
\```

### Users and Groups
\```bash
groupadd developers
useradd -m -G developers john
chown root:developers /shared/developers
chmod 770 /shared/developers
\```

### SSH Hardening
\```bash
# /etc/ssh/sshd_config changes
PermitRootLogin no
MaxAuthTries 3
LoginGraceTime 60
Banner /etc/ssh/banner.txt
\```

### Password Policy
\```bash
chage -M 90 username
chage -d 0 username
chage -W 14 username
\```

## Security Improvements

| Setting | Before | After |
|---|---|---|
| Root SSH login | Allowed | Blocked |
| Auth attempts | 6 tries | 3 tries |
| Login time | 2 minutes | 60 seconds |
| Password expiry | Never | 90 days |
| Firewall | Open | HTTP/HTTPS only |

## Screenshots
(Add your screenshots here)

## Tech Stack
- OS: CentOS Linux
- Web Server: Apache HTTP Server
- Firewall: firewalld
- Security: SSH hardening, chage
- Access Control: useradd, chmod, chown

## Author
Varsha P R
- LinkedIn: linkedin.com/in/varsha-p-r-843980360
- GitHub: github.com/varshapr-8
- Email: varshapbn8@gmail.com
