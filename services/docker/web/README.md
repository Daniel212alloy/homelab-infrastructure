# 🌐 Docker Web Server Deployment with Cloudflare Tunnel

A self-hosted web deployment project running inside a Docker container and exposed to the public internet securely using **Cloudflare Tunnel**.

This project demonstrates containerized web hosting, secure remote access, and modern infrastructure deployment practices without exposing local server ports directly to the internet.

---

## 🚀 Features

* ✅ Web application running inside Docker Container
* ✅ Secure public access through Cloudflare Tunnel
* ✅ No direct port forwarding required
* ✅ Automatic HTTPS with Cloudflare SSL
* ✅ Isolated and portable container environment
* ✅ Easy deployment and maintenance

---


## 🛠️ Technology Stack

| Component          | Technology        |
| ------------------ | ----------------- |
| Container Platform | Docker            |
| Web Server         | Apache / Nginx    |
| Secure Tunnel      | Cloudflare Tunnel |
| SSL / HTTPS        | Cloudflare        |
| Host OS            | Rocky Linux       |
| Deployment         | Docker Compose    |

---

## 📂 Project Structure

```
.
├── docker-compose.yml
├── Dockerfile
├── web/
│   ├── index.html
│   ├── css/
│   ├── js/
│   └── assets/
└── README.md
```

---


### Build Docker Image

```bash
docker compose build
```

### Start Container

```bash
docker compose up -d
```

Check running containers:

```bash
docker ps
```

---

## 🌍 Cloudflare Tunnel Configuration

Cloudflare Tunnel provides secure access from the internet to local services without opening inbound ports.


---

## 🔐 Security Benefits

Using Cloudflare Tunnel provides:

* No exposed public IP address
* No open inbound firewall ports
* Encrypted connection between server and Cloudflare
* HTTPS protection managed by Cloudflare
* Additional security layer through Cloudflare network

---

## 📊 Management & Monitoring

Docker container management:

```bash
docker ps
```

View container logs:

```bash
docker logs -f container-name
```

Monitor resource usage:

```bash
docker stats
```

---

## 🎯 Project Goals

This project was created to learn and demonstrate:

* Linux server administration
* Docker container management
* Cloudflare Zero Trust networking
* Secure self-hosted services
* Homelab infrastructure development

---

## 🔮 Future Improvements

* [ ] Add CI/CD automation
* [ ] Integrate Prometheus & Grafana monitoring
* [ ] Add automated backup system
* [ ] Improve container security hardening
* [ ] Deploy additional self-hosted services

---

## 👨‍💻 Author

**Daniel Saragih**



---

⭐ Built as part of a personal homelab infrastructure and continuous learning journey.

