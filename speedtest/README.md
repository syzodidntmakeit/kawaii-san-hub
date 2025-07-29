# Librespeed Docker Setup - kawaii-san-hub

Want a way to test the internet connection between you and your server? Here's an easy way to do it.

## 🐳 Docker Compose
Get to you directory for librespeed
> ~/docker/librespeed
and create a [docker-compose.yml](./docker-compose.yml) file. Simple.

## 🚀 Start Librespeed
Once we have the compose file, just start it
```
cd ~/docker/librespeed
docker compose up -d
```
Good.

## ☁️ Cloudflare Tunnel Configuration
"We have Cloudflare at home". So we get cloudflare tunnel
Edit the "/etc/cloudflared/config.yml
```
  - hostname: librespeed.domain.com
    service: http://localhost:8015
```
Restart the service:
```
sudo systemctl restart cloudflared
```
Then route the DNS:
```
cloudflared tunnel route dns <tunnel_ID> librespeed.domain.com
```
## 🎉Congrats!
The numbers go up and your bandwidth goes VROOM VROOM!
You should get a screen like this. Plain and s1mple.
<img width="1867" height="917" alt="image" src="https://github.com/user-attachments/assets/154781e8-1515-4a79-bea7-16d797c37868" />
Enjoy.
