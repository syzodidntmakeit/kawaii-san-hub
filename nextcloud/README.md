# Nextcloud: GOODBYE GOOGLE DRIVE! — kawaii-san-hub

I **hate** Google Drive and their Google Services. It's mediocre at best and intrusive at worse. At times where your wifi just dies, and you are left wondering, "I'm sorry? Excuse me? WTF?". Turns out Drive decided you DIDN'T need your bandwidth and backups every single bit on your phone. And no. There's no way to stop it. I hate it. But I am smart enough to do something about it. Thus, Nextcloud.

---

## I am the Datacenter ☁️

Instead of trusting Tech Giants with my data, I'll manage them myself, thank you very much. Nextcloud; turn your home PC into a proper server. It supports backups, note taking, metadata editing... all over a web interface. All for the low low price FREE! (that's GFYS money)

I created a ~/docekr/nexcloud directory cuz I like to be organized.
Created a [docker compose](.docker-compose.yml), which is a heavy blueprint since Nextcloudhas a bunch of security functions.
And then ran it.
```
docker compose up -d
```

For reference, this is what it's supposed to look like kinda, not exactly.

<img width="920" height="880" alt="image" src="https://github.com/user-attachments/assets/a99962e1-6632-4ecf-b531-6f2f00fe3f91" />

## Cloudflare, my pookie 🌧️

What's better than 1 line of security? 2 lines of security. Nextcloud is already pretty secure, but I went, "Nuh uh", and added my cloud server to my domain DNS.

I did it by editing the "/etc/cloudflared/config.yml
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

Yadda yadda yoda...

## 🔵Top 10 Anime Betrayals

Nextcloud is so secure, it doesn't even let YOU in.
So first, we tell him, "Yes, I am indeed, suppose to be here".

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

## 🎉やった!!!
Now I can access my new cloud storage service.

And I can save pics of Asuka Langsley from Evangelion: Neon Genesis
Grr.
![image-asset](https://github.com/user-attachments/assets/24251860-26b6-43a9-a49d-1ed61800ac32)
