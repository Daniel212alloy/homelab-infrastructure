# 📧 Self-Hosted Mail Server with Zimbra & Cloudflare Infrastructure

A self-hosted email infrastructure project built using **Zimbra Collaboration Suite** running on a virtual machine environment.

This project demonstrates the implementation of a private mail server, SMTP relay integration, DNS email security standards, and secure webmail access using Cloudflare infrastructure.

The main goal of this project is to build a reliable email system while overcoming ISP limitations and applying modern email security practices.

---

# 🏗️ Infrastructure Architecture

```
                 Internet
                    |
                    |
              Cloudflare DNS
                    |
        +-----------+-----------+
        |                       |
  Webmail Access          Email Security
 Cloudflare Tunnel      SPF / DKIM / DMARC
        |
        |
 Rocky Linux VM
        |
        |
 Zimbra Collaboration Suite
        |
        |
 Postfix SMTP Server
        |
        |
 Brevo SMTP Relay
```

---

# 🛠️ Technical Stack

| Component            | Technology                           |
| -------------------- | ------------------------------------ |
| Virtualization       | Virt-Manager (KVM/QEMU)              |
| Operating System     | Rocky Linux 8                        |
| Mail Platform        | Zimbra Collaboration Suite 8.8.15 GA |
| SMTP Server          | Postfix (Zimbra MTA)                 |
| SMTP Relay Provider  | Brevo (Sendinblue)                   |
| DNS Management       | Cloudflare DNS                       |
| Secure Remote Access | Cloudflare Tunnel                    |
| Authentication       | SASL SMTP Authentication             |

---

# 🚀 Key Implementation

## 1. Overcoming ISP SMTP Port Restrictions

Many ISPs block traditional mail ports such as:

* Port 25
* Port 587

To bypass these restrictions, outbound SMTP traffic was redirected through Brevo SMTP Relay using an alternative SMTP submission port:

```
Zimbra Postfix
        |
        |
SMTP Relay Authentication
        |
        |
Brevo SMTP Server (Port 2525)
```

This allows the mail server to send emails reliably without requiring direct SMTP connectivity from the ISP network.

---






[root@mail ~]# tail -f /var/log/zimbra.log | grep "smtp-relay.brevo.com"
Apr 15 13:03:29 mail postfix/smtp[105148]: C1583451154F: to=<danielsaragih212@gmail.com>, relay=smtp-relay.brevo.com[1.179.116.1]:2525, delay=2737, delays=2734/1.7/1.3/0.25, dsn=2.0.0, status=sent (250 2.0.0 OK: queued as <27687904.11.1776230268133.JavaMail.zimbra@aloy-tech.my.id>)
Apr 15 13:04:13 mail postfix/smtp[105149]: 3CC8945114BA: to=<danielsaragih212@gmail.com>, relay=smtp-relay.brevo.com[1.179.116.1]:2525, delay=1.5, delays=0.01/0/1.3/0.21, dsn=2.0.0, status=sent (250 2.0.0 OK: queued as <2137116700.64.1776233047367.JavaMail.zimbra@aloy-tech.my.id>)
Apr 15 13:08:07 mail postfix/smtp[108635]: BBE874511453: to=<danielsaragih212@gmail.com>, relay=smtp-relay.brevo.com[1.179.116.1]:2525, delay=1.7, delays=0.02/0.09/1.4/0.24, dsn=2.0.0, status=sent (250 2.0.0 OK: queued as <400483586.66.1776233280978.JavaMail.zimbra@aloy-tech.my.id>)
Apr 15 13:26:18 mail postfix/smtp[123539]: 9D03545113DF: to=<danielsaragih212@gmail.com>, relay=smtp-relay.brevo.com[1.179.116.1]:2525, delay=1.6, delays=0.01/0.03/1.3/0.28, dsn=2.0.0, status=sent (250 2.0.0 OK: queued as <1891224832.67.1776234371866.JavaMail.zimbra@aloy-tech.my.id>)
Apr 15 13:28:30 mail postfix/smtp[125339]: 943A34511187: to=<danielsaragih212@gmail.com>, relay=smtp-relay.brevo.com[1.179.116.1]:2525, delay=1.6, delays=0.01/0.03/1.3/0.28, dsn=2.0.0, status=sent (250 2.0.0 OK: queued as <243651722.75.1776234503921.JavaMail.zimbra@aloy-tech.my.id>)
Apr 15 13:30:34 mail postfix/smtp[126798]: CEDC14511187: to=<saragih.wiono@gamil.com>, relay=smtp-relay.brevo.com[1.179.116.1]:2525, delay=1.8, delays=0.02/0.05/1.4/0.28, dsn=2.0.0, status=sent (250 2.0.0 OK: queued as <1920019729.81.1776234628136.JavaMail.zimbra@aloy-tech.my.id>)
Apr 15 13:30:34 mail postfix/smtp[126798]: CEDC14511187: to=<danielsaragih212@gmail.com>, relay=smtp-relay.brevo.com[1.179.116.1]:2525, delay=1.8, delays=0.02/0.05/1.4/0.28, dsn=2.0.0, status=sent (250 2.0.0 OK: queued as <1920019729.81.1776234628136.JavaMail.zimbra@aloy-tech.my.id>)
Apr 15 13:33:31 mail postfix/smtp[128722]: BC87A45114B8: to=<danielsaragih212@gmail.com>, relay=smtp-relay.brevo.com[1.179.116.1]:2525, delay=1.6, delays=0.01/0.03/1.3/0.27, dsn=2.0.0, status=sent (250 2.0.0 OK: queued as <229680980.83.1776234805052.JavaMail.zimbra@aloy-tech.my.id>)
Apr 15 13:33:31 mail postfix/smtp[128722]: BC87A45114B8: to=<saragih.wiono@gmail.com>, relay=smtp-relay.brevo.com[1.179.116.1]:2525, delay=1.6, delays=0.01/0.03/1.3/0.27, dsn=2.0.0, status=sent (250 2.0.0 OK: queued as <229680980.83.1776234805052.JavaMail.zimbra@aloy-tech.my.id>)
Apr 15 13:35:58 mail postfix/smtp[130332]: 4844E45114B8: to=<danielsaragih212@gmail.com>, relay=smtp-relay.brevo.com[1.179.116.1]:2525, delay=1.6, delays=0.01/0.03/1.3/0.24, dsn=2.0.0, status=sent (250 2.0.0 OK: queued as <81952014.85.1776234952395.JavaMail.zimbra@aloy-tech.my.id>)
Apr 15 13:35:58 mail postfix/smtp[130332]: 4844E45114B8: to=<melda_alin@yahoo.co.id>, relay=smtp-relay.brevo.com[1.179.116.1]:2525, delay=1.6, delays=0.01/0.03/1.3/0.24, dsn=2.0.0, status=sent (250 2.0.0 OK: queued as <81952014.85.1776234952395.JavaMail.zimbra@aloy-tech.my.id>)
