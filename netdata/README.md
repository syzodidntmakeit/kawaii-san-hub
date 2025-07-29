# Netdata Docker Setup - kawaii-san hub

Monitor your server's performance, and look like an elite hacker while doing it.

---

## 🐳 Docker Compose
Get to your directory for netdata
> ~/docker/netdata
and create a [docker-compose.yml](./docker-compose.yml) file

## 🚀 Start Nextcloud
Once we have the compose file, just start it
```
cd ~/docker/nextcloud
docker compose up -d
```

## ☁️ Cloudflare Tunnel Configuration
I am hacker and super cool... So we get cloudflare tunnel. 

Edit the "/etc/cloudflared/config.yml
```
  - hostname: netdata.domain.com
    service: http://localhost:19999
```
Restart the service:
```
sudo systemctl restart cloudflared
```
Then route the DNS:
```
cloudflared tunnel route dns <tunnel_ID> netdata.domain.com
```

---

## 🎉Congrats!
Now access your agent, get ready to get blasted with information you don't understand and refuse to process. And green. 🤷
Click Sign-In or continue wihtout signing in.
You should get a screen like this. Prada no voila.
<img width="1865" height="914" alt="image" src="https://github.com/user-attachments/assets/470fad1d-467f-4377-8780-b101f937f69c" />
Scary
