# ☁️ Cloudflare Infrastructure & Secure Tunnel Deployment

This project implements **Cloudflare infrastructure services** to securely expose self-hosted applications running inside a private homelab environment to the public internet.

The main purpose of this implementation is to provide secure remote access without exposing the local server directly through public IP addresses or opening inbound firewall ports.

---

# 🏗️ Architecture Overview

```
                    Internet
                       |
                       |
              Cloudflare Network
                       |
          +------------+------------+
          |                         |
     Cloudflare DNS          Cloudflare Tunnel
          |                         |
          |                         |
     Domain Management        Encrypted Tunnel
                                    |
                                    |
                           Local Homelab Server
                                    |
                                    |
                              Self-Hosted Services
                                    |
              +---------------------+---------------------+
              |                     |                     |
             Web                Webmail              Monitoring
          Docker App            Zimbra              Grafana
```

---

# 🛠️ Technical Stack

| Component           | Technology                      |
| ------------------- | ------------------------------- |
| DNS Provider        | Cloudflare DNS                  |
| Secure Access       | Cloudflare Tunnel               |
| Zero Trust Platform | Cloudflare Zero Trust           |
| SSL/TLS             | Cloudflare Managed Certificates |
| Server Environment  | Linux Homelab                   |
| Container Platform  | Docker                          |
| Virtualization      | KVM / Virt-Manager              |

---

# 🚀 Key Implementation

## 1. Secure Public Access with Cloudflare Tunnel

Cloudflare Tunnel creates an outbound-only encrypted connection from the local server to Cloudflare's global network.

Benefits:

* No public IP exposure
* No inbound firewall ports required
* No router port forwarding
* Automatic HTTPS support
* Protected by Cloudflare security layer

Traffic flow:

```
User Browser
      |
      |
Cloudflare Edge Network
      |
      |
Encrypted Tunnel
      |
      |
Local Service
```

---

# 🌐 DNS Management

Cloudflare DNS is used to manage domain records and route services to the correct tunnel endpoints.

Example services:

```
aloy-tech.my.id
        |
        |
+-------------------------+
|                         |
cloud.aloy-tech.my.id     mail.aloy-tech.my.id
        |                         |
     Nextcloud               Zimbra Webmail
```

DNS features implemented:

* A / CNAME record management
* Proxy configuration
* SSL/TLS configuration
* Domain routing

---

# 🔐 Security Features

Implemented security improvements:

* ✅ Hidden origin server IP address
* ✅ HTTPS encryption
* ✅ Cloudflare security layer
* ✅ Secure tunnel-based access
* ✅ DNS-based service routing

---

# ⚙️ Cloudflare Tunnel Configuration

Example configuration:

```yaml
tunnel: tunnel-id
credentials-file: /home/user/.cloudflared/tunnel.json

ingress:
  - hostname: example.domain.com
    service: http://localhost:8080

  - service: http_status:404
```

Run tunnel:

```bash
cloudflared tunnel run tunnel-name
```

---

# 📂 Directory Example

```
cloudflare/
│
├── tunnel-config.yml
├── README.md
└── screenshots/
```

---

# 🎯 Project Goals

This Cloudflare implementation was created to learn and demonstrate:

* Secure self-hosted service exposure
* Zero Trust networking concepts
* DNS management
* Reverse proxy architecture
* Cloud-based security integration

---

# 🔮 Future Improvements

* [ ] Add Cloudflare Access authentication
* [ ] Implement additional security policies
* [ ] Integrate monitoring alerts
* [ ] Automate tunnel deployment
* [ ] Add infrastructure documentation

---

# 👨‍💻 Author

**Daniel Saragih**


---

⭐ Part of a personal homelab infrastructure project focused on Linux administration, networking, and self-hosted services.

