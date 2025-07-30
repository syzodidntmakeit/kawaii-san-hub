# Jellyfin: Watch all the Anime - kawaii-san-hub 

I was always interested in Anime, I just never found the time to actually sit down and enjoy. With this, I'm morally obligated to appreciate my work. Grr. Let's get started.

---

## First, I created a docker compose file 🐳

Typically for Jellyfin, we just need 3 directories. So I;
```
mkdir -p ~/docker/jellyfin/config
mkdir -p ~/docker/jellyfin/cache
mkdir -p ~/docker/jellyfin/meida
```
This is done because Jellyfin has 3 important files it reaches for:
- cache (where we can store data temporarily)
- config (where we can config the service)
- media (where all our content will be stored)
Typically you would route the media directory to your own content file, but since I'm startin new, I don't have one.

next I created a [docker-compose.yml](./docker-compose.yml) file. Pretty basic sh*t.
```
cd ~/docker/jellyfin
sudo nano docker-compose.yml
```

## Second, Run that bad boi! ⚡

Deploy the docker service with 
```
docker compose up -d
```
(We use ' -d ' as to run the file detached from the interface so it runs in the background as we can do other shit instead)

Usually, this is the point where we enter the IP port address into the web browser and viola, but I'm special (mentally) and I want a subdomain for Jellyfin. Thus, I took a detour.

## Clouds' the Limit ☁️
We ❤️ Cloudflare. These f*ckers use lavalamps because computers are too vulnerable to secure your websites. Madlads.
I create a subdomain with my domain I bought FROM Cloudflare (ily mwah) and we can easily access my Jellyfin server that's much easier to remember compared to a bunch of noomberos. (Grr.)

I edit the "/etc/cloudflared/config.yml
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

## 🎉 YIPPEE!
If your following along, you should be greeted with such a site:
<img width="1868" height="918" alt="image" src="https://github.com/user-attachments/assets/c69d56a2-35fc-4a5b-8174-a7efff3c92ac" />
I did, so now I can finally stop whinning about having nothing to watch. I literally spent sleepless nights downloading a LOT of shows, I WILL watch em. (this isn't a choice)

Anyways, I can either save my content here;
~~~
~/docker/jellyfin/media
~~~
or route a ~/media/anime into the service and it's easier to remember. This is good practise, but I'm lazy.

Anyways, bye bye cutie patootie!
