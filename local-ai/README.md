# AI Chat bot: It gets lonely in here - kawaii-san.org

I wanna use an AI model, but I am afraid of OpenAI, Microsoft, Google and Deepseek stealing my data.
And more primarily, in my Polytechnic, chatgpt.com is blacklisted. Just why? And why just chatgpt? Anyways, I have the hardware and knowledge to run my own local AI models, so why not right?

## Beep boop says hi 🧠

My PC can't handle the big bois like ChatGPT, Deepseek R1, Claude and other woopity scoop. But it CAN handle smaller Large Language Models (counter-intuitive ahh name) like Mistral. Like a "we have chatgpt at home" but it's actually pretty good. I will not explain **why** I am unable to run more powerful AI. That you will have to do your own research. Probably just chatgpt why I can't use chatgpt (meta af)

So, I will be using:
- Ollama (for AI Models)
- Open WebUI (for web user interface)

This is because Ollama only supports CLI or command-line interface. This is what CLI looks like.

<img width="512" height="384" alt="Linux_command-line _Bash _GNOME_Terminal _screenshot" src="https://github.com/user-attachments/assets/e55801cf-7b87-4a24-98b4-51b95febe9ae" />

Which is pretty cool, I'll admit. But not for today's project.

## Hellow World! 🖥️

First, install Ollama. Ez. just-
```
curl -fsSL https://ollama.com/install.sh | sh
```

That's literally it. That's the hardest part.
Whew. All in good days work... I then tested the download with a "test" model. (wink wink)

```
ollama run mistral
```

This both PULLS and RUNS the model from the Ollama library. It's also the only AI model small enough where my PC doesn't turn into a jet engine when I run it, but also good enough to deserve my attention. (Mortal beings)

## Yellow Squirrel 🐿️

Yellow Squirrel refers to the front-end program I will be running, Open WebUI. It is a lightweight web development where it easily communicates with Ollama, so I don't even have to do anything. All I have to do is just run the service and it will do it all for me while also looking pretty slick.

<img width="1400" height="700" alt="1_e_OETKtrx46jcUUpBXL80w" src="https://github.com/user-attachments/assets/77d482ef-aafd-47c8-8318-8f132c42ad17" />

```
cd ~/docker/ai
git clone https://github.com/open-webui/open-webui.git
cd open-webui
```

Start it up.

```
docker compose up -d
```
And then I set up a cloudflare subdomain cuz it's easy to remember, and I am lazy.

## "Is anyone there?" 

Now I just introduce Open-san and Ollama-kun to each other. Aww. They're so cute together. Anyways...

1. Make an account.
2. Go to Settings > Models
3. It shoudl detect ollama.
4. Go to the ollama models lists and find a model (I will be using deepseek's R1 8b)
5. Do 2 pushups.

## 🎉And that's it!

Now I can pretend I have friends cuz I'm not smart enough to make real ones...
Anyways, ain't this cool asf?

<img width="1659" height="914" alt="image" src="https://github.com/user-attachments/assets/1569ae48-5538-45b3-862e-8eec0d5d8694" />

