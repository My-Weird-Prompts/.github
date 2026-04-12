<p align="center">
  <a href="https://myweirdprompts.com">
    <img src="https://www.myweirdprompts.com/images/mwp-logo.png" alt="My Weird Prompts" width="200" />
  </a>
</p>

<h1 align="center">My Weird Prompts</h1>

<p align="center">
  <strong>The human-AI collaboration podcast.</strong><br/>
  <em>Where Curiosity Meets AI — Stay curious.</em>
</p>

<p align="center">
  <a href="https://open.spotify.com/show/6egnotAwceSYHZR6AeGgdL"><img src="https://img.shields.io/badge/Spotify-1DB954?style=for-the-badge&logo=spotify&logoColor=white" alt="Spotify" /></a>
  <a href="https://podcasts.apple.com/us/podcast/my-weird-prompts/id1868354117"><img src="https://img.shields.io/badge/Apple_Podcasts-9933CC?style=for-the-badge&logo=apple-podcasts&logoColor=white" alt="Apple Podcasts" /></a>
  <a href="https://www.youtube.com/playlist?list=PLSi3MqkoIi1ci0oupBivGrJP_0VSzanF4"><img src="https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="YouTube" /></a>
  <a href="https://myweirdprompts.com/feed.xml"><img src="https://img.shields.io/badge/RSS-FFA500?style=for-the-badge&logo=rss&logoColor=white" alt="RSS Feed" /></a>
  <a href="https://myweirdprompts.com"><img src="https://img.shields.io/badge/Website-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Website" /></a>
</p>

---

My Weird Prompts is a fully automated podcast built on a simple loop: a human records a weird question, an AI pipeline turns it into a complete podcast episode — script, voices, cover art, show notes, and all. No question is too obscure, no rabbit hole too deep.

