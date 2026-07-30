# Open AI Agents Hub

Open-source platform for building, browsing, and chatting with AI agents — both LLM chat agents and media generation agents (image, video, audio) — in a single web interface.

Instead of writing custom integration code for every model provider, Open AI Agents Hub gives you an agent library (your own agents, template agents, and featured agents), a chat/generation interface per agent, and a proxy backend so you can run the whole thing on your own infrastructure with your own API key.

<p align="center">
  <a href="https://github.com/Anil-matcha/awesome-generative-ai-apps">
    <img src="https://img.shields.io/badge/Part%20of-Awesome%20Generative%20AI%20Apps-FFD700?style=for-the-badge&logo=github&logoColor=black" alt="Awesome Generative AI Apps">
  </a>
</p>

> 🎨 **[Explore 50+ more open-source AI apps →](https://github.com/Anil-matcha/awesome-generative-ai-apps)**

## Why agents, not just chat

Most "chat with AI" tools stop at text. An **agent** here is a reusable, shareable unit that bundles:

- a system prompt / persona
- a target capability — chat, image generation, video generation, or audio generation
- its own profile page, slug, and conversation history

That means the same interface handles a customer-support chatbot agent and a "turn my photo into anime" image-generation agent, side by side in one library — you're not bolting media generation on as an afterthought.

## Features

- **Agent library** — browse your own agents, ready-made template agents, and featured agents from one screen.
- **Agent builder** — create and edit agents visually (the client uses React Flow for the agent creation/edit canvas) with custom prompts, skills, and profile pages.
- **Chat agents** — multi-turn conversations per agent, with full conversation history stored per agent + conversation ID.
- **Media generation agents** — agents whose "reply" is a generated image, video, or audio clip instead of text.
- **Suggested agents** — an endpoint that recommends agents based on what you're trying to do.
- **Like / profile pages** — each agent has a public-style profile (`/agents/{slug}/profile`) so agents can be discovered and shared inside your instance.
- **Bring your own key** — the backend is a thin FastAPI proxy; you supply the credentials for whichever model/agent provider backs it, so there's no vendor lock-in baked into the UI.
- **Self-hosted** — Next.js frontend + FastAPI backend, run both locally or deploy anywhere that runs Node and Python.

## Architecture

```
client/   Next.js 16 (React 19) app — agent library, agent builder (React Flow), chat + profile pages
server/   FastAPI backend — proxies agent CRUD, chat, and generation requests to your configured provider
packages/agents/  Shared React component library used by the client (agent cards, theming, create/edit UI)
```

The backend (`server/app/routers/agent_proxy.py`) exposes REST endpoints for:

- `GET /api/agents/user/agents`, `/agents/templates/agents`, `/agents/featured/agents` — agent library
- `POST /api/agents` — create an agent
- `GET/PUT /api/agents/by-slug/{slug}` — read/update an agent
- `POST /api/agents/by-slug/{slug}/chat` — chat or generate with an agent
- `POST /api/agents/by-slug/{slug}/like` — like an agent
- `POST /api/agents/suggest` — get suggested agents
- `GET /api/agents/skills` — list available agent skills

These all proxy through to a configurable base URL, so you can point the backend at whichever agent/model provider you want to power generation and chat.

## Tech stack

- **Frontend:** Next.js 16, React 19, Tailwind CSS 4, React Flow
- **Backend:** FastAPI, SQLAlchemy, asyncpg, httpx
- **Monorepo:** npm workspaces (`client`, `server`, `packages/agents`)

## Status

Early work in progress. Contributions welcome — see the routers and client `agents/` pages for the current surface area.

## Quick start

**Backend**
```bash
cd server
pip install -r requirements.txt
cp .env .env.local   # set MUAPI_BASE_URL and your API key
uvicorn app.main:app --reload
```

**Frontend**
```bash
cd client
npm install
npm run dev
```

Then open http://localhost:3000. The API runs on port 8000 by default; the client is configured to talk to it via CORS.

## Related Projects

- [Open-Pomelli](https://github.com/SamurAIGPT/Open-Pomelli) — Open-source Pomelli alternative — self-hosted AI marketing assistant
- [open-character-ai](https://github.com/Anil-matcha/open-character-ai) — Open-source Character.AI alternative with custom AI personas

## License

MIT
