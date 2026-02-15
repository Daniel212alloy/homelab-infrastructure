# Linux Administration Notes

This document summarizes Linux administration principles
applied in this homelab infrastructure project.

---

## Linux Basics

- `/var/www` is used for web applications
- Application and data directories should be separated
- Services should run as non-root users for security

---

## Linux Permissions

- File permissions should not be modified directly inside application data directories
- Access control should be managed at application level when available
- Linux permissions act as a base security layer

---

## Storage Management

- Application data is stored under `/data`
- Data directory is mounted from a separate disk
- This approach simplifies backup and restore operations

---

## Networking Basics

- Services expose only required ports
- Internal services are not publicly accessible
- Network access is restricted by firewall rules

---

## Troubleshooting Approach

1. Check service status
2. Review application logs
3. Verify permissions
4. Validate configuration files
5. Restart service only after root cause analysis

---

## Security Principles

- Least privilege principle
- Services run with minimum required permissions
- Regular updates and patching are applied

---

