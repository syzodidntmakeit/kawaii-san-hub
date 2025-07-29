# Jellyfin 🪼 

## Stream your media to your hearts content!
Setup locally so you never worry about being tracked. And stream your downloaded files, STOP PAYING FOR STREAMING SERVICES!!!

---

Setting up Jellyfin is easy, we just need 3 directories. We do this with
```
mkdir -p ~/docker/jellyfin/config
mkdir -p ~/docker/jellyfin/cache
mkdir -p ~/docker/jellyfin/meida
```
- cache (where we can store data temporarily)
- config (where we can config the service)
- medai (where all our content will be stored)

Then you create a docker-compose.yml file and dump in the code.
```
cd ~/docker/jellyfin
nano docker-compose.yml
```

[You can find the file here!](./docker-compose.yml)


then deploy the docker service with 
```
docker compose up -d
```

And enter with 
~~~
http://<server-ip>:8096
~~~

You should be greeted with such a site:
<img width="1868" height="918" alt="image" src="https://github.com/user-attachments/assets/c69d56a2-35fc-4a5b-8174-a7efff3c92ac" />

## Congrats!

If you do, you're done.
Now just makes sure your content is in the right directory
~~~
~/docker/jellyfin/media
~~~
and you're done.
