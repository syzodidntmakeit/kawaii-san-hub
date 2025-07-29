# AI Chat bot - kawaii-san.org

## 🧠 Local LLM with Ollama + Open WebUI
I wanted a chatbot I can run loccaly. And since i have the hardware to perform such heavy task, I will.
- I amd using Ollama as it is the most begineer and CLI (command line interface) friendly while also giving you control. (Like the Linux Mint of AI)
- I will also be using Open WebUI as I like the way it looks, and LM Stuios doesn't a web interface natively.
- And of course we will tunnel it with cloudflare tunnel. Duh

## 🔧 Setup
First, install Ollama.
```
curl -fsSL https://ollama.com/install.sh | sh
```
That's literally it. That's the hardest part.
You can test to see if it works. Or just use your models at CLI level.
```
ollama run mistral
```

## 🖼️ Interface
Now we get Open WebUI. It's basically a fortnite skin from the battlepass. (idk how that works). But basically, somwone else has done the hardwork for you. Just sit back, relax, and pretend it was all you.
```
cd ~/docker/ai
git clone https://github.com/open-webui/open-webui.git
cd open-webui
```
Start it up.
```
docker compose up -d
```
And now it's up. Go see for yourself.
```
http://<your-server-ip>:3000
```
You shoudl see a page like this:

<img width="1400" height="700" alt="1_e_OETKtrx46jcUUpBXL80w" src="https://github.com/user-attachments/assets/77d482ef-aafd-47c8-8318-8f132c42ad17" />

## 👷 Connect Open WebUI to Ollama
Once you've gotten your browser up,
1. Make an account.
2. Go to Settings > Models
3. It shoudl detect ollama.
4. Go to the ollama models lists and find for models that you can run locally and send it in here.
5. Greet it with 3 fire emojis 🔥🔥🔥 It's important (it's not but whatever)

## ☁️ Cloudflare Tunnel Configuration
I am, therefore, I am. So we get cloudflare tunnel
Edit the '/etc/cloudflared/config.yml'
```
  - hostname: ai.domain.com
    service: http://localhost:3000
```
Restart the service:
```
sudo systemctl restart cloudflared
```
Then route the DNS:
```
cloudflared tunnel route dns <tunnel_ID> ai.domain.com
```
## 🎉Congrats!
Now you have your very own AI Chatbot that you can talk about sexually suggestive things to because you can't talk to women. I know you. I don't judge.
