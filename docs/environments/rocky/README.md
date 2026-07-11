# 🔴 Rocky Linux Environment

This directory contains documentation for **Rocky Linux virtual machines** used in the homelab infrastructure.

Rocky Linux is used as an enterprise Linux replacement for CentOS and is mainly deployed for server workloads requiring Red Hat Enterprise Linux compatibility.

---

## 🛠️ Environment Overview

| Component        | Details                    |
| ---------------- | -------------------------- |
| Operating System | Rocky Linux                |
| Package Manager  | DNF                        |
| Virtualization   | Virt-Manager (KVM/QEMU)    |
| Main Usage       | Enterprise Server Services |

---

## 🎯 Learning Objectives

This environment is used to practice:

* Enterprise Linux administration
* Zimbra mail server deployment
* Network service configuration
* Security management
* Docker
* System troubleshooting

---

## 🔧 Common Commands

Update system:

```bash
sudo dnf update -y
```

Install packages:

```bash
sudo dnf install package-name
```

Manage services:

```bash
systemctl status service-name
```

Check firewall:

```bash
firewall-cmd --list-all
```

---

## 📚 Notes

Rocky Linux environments are used for enterprise-style server implementations and production-like service testing.

