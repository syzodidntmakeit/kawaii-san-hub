# 🌐 kawaii-san-hub

Welcome to **kawaii-san-hub** — a self-hosted hub for all my local services like Jellyfin, Nextcloud, and more. Powered by Ubuntu Server OS (a headless operating system), Docker 🐳 and managed through Portainer. This project is designed to work behind CGNAT because Starhub doesn't like fun, I will be using NetBird and Cloudflare Tunnels. 

---

## 🧱 Stack Overview

| Service             | Description                                | Type | Access URL                       |
|---------------------|--------------------------------------------|------|----------------------------------|
| **Portainer**       | Docker UI to manage my containers          | Miscellaneous | http://portainer.kawaii-san.org  |
| **Jellyfin**        | Stream Anime without Netflix               | Entertainment | https://anime.kawaii-san.org     |
| **Nextcloud**       | Cloud storage, file sharing and backups    | Files | https://cloud.kawaii-san.org     |
| **Navidrome**       | Stream music in FLAC and WAV               | Entertainment | https://music.kawaii-san.org     | 
| **Whoogle**         | Local Search Engine                        | Productivity | https://whoogle.kawaii-san.org   |
| **Filebrowser**     | Lightweight file manager over WebUI        | Files | https://files.kawaii-san.org     |
| **Joplin**          | Private note-taking based on Markdown      | Productivity | https://notes.kawaii-san.org     |
| **netdata**         | Monitor the server and performance         | Miscellaneous | https://monitor.kawaii-san.org   |
| **Uptime-Kuma**     | Monitor the services and productivity      | Miscellaneous | https://uptime.kawaii-san.org    |
| **Vaultwarden**     | Self-hosted Password Manager               | Miscellaneous | https://passwords.kawaii-san.org |
| **Ollama + OpenUI** | Local AI Models with sick as f*ck webUI    | Productivity | https://ai.kawaii-san.org        |
| **Librespeed**      | Speedtest.net at home                      | Misc | https://speedtest.kawaii-san.org |

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
