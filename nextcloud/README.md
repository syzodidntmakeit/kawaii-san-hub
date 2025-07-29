# Nextcloud Docker Setup — kawaii-san-hub

This documents how I set up Nextcloud with Docker on Ubuntu Server, exposed securely via Cloudflare Tunnel with custom ports and trusted domains configured.

---

## 🐳 Docker Compose
Get to you directory for nextcloud
> ~/docker/nextcloud
and create a [docker-compose.yml](./docker-compose.yml) file

## 🚀 Start Nextcloud
Once we have the compose file, just start it
```
cd ~/docker/nextcloud
docker compose up -d
```

## ☁️ Cloudflare Tunnel Configuration
WE WANT EASY ACCESS! So we get cloudflare tunnel
Edit the "/etc/cloudflared/config.yml
```
  - hostname: nextcloud.domain.com
    service: http://localhost:8018
```
Restart the service:
```
sudo systemctl restart cloudflared
```
Then route the DNS:
```
cloudflared tunnel route dns <tunnel_ID> nextcloud.domain.com
```

## 🔵NEXCTLOUD IS A WHINY LITTLE WH*RE
And we need to fix her. She doesn't anyone else. So let's tell her she's a b*tch.
1. Copy the config file out
```
docker cp nextcloud-app:/var/www/html/config/config.php ~/config.php
```
2. Add your domain to the trust_domains:
```
***
'trusted_domains' =>
array (
  0 => 'localhost',
  1 => 'your-server-ip',
  2 => 'nextcloud.domain.com',
),
```
3. Copy it back
```
docker cp ~/config.php nextcloud-app:/var/www/html/config/config.php
```
4. Fix the permissions inside the container
```
docker exec -it nextcloud-app /bin/bash
chown www-data:www-data /var/www/html/config/config.php
chmod 640 /var/www/html/config/config.php
exit
```
5. Restart the service
```
docker restart nextcloud-app
```

---

## 🎉Congrats!
Now access your new cloud storage service.
You should get a screen like this. Just set it up from there.
<img width="2560" height="1440" alt="image" src="https://github.com/user-attachments/assets/a99962e1-6632-4ecf-b531-6f2f00fe3f91" />
