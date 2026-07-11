# 🐧 Debian Environment

This directory contains documentation for **Debian-based virtual machines** used in the homelab infrastructure.

Debian is used as a stable Linux platform for running applications, services, and testing server deployments.

---

## 🛠️ Environment Overview

| Component        | Details                      |
| ---------------- | ---------------------------- |
| Operating System | Debian Linux                 |
| Package Manager  | APT                          |
| Virtualization   | Virt-Manager (KVM/QEMU)      |
| Purpose          | Server & Application Hosting |

---

## 🎯 Learning Objectives

This environment is used to practice:

* Linux server management
* Debian package administration
* Web service deployment
* Networking configuration
* Application hosting

---

## 🔧 Common Commands

Update system:

```bash
sudo apt update && sudo apt upgrade -y
```

Install packages:

```bash
sudo apt install package-name
```

Check services:

```bash
systemctl status service-name
```

Check IP address:

```bash
ip addr
```

---

## 📚 Notes

Debian environments are used for stable service deployment and testing within the homelab infrastructure.

