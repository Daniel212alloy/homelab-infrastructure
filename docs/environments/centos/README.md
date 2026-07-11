# 🖥️ CentOS Environment

This directory contains documentation and notes related to **CentOS-based virtual machine environments** used in the homelab infrastructure.

CentOS systems are used for learning Linux server administration, service deployment, and enterprise-style server management.

---

## 🛠️ Environment Overview

| Component        | Details                                |
| ---------------- | -------------------------------------- |
| Operating System | CentOS                                 |
| Usage            | Server Environment                     |
| Virtualization   | Virt-Manager (KVM/QEMU)                |
| Purpose          | Linux Administration & Service Testing |

---

## 🎯 Learning Objectives

This environment is used to practice:

* Linux system administration
* Package management with YUM & DNF
* Service management using Systemd
* Network configuration
* Server troubleshooting
* Security configuration
* Ldap and central DB
---

## 🔧 Common Administration Commands

Update packages:

```bash
sudo yum update -y
```

Check system information:

```bash
cat /etc/os-release
```

Manage services:

```bash
systemctl status service-name
```

Check network:

```bash
ip address
```

---

## 📚 Notes

This environment is part of a personal homelab used for testing server configurations and infrastructure experiments.

