# Jellyfin Docker Setup - kawaii-san-hub 

Stream your media to your hearts content!
Setup locally so you never worry about being tracked. And stream your downloaded files, STOP PAYING FOR STREAMING SERVICES!!!

---

## 🪼 Setting up Jellyfin is easy!
we just need 3 directories. We do this with
```
mkdir -p ~/docker/jellyfin/config
mkdir -p ~/docker/jellyfin/cache
mkdir -p ~/docker/jellyfin/meida
```
- cache (where we can store data temporarily)
- config (where we can config the service)
- medai (where all our content will be stored)

Then you create a [docker-compose.yml](./docker-compose.yml) file and dump in the code.
```
cd ~/docker/jellyfin
nano docker-compose.yml
```

then deploy the docker service with 
```
docker compose up -d
```

## ☁️ Cloudflare Tunnel Configuration
Woah woah woah, I ain't hacking myself. So we get cloudflare tunnel
Edit the "/etc/cloudflared/config.yml
```
  - hostname: jellyfin.domain.com
    service: http://localhost:8096
```
Restart the service:
```
sudo systemctl restart cloudflared
```
Then route the DNS:
```
cloudflared tunnel route dns <tunnel_ID> jellyfin.domain.com
```

## 🎉 Congrats!
You should be greeted with such a site:
<img width="1868" height="918" alt="image" src="https://github.com/user-attachments/assets/c69d56a2-35fc-4a5b-8174-a7efff3c92ac" />
If you do, you're done.
Now just makes sure your content is in the right directory
~~~
~/docker/jellyfin/media
~~~
and you're done.
Now Piss off cutie patootie!