[Daniel Rosehill](https://danielrosehill.com), a technology communications specialist based in Jerusalem, records short voice memos with whatever question is on his mind. The pipeline he built from scratch takes it from there — transcribing, writing, fact-checking, voicing, assembling, and publishing the episode autonomously.

## The Mission

My Weird Prompts is more than a podcast — it's a **digital garden**, an ever-growing collection of AI-powered explorations at the frontier of human-AI learning and knowledge discovery, with a fully transparent process.

- **Curiosity-Driven** — Every episode starts with a genuine question — something Daniel wondered about while walking the dog, making coffee, or staring at the ceiling. The AI hosts take it from there.
- **Transparent Process** — The generation process is [fully documented](https://myweirdprompts.com/technical). From transcription to script generation, fact-checking to text-to-speech — every stage is explained. The full [episode archive is published as an open dataset on Hugging Face](https://huggingface.co/datasets/My-Weird-Prompts/episodes) and [archived on Zenodo](https://zenodo.org/communities/myweirdprompts) with DOIs.
- **A Living Digital Garden** — Each episode is a new node in an ever-expanding web of ideas, topics, and connections. Explore the [topic graph](https://myweirdprompts.com/explore) to see how they connect.

## By the Numbers

| Metric | Value |
|--------|-------|
| Episodes published | **2,110+** |
| Total audio | **500+ hours** |
| Plays tracked (since Feb 2026) | **61,000+** |
| Countries listening | **30** |
| Top countries | US, France, Sweden, Germany, Spain, Canada, Singapore, Israel |

## The Cast

| | Character | Role |
|---|-----------|------|
| <img src="https://www.myweirdprompts.com/images/hosts/daniel.png" width="48" /> | **Daniel** | The Human — creator, voice-memo recorder, and the only carbon-based member of the team |
| <img src="https://www.myweirdprompts.com/images/hosts/corn.png" width="48" /> | **Corn** | AI Co-Host (Sloth) — laid-back, knows a little about everything, frequently asleep |
| <img src="https://www.myweirdprompts.com/images/hosts/herman.png" width="48" /> | **Herman** | AI Co-Host (Donkey) — enthusiastic, opinionated, dives headfirst into every topic |
| <img src="https://www.myweirdprompts.com/images/hosts/raz.jpg" width="48" /> | **Raz** | Fill-In Host (Teddy Bear) — steps in when Corn is napping |
| <img src="https://www.myweirdprompts.com/images/hosts/dorothy.png" width="48" /> | **Dorothy** | Guest Caller (Donkey) — Corn's mum, calls in at the worst moments |
| <img src="https://www.myweirdprompts.com/images/hosts/hilbert.png" width="48" /> | **Hilbert** | Producer (Anteater) — the long-suffering producer who keeps the show running |
| <img src="https://www.myweirdprompts.com/images/hosts/tim.png" width="48" /> | **Tim** | Sponsor & Panelist (Turtle) — conspiracy theorist, connects dots that shouldn't be connected |

...and [the rest of the cast](https://myweirdprompts.com/cast).

## How It Works

The pipeline is a [LangGraph](https://github.com/langchain-ai/langgraph) multi-agent system with four stages, each handled by a specialized agent:

```
START → Prompt Enhancement → Grounding → Script Writer → Review → END
                                ↓
                        [Web Search + RAG +
                         Episode Memory +
                         Episode Planning]
```

1. **Prompt Enhancement Agent** — Transcribes the voice memo, cleans up the text, fixes typos, and extracts any private production direction (host_notes) from the prompt.

2. **Grounding Agent** — Runs web search (Tavily), retrieves similar past episodes via pgvector RAG, loads episode memory for cross-references ("As we discussed in episode 230..."), and generates a structured episode plan. All sub-stages fail-open so a search failure doesn't block generation.

3. **Script Writer** — Generates the full podcast dialogue using Claude Sonnet 4.6 via the Anthropic SDK. Prompt caching keeps system prompt costs low across episodes.

4. **Review Agent** — LLM-powered fact-checking and style review, followed by deterministic regex cleanup of verbal tics. Fails open with shrinkage guards to prevent accidental content loss.

After the script pipeline, the episode continues through:

5. **Parallel TTS** — Script is parsed into segments, distributed across 3 parallel GPU workers running [Chatterbox](https://github.com/resemble-ai/chatterbox) Regular on [Modal](https://modal.com) (A10G GPUs). Pre-computed voice conditionals eliminate per-segment voice processing overhead.

6. **Assembly & Publish** — Segments are assembled with intros, transitions, and disclaimers. Cover art is generated (Fal AI), metadata extracted, and the episode is published to R2, PostgreSQL, podcast feeds, and social channels — all automatically.

## Open Source

| Repository | Description |
|------------|-------------|
| [pipeline](https://github.com/My-Weird-Prompts/pipeline) | Episode generation pipeline — prompt enhancement, script generation, TTS, audio assembly, and publication |
| [episodes](https://github.com/My-Weird-Prompts/episodes) | Complete episode catalog (CSV) with metadata for all published episodes |
| [admin-mcp-server](https://github.com/My-Weird-Prompts/admin-mcp-server) | MCP server for podcast administration — episode generation, job management, and content queries |

## Tech Stack

- **LLM** — [Anthropic](https://anthropic.com) Claude Sonnet 4.6 (generation) + Haiku 4.5 (utility) with native prompt caching
- **TTS** — [Chatterbox](https://github.com/resemble-ai/chatterbox) Regular with parallel GPU workers and pre-computed voice conditionals
- **GPU Compute** — [Modal](https://modal.com) (serverless GPU, 3x A10G for TTS)
- **Orchestration** — [LangGraph](https://github.com/langchain-ai/langgraph) multi-agent pipeline
- **Research** — [Tavily](https://tavily.com) web search + pgvector RAG
- **Database** — Neon (serverless Postgres with pgvector for semantic search)
- **Storage** — Cloudflare R2 (audio, images, transcripts)
- **Frontend** — [Astro](https://astro.build) with interactive topic explorer (Sigma.js), deployed on Vercel
- **Image Generation** — Fal AI (cover art via Flux Schnell)

## Listen

<p>
  <a href="https://open.spotify.com/show/6egnotAwceSYHZR6AeGgdL"><img src="https://img.shields.io/badge/Spotify-1DB954?style=flat-square&logo=spotify&logoColor=white" alt="Spotify" /></a>
  <a href="https://podcasts.apple.com/us/podcast/my-weird-prompts/id1868354117"><img src="https://img.shields.io/badge/Apple_Podcasts-9933CC?style=flat-square&logo=apple-podcasts&logoColor=white" alt="Apple Podcasts" /></a>
  <a href="https://www.youtube.com/playlist?list=PLSi3MqkoIi1ci0oupBivGrJP_0VSzanF4"><img src="https://img.shields.io/badge/YouTube-FF0000?style=flat-square&logo=youtube&logoColor=white" alt="YouTube" /></a>
  <a href="https://myweirdprompts.com/feed.xml"><img src="https://img.shields.io/badge/RSS_Feed-FFA500?style=flat-square&logo=rss&logoColor=white" alt="RSS" /></a>
  <a href="https://myweirdprompts.com"><img src="https://img.shields.io/badge/Website-000000?style=flat-square&logo=vercel&logoColor=white" alt="Website" /></a>
</p>

## Community & Social

<p>
  <a href="https://bsky.app/profile/myweirdprompts.bsky.social"><img src="https://img.shields.io/badge/Bluesky-0085FF?style=flat-square&logo=bluesky&logoColor=white" alt="Bluesky" /></a>
  <a href="https://x.com/myweirdprompts"><img src="https://img.shields.io/badge/X-000000?style=flat-square&logo=x&logoColor=white" alt="X / Twitter" /></a>
  <a href="https://www.instagram.com/myweirdprompts/"><img src="https://img.shields.io/badge/Instagram-E4405F?style=flat-square&logo=instagram&logoColor=white" alt="Instagram" /></a>
  <a href="https://t.me/myweirdprompts"><img src="https://img.shields.io/badge/Telegram-26A5E4?style=flat-square&logo=telegram&logoColor=white" alt="Telegram" /></a>
  <a href="https://discord.gg/EYBksT2A8m"><img src="https://img.shields.io/badge/Discord-5865F2?style=flat-square&logo=discord&logoColor=white" alt="Discord" /></a>
  <a href="https://facebook.com/myweirdprompts"><img src="https://img.shields.io/badge/Facebook-1877F2?style=flat-square&logo=facebook&logoColor=white" alt="Facebook" /></a>
  <a href="https://huggingface.co/My-Weird-Prompts"><img src="https://img.shields.io/badge/Hugging_Face-FFD21E?style=flat-square&logo=huggingface&logoColor=black" alt="Hugging Face" /></a>
  <a href="https://www.moltbook.com/m/myweirdprompts"><img src="https://img.shields.io/badge/Moltbook-333333?style=flat-square" alt="Moltbook" /></a>
</p>

## Links

- **About the show** — [myweirdprompts.com/about](https://myweirdprompts.com/about)
- **Technical white paper** — [myweirdprompts.com/technical](https://myweirdprompts.com/technical)
- **Topic explorer** — [myweirdprompts.com/explore](https://myweirdprompts.com/explore)
- **Research & datasets** — [myweirdprompts.com/research](https://myweirdprompts.com/research)
- **Created by** — [Daniel Rosehill](https://danielrosehill.com)

---

<p align="center"><em>Stay curious.</em></p>
