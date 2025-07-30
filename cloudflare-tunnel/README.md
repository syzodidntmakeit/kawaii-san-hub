# ☁️ Cloudflare Tunnel Setup – kawaii-san-hub

This guide documents how I set up a persistent Cloudflare Tunnel on my Ubuntu Server to securely expose my local services (like Jellyfin) to the internet, even while behind CGNAT.

No port forwarding. No headaches. Just encrypted tunnels and full control.

---

## 📦 Tools Used

| Tool        | Purpose                                  |
|-------------|------------------------------------------|
| `cloudflared` | CLI for Cloudflare Tunnel              |
| Cloudflare DNS | DNS and SSL management for domain     |
| `systemd`     | Persistent tunnel auto-start at boot   |

---

## 🌐 Your Domain

- **Domain Name:** e.g. `supercooldomainname.com` (bought via [the goat](https://www.cloudflare.com/))
- **Service Subdomain Example:** e.g. `service.domain.com`

---

## 🧱 Directory Structure

```bash
~/
├── .cloudflared/
│   ├── cert.pem
│   ├── config.yml
│   └── <tunnel-id>.json
└── etc/
    └── cloudflared/
        ├── config.yml
        └── <tunnel-id>.json
```

---

## 🚀 Full Setup Steps

### Step 1: Install cloudflaredd
```
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb
sudo cloudflared service install
```

### Step 2: Authenticate with Cloudflare
```
cloudflared tunnel login
```
This opens a browser where you select your domain (e.g. 'supercooldomainname.com').

It stores your cert in ~/.cloudflared/cert.pem.

### Step 3: Create _le_ tunnel
```
cloudflared tunnel create tunnel
```
This generates a tunnel ID and a JSON credentials file in ~/.cloudflared.

### Step 4: Config the config file
Create and edit the config.yml file at:
```
nano ~/.cloudflared/config.yml
```
And paste in the [config.yml](./config.yml) code here.
> Obviosuly don't forget to change the tunnel_ID to your own ID

### Step 5: Move th config file
**cloudflare** is lazy, so we gotta move and copy the config files ourseles.
```
sudo mkdir -p /etc/cloudflared
sudo cp ~/.cloudflared/config.yml /etc/cloudflared/
sudo cp ~/.cloudflared/*.json /etc/cloudflared/
```

### Step 6: Routing baby!
As in route the cloudflare tunnel, we're not routing an actual baby. (Wrong Repo)
```
cloudflared tunnel route dns tunnel service.domain.com
```
This creates a proxied DNS record in your Cloudflare dashboard. Go to your cloudflare dashboard to check!

If you don't wanna use CLI to create tunnels, you can do it in the Cloudflare dashboard itself, but it less fun.
Go to you dash.cloudflare.com > then to your domain > then to DNS and see all Records, for every sercice you have, to each port, you have set a domain name. Use that domain name to create a record.

### Step 7: Enabling
```
sudo systemctl enable cloudflared
sudo systemctl start cloudflared
```
and check with 
```
sudo systemctl status cloudflared
```
---

## ✨Done! Now go to your domain and if it wokrs, you just made a website. Now piss off.
