<p align="center">
  <a href="https://myweirdprompts.com">
    <img src="https://www.myweirdprompts.com/images/mwp-logo.png" alt="My Weird Prompts" width="200" />
  </a>
</p>

<h1 align="center">My Weird Prompts</h1>

<p align="center">
  <strong>An AI-generated podcast where curiosity meets automation.</strong><br/>
  <em>Where Curiosity Meets AI — Stay curious.</em>
</p>

<p align="center">
  <a href="https://myweirdprompts.com">Website</a> ·
  <a href="https://open.spotify.com/show/6egnotAwceSYHZR6AeGgdL">Spotify</a> ·
  <a href="https://podcasts.apple.com/us/podcast/my-weird-prompts/id1868354117">Apple Podcasts</a> ·
  <a href="https://www.youtube.com/playlist?list=PLSi3MqkoIi1ci0oupBivGrJP_0VSzanF4">YouTube</a> ·
  <a href="https://myweirdprompts.com/feed.xml">RSS</a>
</p>

---

My Weird Prompts is a fully automated podcast built on a simple loop: a human records a weird question, an AI pipeline turns it into a complete podcast episode — script, voices, cover art, show notes, and all. No question is too obscure, no rabbit hole too deep.

Daniel Rosehill, a technology communications specialist based in Jerusalem, records short voice memos with whatever question is on his mind. The pipeline he built from scratch takes it from there — transcribing, writing, fact-checking, voicing, assembling, and publishing the episode autonomously.

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

```
Voice memo → Transcription → LLM script generation → AI review →
TTS (Chatterbox) → Audio assembly → Published episode
```

1. **Record** — Daniel records a short voice memo with a question or topic
2. **Transcribe & Plan** — Audio is sent to a webhook, transcribed, and an episode plan is generated
3. **Write & Fact-Check** — An LLM writes the full script, then editing passes review for accuracy and flow
4. **Voice & Assemble** — Each character's lines are voiced using [Chatterbox](https://github.com/resemble-ai/chatterbox) on parallel GPU workers via [Modal](https://modal.com), then assembled into a complete episode
5. **Publish** — Cover art is generated, metadata extracted, and the episode is published everywhere — automatically

## Open Source

| Repository | Description |
|------------|-------------|
| [pipeline](https://github.com/My-Weird-Prompts/pipeline) | Episode generation pipeline — prompt enhancement, script generation, TTS, audio assembly, and publication |

## Tech Stack

- **LLMs** — Multiple models via [OpenRouter](https://openrouter.ai) (script generation, review, metadata)
- **TTS** — [Chatterbox](https://github.com/resemble-ai/chatterbox) with parallel GPU workers and pre-computed voice conditionals
- **GPU Compute** — [Modal](https://modal.com) (serverless GPU infrastructure for TTS)
- **Orchestration** — LangGraph pipeline with multi-agent architecture
- **Database** — Neon (serverless Postgres with pgvector for semantic search)
- **Storage** — Cloudflare R2 (audio, images, transcripts)
- **Frontend** — [Astro](https://astro.build) with interactive topic explorer (Sigma.js), deployed on Vercel
- **Image Generation** — Fal AI (cover art)

## Listen

| Platform | Link |
|----------|------|
| Website | [myweirdprompts.com](https://myweirdprompts.com) |
| Spotify | [open.spotify.com/show/...](https://open.spotify.com/show/6egnotAwceSYHZR6AeGgdL) |
| Apple Podcasts | [podcasts.apple.com/...](https://podcasts.apple.com/us/podcast/my-weird-prompts/id1868354117) |
| YouTube | [youtube.com/playlist/...](https://www.youtube.com/playlist?list=PLSi3MqkoIi1ci0oupBivGrJP_0VSzanF4) |
| RSS Feed | [myweirdprompts.com/feed.xml](https://myweirdprompts.com/feed.xml) |

## Community & Social

| | Platform | Handle |
|---|----------|--------|
| 🦋 | [Bluesky](https://bsky.app/profile/myweirdprompts.bsky.social) | @myweirdprompts.bsky.social |
| ✖️ | [X / Twitter](https://x.com/myweirdprompts) | @myweirdprompts |
| 📸 | [Instagram](https://www.instagram.com/myweirdprompts/) | @myweirdprompts |
| 📣 | [Telegram](https://t.me/myweirdprompts) | @myweirdprompts |
| 💬 | [Discord](https://discord.gg/EYBksT2A8m) | MWP Community |
| 📘 | [Facebook](https://facebook.com/myweirdprompts) | myweirdprompts |
| 🤗 | [Hugging Face](https://huggingface.co/My-Weird-Prompts) | My-Weird-Prompts |

## Links

- **About the show** — [myweirdprompts.com/about](https://myweirdprompts.com/about)
- **Technical white paper** — [myweirdprompts.com/technical](https://myweirdprompts.com/technical)
- **Topic explorer** — [myweirdprompts.com/explore](https://myweirdprompts.com/explore)
- **Created by** — [Daniel Rosehill](https://danielrosehill.com)

---

<p align="center"><em>Stay curious.</em></p>
