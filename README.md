# Open AI Agents Hub

Open-source, self-hosted alternative to [Poe AI](https://poe.com) — build, host, and chat with AI agents (LLM chat bots, image/video generation agents, and custom tool-using agents) from a single interface, on your own infrastructure.

Poe (by Quora) is a hosted marketplace that puts chat bots and media-generation bots behind one UI. **Open AI Agents Hub** is the self-hosted version: bring your own API keys, create your own agents, run it on your own server, and keep full control of prompts, conversations, and data.

<p align="center">
  <a href="https://github.com/Anil-matcha/awesome-generative-ai-apps">
    <img src="https://img.shields.io/badge/Part%20of-Awesome%20Generative%20AI%20Apps-FFD700?style=for-the-badge&logo=github&logoColor=black" alt="Awesome Generative AI Apps">
  </a>
</p>

> 🎨 **[Explore 50+ more open-source AI apps →](https://github.com/Anil-matcha/awesome-generative-ai-apps)**

## Related Projects

- [Open-Pomelli](https://github.com/SamurAIGPT/Open-Pomelli) — Open-source Pomelli alternative — another self-hosted AI assistant
- [open-character-ai](https://github.com/Anil-matcha/open-character-ai) — Open-source Character.AI alternative with custom AI personas

## Features

- **AI agent marketplace** — create, edit, and publish your own agents with custom prompts, tools, and profiles.
- **Media generation agents** — agents that generate images, video, and audio via pluggable model adapters (OpenAI, Fal, Replicate, and any compatible provider).
- **Multi-model chat agents** — unified interface for OpenAI, Anthropic, Google, Mistral, DeepSeek, xAI, Meta Llama, and any OpenAI-compatible endpoint (including local models via Ollama / vLLM / LM Studio).
- **Multi-agent conversations** — query several agents in the same thread and compare outputs side by side.
- **Group chat** — multiple users and multiple agents in one shared conversation.
- **Bring your own keys** — no subscription, no rate caps beyond the providers you use.
- **Self-hosted** — Docker Compose for one-command deploy; works on a laptop, VPS, or Kubernetes.
- **Open protocol** — agent server API so anyone can host their own agent and plug it in.

## Status

Early work in progress. Contributions welcome.

## Quick start

```bash
git clone https://github.com/Anil-matcha/open-ai-agents-hub.git
cd open-ai-agents-hub
cp .env.example .env   # add your provider API keys
docker compose up -d
```

Then open http://localhost:3000.

## License

MIT
