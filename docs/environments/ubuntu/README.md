# 🟠 Ubuntu Environment

This directory contains documentation for **Ubuntu virtual machine environments** used in the homelab infrastructure.

Ubuntu is used as a general-purpose Linux platform for application deployment, Docker services, and development environments.

---

## 🛠️ Environment Overview

| Component        | Details                       |
| ---------------- | ----------------------------- |
| Operating System | Ubuntu Linux                  |
| Package Manager  | APT                           |
| Virtualization   | Virt-Manager (KVM/QEMU)       |
| Main Usage       | FTP, Samba & Application Services |

---

## 🎯 Learning Objectives

This environment is used to learn:

* Docker container deployment
* Linux administration
* Sharing Folder
* System monitoring
* Server automation

---

## 🔧 Common Commands

Update packages:

```bash
sudo apt update && sudo apt upgrade -y
```

Check running services:

```bash
systemctl --type=service
```

Check resources:

```bash
htop
```

Docker check:

```bash
docker ps
```

---

## 📚 Notes

Ubuntu is one of the primary operating systems used in this homelab for running modern infrastructure workloads.

