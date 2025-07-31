# 🌐 kawaii-san-hub

Welcome to **kawaii-san-hub** — a self-hosted hub for all my local services like Jellyfin, Nextcloud, and more. Powered by Ubuntu Server OS (a headless operating system), Docker 🐳 and managed through Portainer. This project is designed to work behind CGNAT because Starhub doesn't like fun, I will be using NetBird and Cloudflare Tunnels. 

---

## 🧱 Stack Overview

| Service             | Description                                | Access URL                       |
|---------------------|--------------------------------------------|----------------------------------|
| **Portainer**       | Docker UI to manage my containers          | http://server-ip:9000            |
| **Jellyfin**        | Stream Anime without Netflix               | https://anime.kawaii-san.org     |
| **Nextcloud**       | Cloud storage, file sharing and backups    | https://cloud.kawaii-san.org     |
| **Navidrome**       | Stream music in FLAC and WAV               | https://music.kawaii-san.org     | 
| **Whoogle**         | Local Search Engine                        | https://whoogle.kawaii-san.org   |
| **Filebrowser**     | Lightweight file manager over WebUI        | https://files.kawaii-san.org     |
| **Joplin**          | Private note-taking based on Markdown      | https://notes.kawaii-san.org     |
| **netdata**         | Monitor the server and performance         | https://monitor.kawaii-san.org   |
| **Uptime-Kuma**     | Monitor the services and productivity      | https://uptime.kawaii-san.org    |
| **Vaultwarden**     | Self-hosted Password Manager               | https://passwords.kawaii-san.org |
| **Ollama + OpenUI** | Local AI Models with sick as f*ck webUI    | https://ai.kawaii-san.org        |
| **Librespeed**      | Speedtest.net at home                      | https://speedtest.kawaii-san.org |

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
.
.
.

you get the idea

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
```
### 🐦 NetBird Installation
```bash
curl -fsSL https://pkgs.netbird.io/install.sh | sh
netbird up
```
I love my bird. NetBird that is.
