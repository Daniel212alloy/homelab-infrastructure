# 🚀 Homelab Infrastructure

A comprehensive documentation of my personal IT infrastructure, focusing on server administration, networking, and self-hosted services. This repository serves as a technical log for configurations and real-world problem-solving.

## 🔧 Tech Stack

* 🐧 **Operating Systems**
  * Debian • Ubuntu • CentOS • Rocky Linux
* 💻 **Virtualization**
  * KVM (Virt-Manager) • VirtualBox
* 🌐 **Web Server & Development**
  * Apache HTTP Server • MariaDB • PHP (LAMP Stack) • Bash
* 🌍 **Networking & Security**
  * MikroTik • Port Forwarding • Firewall Configuration • NAT
* 📧 **Mail & Collaboration**
  * Zimbra Collaboration Suite • Roundcube Webmail
* 👥 **Directory Services**
  * OpenLDAP Server • Multi-OS LDAP Client Configuration
* 📂 **Self-Hosted Services**
  * Nextcloud • TrueNAS • Samba • FTP Server
* 🐳 **Containers & 📊 Monitoring**
  * Docker • Webhook Alert Monitoring • Grafana • Prometheus
* ☁️ **Cloud & Edge Services**
  * Cloudflare DNS Management • Cloudflare Tunnel (Web Server & Nextcloud) • Email DNS Configuration (SPF, DKIM, DMARC)


## 🎯 Current Homelab Status

Berikut adalah status *services* dan infrastruktur yang berjalan aktif di laboratorium mandiri (*homelab*) saat ini:

| Service | Status | Platform | Notes |
| :--- | :---: | :--- | :--- |
| **Zimbra Collaboration Suite** | ✅ Running | Rocky Linux VM | Enterprise Mail Server |
| **Roundcube Webmail** | ✅ Running | Docker | Connected to external Postfix |
| **Postfix SMTP Relay** | ✅ Running | CentOS 9 VM | Integrated with Brevo SMTP |
| **Brevo SMTP** | ✅ Active | Cloud Service | Outbound mail relay integration |
| **Nextcloud** | ✅ Running | Debian & CentOS | Published via Cloudflare Tunnel |
| **OpenLDAP** | ✅ Running | CentOS 7 VM | Centralized Identity & Authentication Management |
| **Grafana** | ✅ Running | Docker (Rocky) | Infrastructure Metrics Monitoring & Dashboard |
| **Prometheus** | ✅ Running | Docker (Rocky) | Time-series Metrics Collection |
| **WhatsApp Alert Bot** | ✅ Running | Docker (Rocky) | Real-time Webhook Monitoring & VM Alerts |
| **Cloudflare Tunnel** | ✅ Running | Debian VM | Secure public access without open inbound ports |
| **Database Server** | ✅ Running | CentOS 7 VM | Centralized DB for homelab services |

---

## 📂 Featured Projects & Experience

### 🌐 Networking Setup
- **IP Segmentation:** Implemented secure network segmentation using MikroTik RouterOS.
- **Subnet Isolation:** Separated server and client networks into distinct subnets to minimize internal attack surfaces.
- **NAT & Port Forwarding:** Configured Network Address Translation (NAT) and precise port forwarding rules for self-hosted applications.
- **Firewall Hardening:** Applied robust firewall rules for strict access control and traffic filtering.

### 📧 Mail Server Stack (Zimbra Collaboration)
Successfully deployed **Zimbra Collaboration Suite (ZCS 8.8.15)** on **Rocky Linux 8**. The primary focus of this project was to establish a highly reliable email delivery system despite strict ISP port restrictions.

#### 📊 Technical Specifications
| Component | Technology / Value |
| :--- | :--- |
| **Operating System** | Rocky Linux 8 (Virtual Machine Environment) |
| **Mail Suite** | Zimbra ZCS 8.8.15 GA |
| **SMTP Relay** | Brevo (formerly Sendinblue) |
| **Relay Port** | `2525` (Successfully bypassing ISP port 25/587 blocking) |
| **DNS Provider** | Cloudflare |

#### 🛠️ Core Implementations
1. **SMTP Relay Integration:** Configured Postfix within Zimbra to relay all outbound mail through Brevo, ensuring maximum deliverability to major providers like Gmail and Yahoo.
2. **Email Security Standards:**
   - Implemented **SPF, DKIM, and DMARC** records via Cloudflare to prevent domain spoofing.
   - Configured **SASL Authentication** to secure outbound SMTP communication.
3. **Domain Authentication:** Fully authenticated `aloy-tech.my.id` using Cloudflare’s Domain Connect to improve sender reputation and prevent emails from being flagged as spam.

#### 🔍 Troubleshooting & Key Takeaways
- **Authentication:** Resolved `535 5.7.8 Authentication failed` errors by validating Brevo SMTP API keys and mapping credentials correctly in Postfix (`sasl_passwd`).
- **Port Management:** Diagnosed connection timeouts on standard email ports and successfully pivoted to port **2525** for stable, unthrottled relaying.
- **Deliverability:** Verified that proper DKIM and SPF TXT records are absolutely essential for passing Google and Yahoo's strict security authentication filters.
- **Log Analysis:** Utilized Postfix mail queues and Zimbra logs (`/var/log/zimbra.log`) to debug mail delivery status in real-time.

---

## 🛠️ Other Services & Enterprise Expertise

- **Operating Systems:** Advanced systems administration across Linux distributions including Ubuntu, Debian, CentOS, and Rocky Linux.
- **Identity Management (OpenLDAP):** Centralized authentication setup, including cross-OS integration (connecting Linux VM servers to various LDAP clients).
- **Cloud Storage:** Deployed and maintained self-hosted Nextcloud instances for secure, private data management.
- **Secure Remote Access:** Implemented modern zero-trust networking using **Cloudflare Tunnels** and **Tailscale** for encrypted remote access without exposing public ports.
- **Cloudflare Integration:** Full domain management, custom DNS records tuning, and proxy optimization for web applications.

---
*Maintained by Daniel (aloy) — Passionate about Linux Systems and Network Engineering.*


### Notes
This setup is used for learning and homelab purposes only.
