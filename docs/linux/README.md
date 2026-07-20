# Linux Administration Guide

This document summarizes the Linux administration practices used throughout this homelab infrastructure. The environment includes Debian, Ubuntu, Rocky Linux, CentOS, Docker containers, virtualization, and self-hosted services.

---

# Directory Structure

The following directory layout is used to keep the system organized.

```text
/
├── /etc                 System configuration
├── /var/log             System and application logs
├── /var/www             Web applications
├── /usr/local           Custom applications
├── /data                Persistent storage
├── /home                User home directories
└── /tmp                 Temporary files
```

---

# User Management

- Avoid using the root account for daily administration.
- Create dedicated users for services whenever possible.
- Use `sudo` for privileged operations.
- Apply the Principle of Least Privilege.

---

# File Permissions

Typical permissions used throughout the environment.

| Permission | Description |
|------------|-------------|
| 644 | Regular files |
| 755 | Directories and executable files |
| 600 | Sensitive configuration files |
| 700 | Private directories |

Ownership should always match the service that manages the files.

Example:

```bash
chown -R www-data:www-data /var/www/html
chmod -R 755 /var/www/html
```

---

# Storage Management

Persistent application data is stored on a dedicated data partition.

Example:

```text
/data
├── docker
├── nginx
├── backups
├── monitoring
└── projects
```

Benefits:

- Easier backups
- Cleaner system upgrades
- Simplified disaster recovery

---

# Service Management

Common systemd commands.

```bash
systemctl status nginx
systemctl restart nginx
systemctl enable nginx
systemctl disable nginx
journalctl -u nginx -f
```

---

# Log Management

Useful log locations.

| Service | Log Location |
|----------|--------------|
| System | /var/log/messages |
| Nginx | /var/log/nginx/ |
| Apache | /var/log/httpd/ |
| Docker | docker logs |
| SSH | journalctl -u sshd |

---

# Networking

Basic verification commands.

```bash
ip addr
ip route
ss -tulpn
ping
curl
```

Firewall example:

```bash
firewall-cmd --list-all
firewall-cmd --reload
```

---

# Security Practices

- Keep packages updated.
- Disable unused services.
- Use SSH key authentication when possible.
- Restrict firewall rules.
- Limit exposed ports.
- Regularly review system logs.
- Backup important data.

---

# Troubleshooting Workflow

1. Verify the service status.
2. Review logs.
3. Check configuration syntax.
4. Validate permissions.
5. Test network connectivity.
6. Restart the service only after identifying the issue.

---

# Backup Strategy

Critical data includes:

- Docker volumes
- Configuration files
- Databases
- SSL certificates
- Project files

Backups should be stored separately from the production environment.

---

# References

- Linux Documentation Project
- systemd Documentation
- Docker Documentation
- Rocky Linux Documentation
- Debian Documentation
- Ubuntu Documentation
