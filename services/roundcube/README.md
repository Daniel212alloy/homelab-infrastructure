# 📧 Roundcube Webmail on Docker + Rocky Linux

Technical Stack

    OS: Rocky Linux 8 & Centos 9 (Virtual Machine via Virt-Manager)

    Mail Server: Postfix & Dovecot

    SMTP Relay: Brevo (Sendinblue)

    DNS Management: Cloudflare

    Networking: Cloudflare Tunnels (for webmail access)

Key Implementation

    Bypassing ISP Restrictions: Mengatasi pemblokiran port 25 & 587 oleh ISP dengan mengalihkan traffic ke port 2525.

    SMTP Authentication: Konfigurasi SASL authentication pada Postfix Zimbra menggunakan kredensial Brevo.

    DNS Security (SPF, DKIM, DMARC): Implementasi standar keamanan email via Cloudflare untuk memastikan email tidak masuk folder Spam.

    Relay Configuration:



## 📖 Overview

This project demonstrates how to deploy **Roundcube Webmail** using **Docker** on **Rocky Linux 9**, while connecting to a **remote MariaDB database** hosted on **CentOS 7**.

The environment is designed as part of a homelab infrastructure for learning, testing, and self-hosted email services.


## 📂 Project Structure

roundcube-docker/
├── docker-compose.yml
├── .env
├── config/
├── plugins/
├── skins/
├── logs/
└── README.md


Start container
docker compose up -d

Check running container

docker ps

View logs

docker logs -f roundcube

