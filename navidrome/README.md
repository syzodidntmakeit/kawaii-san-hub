# 💿 Navidrome Docker Setup - kawaii-san.org

Stream music you own, instead of what's popular. And no one can judge you. Stop spending $5/mnth and shitty Green App or funny Red App...
Take Control

---

## 🐳 Docker Compose
Get to you directory for navidrome
> ~/docker/navidrome
and create a [docker-compose.yml](./docker-compose.yml) file

## 🎵 Start Navidrome
Once we have the compose file, just start it
```
cd ~/docker/navidrome
docker compose up -d
```

## ☁️ Cloudflare Tunnel Configuration
WHAT IS LOVE!? idk-... So we get cloudflare tunnel
Edit the "/etc/cloudflared/config.yml
```
  - hostname: navidrome.domain.com
    service: http://localhost:4533
```
Restart the service:
```
sudo systemctl restart cloudflared
```
Then route the DNS:
```
cloudflared tunnel route dns <tunnel_ID> navidrome.domain.com
```
You're off to the races.

---

## 🎉Congrats!
Now access your music from anywhere.
You should get a screen like this. Just set it up from there and you're golden. 
![navidrome-docker-05](https://github.com/user-attachments/assets/a0d1d485-9026-46ab-a603-9cf889e968c6)
