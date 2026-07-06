Technical Stack

    OS: Rocky Linux 8 (Virtual Machine via Virt-Manager)

    📁 folder-webhook-lu/
    ├── 📄 Dockerfile
    ├── 📄 package.json
    ├── 📄 package-lock.json
    └── 📄 index.js

    docker ps -a
    docker start 35865a3df368
    docker stop 35865a3df368
    docker restart 35865a3df368



# 🚨 WhatsApp Webhook Monitoring

 Real-time infrastructure monitoring and alerting via WhatsApp using Docker.

---

# 📖 Overview

This project is a **Dockerized WhatsApp Webhook** designed to monitor server availability and service health in real time.

When a server or critical service becomes unavailable, the webhook automatically sends an alert notification to WhatsApp, allowing administrators to respond quickly and minimize downtime.

This project is part of my homelab infrastructure for learning Linux system administration, Docker, networking, and monitoring.

---

# ✨ Features

* 🚀 Real-time monitoring
* 📱 WhatsApp notifications
* 🐳 Docker deployment
* ❤️ Server health monitoring
* ⚙️ Service status monitoring
* 🔄 Automatic periodic checks
* 📊 Lightweight and easy to deploy
* 🔒 Suitable for internal infrastructure monitoring

---

# 🏗️ Infrastructure

| Component              | Technology |
| ---------------------- | ---------- |
| Monitoring Application | Node.js    |
| Container Platform     | Docker     |
| Notification           | WhatsApp   |
| Reverse Proxy          | Nginx      |
| Operating System       | Linux      |

---

# 🖥️ Monitoring Flow

          Server / VM
               │
       Health Check Script
               │
        Webhook Application
               │
      Docker Container
               │
      WhatsApp Notification
               │
        System Administrator

---

# 📊 Monitoring Capabilities

## 🖥️ Server Monitoring

* Server Online
* Server Offline
* Recovery Detection  (on pogres)
* Periodic Availability Check (on pogres)

## ⚙️ Service Monitoring

Monitor services such as:

* Nginx
* Apache
* Docker
* MariaDB / MySQL
* PostgreSQL
* SSH
* Zimbra
* LDAP
* FTP
* Custom Services

View logs

docker logs -f wa-webhook-app


Restart application


docker compose restart


---

# 📱 Example Alert

## ✅ Server Online

🟢 SERVER RECOVERED

Server : Rocky Linux 9
IP     : 192.168.1.10
Status : ONLINE
Time   : 2026-07-06 10:30


---

## ❌ Server Down

🔴 SERVER DOWN

Server : Rocky Linux 9
IP     : 192.168.1.10
Status : OFFLINE
Time   : 2026-07-06 10:31
```

---

## ⚠️ Service Down

```text
⚠️ SERVICE ALERT

Server  : Rocky Linux 9
Service : Docker
Status  : DOWN
Time    : 2026-07-06 10:35


---

# 🔒 Security

* Docker Isolation
* Environment Variables
* Reverse Proxy Ready
* HTTPS Support
* Firewall Friendly

---

# 📚 Learning Objectives

This project helps demonstrate practical experience with:

* Docker
* Linux Server Administration
* Infrastructure Monitoring
* WhatsApp API Integration
* Webhook Development
* Network Troubleshooting
* Automation
* DevOps Fundamentals

---

# 🛣️ Roadmap

* [x] Docker Deployment
* [x] WhatsApp Notifications
* [x] Server Availability Monitoring
* [x] Service Monitoring
* [ ] Email Notifications
* [ ] Grafana Integration
* [ ] Prometheus Metrics
* [ ] Multi-Server Dashboard
* [ ] Historical Monitoring Reports

---

# 📄 License

This project is licensed under the MIT License.

---

# 👨‍💻 Author

**Daniel Saragih**

GitHub:
https://github.com/Daniel212alloy

---

⭐ If you found this project useful, consider giving it a star!


