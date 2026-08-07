# 🏡 Home Server Documentation

![Debian](https://img.shields.io/badge/OS-Debian-A81D33?style=flat&logo=debian&logoColor=white)
![Docker](https://img.shields.io/badge/Container-Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Tailscale](https://img.shields.io/badge/Mesh-Tailscale-242424?style=flat&logo=tailscale&logoColor=white)
![Portainer](https://img.shields.io/badge/Manage-Portainer-13BEF9?style=flat&logo=portainer&logoColor=white)
![Uptime Kuma](https://img.shields.io/badge/Monitor-Uptime%20Kuma-5CDA64?style=flat&logo=uptime-kuma&logoColor=white)
![ntfy](https://img.shields.io/badge/Notify-ntfy-3182CE?style=flat&logo=ntfy&logoColor=white)
![Beszel](https://img.shields.io/badge/Stats-Beszel-10B981?style=flat&logo=beszel&logoColor=white)

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
| **Uptime Kuma** | Monitoring | Docker | Web-based service uptime and HTTP/ICMP/TCP monitor |
| **ntfy** | Notifications | Docker | HTTP-based pub-sub notification service for pushing server alerts to mobile devices |
| **Beszel** | Telemetry / Stats | Docker | Modern, lightweight server resource monitor (CPU, RAM, GPU, Docker, Temps) communicating via Unix Socket |
| **Portainer** | Management | Docker | Lightweight web-based visual management UI for Docker containers, images, volumes, and stacks |

---

## 🔮 Planned Services

- [ ] **Vaultwarden** (Self-hosted password manager)
- [ ] **Homepage / Dashy** (Central dashboard for launching all web apps)
- [x] **Uptime Kuma** (Monitoring server health and container status)
- [x] **Portainer** (Web UI for managing Docker containers)
- [x] **ntfy** (Push notification pipeline for server alerts)
- [x] **Beszel** (Host telemetry and container resource tracking)
- [ ] **Joplin** (Secure note-taking and to-do app)

---

## 🔒 Security & Optimization Setup

* **Firewall (UFW):** Strict default deny incoming policy. Allows only Tailscale (`tailscale0`) and local LAN subnet (`192.168.0.0/24`).
* **Inter-Container Communication:** `ntfy` and `Uptime Kuma` linked via custom Docker bridge networks (`uptime-kuma_default`).
* **Beszel Socket Interconnect:** Beszel Hub and Agent communicate directly via host-mounted Unix socket (`./beszel_socket/beszel.sock`) for firewall-free, zero-latency metric streaming.
* **Power Management:** 
  * PowerTOP tuned for minimal idle consumption.
  * Discrete NVIDIA GPU blacklisted to eliminate draw.
  * Radios (Wi-Fi/Bluetooth) disabled via `rfkill`.
* **SSH Access:** Protected via Tailscale identity-based authentication with password/standard port exposure restricted.

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
