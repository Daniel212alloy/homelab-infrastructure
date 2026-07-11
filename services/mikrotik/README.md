# 🌐 MikroTik Router Infrastructure

This project contains the **MikroTik router configuration** used as the core networking component in my self-hosted homelab infrastructure.

The MikroTik router runs as a virtual machine and provides network routing, NAT, firewall management, and connectivity between multiple virtual networks and self-hosted services.

---

# 🏗️ Network Architecture

```
                    Internet
                       |
                       |
                 MikroTik Router
                 (Virtual Router)
                       |
        +--------------+--------------+
        |              |              |
      LAN-A          LAN-B          LAN-C
   10.20.70.0/24   172.16.8.0/24  192.168.60.0/24
        |              |              |
        |              |              |
   Web Services     Mail Server    Internal VM
   Nextcloud        Zimbra         Services
```

---

# 🛠️ Technical Stack

| Component       | Technology              |
| --------------- | ----------------------- |
| Router Platform | MikroTik RouterOS       |
| Deployment      | Virtual Machine         |
| Hypervisor      | Virt-Manager (KVM/QEMU) |
| Networking      | Virtual Bridge Network  |
| Firewall        | MikroTik Firewall       |
| NAT             | Masquerade NAT          |
| Routing         | Static Routing          |

---

# 🚀 Main Responsibilities

The MikroTik router is responsible for:

* Network gateway management
* Routing between virtual networks
* NAT configuration
* Firewall rule management
* Port forwarding
* Internet access for internal services
* Network segmentation

---

# 🌐 Network Interfaces

Example interface mapping:

| Interface | Network | Purpose                   |
| --------- | ------- | ------------------------- |
| ether1    | WAN     | Internet Gateway          |
| ether2    | LAN-A   | Web / Application Network |
| ether3    | LAN-B   | Internal Services         |
| ether4    | LAN-C   | Server Network            |

---

# 🔥 NAT Configuration

Internet access for internal networks is provided using NAT masquerading.

Example:

```
Private Network
       |
       |
 MikroTik NAT
       |
       |
    Internet
```

Example configuration:

```bash
/ip firewall nat
add chain=srcnat out-interface=ether1 action=masquerade
```

---

# 🔐 Firewall Management

Firewall rules are implemented to:

* Control incoming and outgoing traffic
* Protect internal services
* Limit unauthorized access
* Manage service exposure

Security approach:

* Allow required services only
* Block unnecessary access
* Separate internal networks

---

# 🔀 Routing Configuration

The router manages communication between different network segments.

Example networks:

```
LAN-A
10.20.70.0/24

LAN-B
172.16.8.0/24

LAN-C
192.168.60.0/24
```

Routing allows services located in different networks to communicate securely.

---

# 📦 Configuration Backup

Export MikroTik configuration:

```bash
/export file=backup-config (Planing)
```

Restore configuration:

```bash
/import file-name=backup-config.rsc  (Planing)
```

---

# 📂 Project Structure

```
mikrotik/
│
├── README.md
├── firewall.rsc
├── nat.rsc
├── routing.rsc
└── topology.png
```

---

# 🎯 Project Goals

This MikroTik implementation was created to learn and demonstrate:

* Enterprise-style network design
* Router configuration and management
* Firewall concepts
* Network segmentation
* Virtual networking in homelab environments

---

# 🔮 Future Improvements

* [ ] Add VLAN implementation 
* [ ] Add VPN remote access
* [ ] Add centralized network monitoring
* [ ] Improve firewall security policies
* [ ] Automate configuration backup

---

# 👨‍💻 Author

**Daniel Saragih**

---

⭐ Part of a personal homelab infrastructure project focused on networking, virtualization, Linux administration, and self-hosted services.

