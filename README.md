# 🚀 Homelab Infrastructure

A comprehensive documentation of my personal IT infrastructure, focusing on server administration, networking, and self-hosted services. This repository serves as a technical log for configurations and real-world problem-solving.

## 🔧 Tech Stack

🐧 Operating Systems
  * Debian * Ubuntu * CentOS * Rocky Linux
💻 Virtualization 
  * KVM (Virt-Manager) * VirtualBox
🌐 Web Server & Development
  * Apache HTTP Server * MariaDB * PHP (LAMP Stack) * Bash
🌍 Networking & Security
  * MikroTik  * Port Forwardin  * Firewall Configuration * NAT
📧 Mail & Collaboration
  * Zimbra Collaboration Suite * Roundcube Webmail
👥 Directory Services
  * OpenLDAP Server  * Multi-OS LDAP Client Configuration
📂 Self-Hosted Services
  * Nextcloud  * Truenas * Samba * FTP Server
🐳 Containers & 📊 Monitoring
  * Docker  * Webhook Alert Monitoring * Grafana * Prometheus
☁️ Cloud & Edge Services
  * Cloudflare DNS Management * Cloudflare Tunnel (Web Server & Nextcloud) * Email DNS Configuration SPF,DKIM,DMARC

## 🎯 Current Homelab

| Service                    | Status    | Platform       | Notes                           |
| -------------------------- | --------- | -------------- | ------------------------------- |
| Zimbra Collaboration Suite | ✅ Running | Rocky Linux VM | Mail Server                     |
| Roundcube Webmail          | ✅ Running | Docker         | Connected to external Postfix   |
| Postfix SMTP Relay         | ✅ Running | Centos 9 VM    | Integrated with Brevo SMTP      |
| Brevo SMTP                 | ✅ Active  | Cloud Service  | Outbound mail relay             |
| Nextcloud                  | ✅ Running | Debian & Centos| Published via Cloudflare Tunnel |
| OpenLDAP                   | ✅ Running | Centos 7 VM    | Centralized Authentication      |
| Grafana                    | ✅ Running | Docker         | Infrastructure Monitoring       |
| Prometheus                 | ✅ Running | Docker         | Metrics Collection              |
| WhatsApp Alert             | ✅ Running | Docker         | Webhook Monitoring              |
| Cloudflare Tunnel          | ✅ Running | Cloudflare     | Secure public access            |


📂 Featured Projects & 💼 Experience Through Projects

## 🌐 Networking Setup
- Implemented IP segmentation using Mikrotik RouterOS
- Separated server and client networks using different subnets
- Configured NAT and port forwarding for self-hosted services
- Applied basic firewall rules for access control

## 📧 Mail Server Stack (Zimbra Collaboration)
Successfully deployed **Zimbra Collaboration Suite (ZCS 8.8.15)** on **Rocky Linux 8**. The primary focus of this lab was to establish a reliable email delivery system despite ISP port restrictions.

### **Technical Specifications**
- **Operating System:** Rocky Linux 8 (VM environment)
- **Mail Suite:** Zimbra ZCS 8.8.15 GA
- **SMTP Relay:** Brevo (formerly Sendinblue)
- **Relay Port:** 2525 (Bypassing ISP port 25/587 blocking)
- **DNS Provider:** Cloudflare

### **Core Implementations**
1. **SMTP Relay Integration:** Configured Zimbra to relay outbound mail through Brevo to ensure high deliverability to providers like Gmail and Yahoo.
2. **Email Security Standard:**
   - Implemented **SPF, DKIM, and DMARC** records via Cloudflare.
   - Configured **SASL Authentication** for secure SMTP communication.
3. **Domain Authentication:** Fully authenticated `aloy-tech.my.id` using Cloudflare’s Domain Connect to improve sender reputation and prevent spam flagging.

### **Troubleshooting & Key Takeaways**
- **Authentication:** Resolved `535 5.7.8 Authentication failed` errors by validating SMTP API keys and mapping credentials correctly in Postfix.
- **Port Management:** Diagnosed connection timeouts on standard ports and successfully pivoted to port **2525** for stable relaying.
- **Deliverability:** Verified that proper DKIM TXT records are essential for passing Google's strict security filters.

## 🛠️ Other Services & Expertise
- **Operating Systems:** Advanced administration of Ubuntu, Debian, CentOS, and Rocky Linux.
- **Identity Management:** Centralized authentication using OpenLDAP.
- **Cloud Storage:** Self-hosted Nextcloud instance for private data management.
- **Secure Access:** Implementing Cloudflare Tunnels and Tailscale for encrypted remote access.
- **LDAP:** Integrasi Ldap VM to Ldap Client with Other OS
- **Cloudflare:** Setting Cloudflare and integrasi Domain and Tunnel
---
*Maintained by Daniel (aloy) — Passionate about Linux Systems and Network Engineering.*


### Notes
This setup is used for learning and homelab purposes only.


