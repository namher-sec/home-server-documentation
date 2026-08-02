# 🏡 Home Server Documentation

![Debian](https://img.shields.io/badge/OS-Debian-A81D33?style=flat&logo=debian&logoColor=white)
![Docker](https://img.shields.io/badge/Container-Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Tailscale](https://img.shields.io/badge/Mesh-Tailscale-242424?style=flat&logo=tailscale&logoColor=white)

Welcome to my home server repository! This repo documents my homelab setup, network architecture, and self-hosted services running on Debian Linux.

---

## 💻 Hardware Specs

* **Device:** Dell Precision M4800
* **OS:** Debian Linux 13 (Trixie)
* **CPU:** Intel(R) Core(TM) i7-4810MQ (8) @ 3.80 GHz
* **RAM:** 16 GB
* **Storage:** 512 GB SATA SSD
* **Primary Interface:** Ethernet (`eno1`) 

---

## 🚀 Currently Running Services

All services are containerized using **Docker** and **Docker Compose**, managed behind a strict UFW firewall.

| Service | Category | Deployment | Description |
| :--- | :--- | :--- | :--- |
| **Tailscale** | Networking | Native Service | Encrypted mesh VPN for secure remote access without open ports |
| **AdGuard Home** | Network / Security | Docker | Network-wide DNS ad-blocking and tracking sinkhole |
| **Nextcloud** | Cloud & Storage | Docker | Self-hosted personal cloud storage, file sync, and backup |

---

## 🔮 Planned Services

- [ ] **Vaultwarden** (Self-hosted password manager)
- [ ] **Homepage / Dashy** (Central dashboard for launching all web apps)
- [ ] **Uptime Kuma** (Monitoring server health and container status)
- [ ] **Portainer** (Web UI for managing Docker containers)
- [ ] **Joplin** (Secure note-taking and to-do app)


---

## 🔒 Security & Optimization Setup

* **Firewall (UFW):** Strict default deny incoming policy. Allows only Tailscale (`tailscale0`) and local LAN subnet (`192.168.0.0/24`).
* **Power Management:** 
  * PowerTOP tuned for minimal idle consumption.
  * Discrete NVIDIA GPU blacklisted to eliminate draw.
  * Radios (Wi-Fi/Bluetooth) disabled via `rfkill`.
* **SSH Access:** Protected via Tailscale identity-based authentication with password/standard port exposure restricted.

---

## 📂 Repository Structure

```text
.
├── docker/
│   ├── adguard/
│   │   └── docker-compose.yml
│   └── nextcloud/
│       └── docker-compose.yml
├── scripts/
│   └── power-tuning.sh
└── README.md
