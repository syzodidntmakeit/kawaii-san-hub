# 🔎 Whoogle - Self-hosted Private Google Frontend

**Whoogle Search** is a self-hosted proxy to Google Search that removes ads, tracking, and JavaScript — giving you fast and private search.
This is probably the easiest one yet

## 🐳 Docker Compose
Get to your directory for whoogle
> ~/docker/whoogle
adn create a [docker-compose.yml](./docker-compose.yml) file

## 🚀 Start Whoogle
Once we have the compose file, fire up the search engine.
```
cd ~/docker/whoogle
docker compsoe up -d
```

## ☁️ Cloudflare Tunnel Configuration
local IP web addresses? yuck. Give me that good-good. So we get cloudflare tunnl.
Edit the "/etc/cloudflared/config.yml
```
  - hostname: whoogle.domain.com
    service: http://localhost:8012
```
Restart the service:
```
sudo systemctl restart cloudflared
```
Then route the DNS:
```
cloudflared tunnel route dns <tunnel_ID> whoogle.domain.com
```

## 🎉Congrats!
Now research in peace without being bogged down by Google's and his goofy little brother Bing.
You should get a screen like this. It ain't **that** hard.
<img width="1860" height="910" alt="image" src="https://github.com/user-attachments/assets/0db41c47-2b8d-4fc4-91ae-98c2a2fb7ed0" />
