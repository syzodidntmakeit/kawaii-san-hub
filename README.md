# 🌐 kawaii-san-hub

Welcome to **kawaii-san-hub** — a self-hosted hub for all my local services like Jellyfin, Nextcloud, and more. Powered by Docker and managed through Portainer. This project is built on Ubuntu Server and designed to work behind CGNAT using NetBird and Cloudflare Tunnels.

---

## 🧱 Stack Overview

| Service       | Description                                | Access URL (example)             |
|---------------|--------------------------------------------|----------------------------------|
| **Portainer** | Docker UI to manage containers             | http://your-ip:9000              |
| **Jellyfin**  | Stream Anime                               | https://jellyfin.kawaii-san.org  |
| **Nextcloud** | Cloud Storage and Note taking              | https://nextcloud.kawaii-san.org |
| **Navidrome** | Stream music in FLAC and WAV               | https://navidrome.kawaii-san.org | 
| **Whoogle**   | Local Search Engine                        | https://whoogle.kawaii-san.org   |

---

## 🔒 Networking Stack

- **NetBird**: Mesh VPN to access server behind CGNAT.
- **Cloudflare Tunnel**: Exposes services securely to the web with free SSL.
- **Cloudflare DNS**: Manages subdomains (e.g. `jellyfin.kawaii-san.org`, etc).

---

## 📁 Directory Structure

All services are organized under `~/docker/`:

~/docker/

├── portainer/

│ └── docker-compose.yml

├── jellyfin/

│ └── docker-compose.yml

└── nextcloud/

  └── docker-compose.yml

---

## 🚀 Service Deployment

### 🧰 Prerequisites

- Ubuntu Server OS
- Docker & Docker Compose
- Cloudflare domain
- NetBird installed on host and client

### 🐳 Docker Installation

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo apt install docker-compose -y
sudo usermod -aG docker $USER
