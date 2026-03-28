# My Weird Prompts

**An AI-generated podcast where curiosity meets automation.**

My Weird Prompts is a show built on a simple loop: a human records a weird question, an AI pipeline turns it into a full podcast episode. No question is too obscure, no rabbit hole too deep.

The cast includes Herman the donkey and Corn the sloth — two AI-voiced characters living in Jerusalem with their creator Daniel Rosehill and his wife Hannah. Episodes are short, curious, and cover everything from Icelandic gas stations to what would happen if every bird disappeared for a day.

## How It Works

```
Voice memo → Transcription → LLM script generation → AI review →
TTS (Chatterbox) → Audio assembly → Published episode
```

The entire pipeline — from raw voice prompt to published episode with cover art, show notes, and transcript — runs autonomously on GPU infrastructure. Episodes cost roughly $0.30–0.50 each to produce.

## Listen

**[myweirdprompts.com](https://myweirdprompts.com)** — website with full episode archive, topic explorer, and playlists.

Also available on [Apple Podcasts](https://podcasts.apple.com/podcast/my-weird-prompts/id1789386280), [Spotify](https://open.spotify.com/show/0B3T2KhxGQy0RnFBIr3fMJ), and most podcast apps.

## Open Source

| Repository | Description |
|------------|-------------|
| [pipeline](https://github.com/My-Weird-Prompts/pipeline) | Episode generation pipeline — prompt enhancement, script generation, TTS, audio assembly, and publication |

## Tech Stack

- **LLMs**: Multiple models via OpenRouter (script generation, review, metadata)
- **TTS**: Chatterbox Regular with parallel GPU workers and pre-computed voice conditionals
- **Infrastructure**: Modal (GPU compute), Neon (Postgres), Cloudflare R2 (storage), Vercel (website)
- **Frontend**: Astro with interactive topic explorer (Sigma.js graph visualization)
- **Orchestration**: LangGraph pipeline with multi-agent architecture

## Links

- **Website**: [myweirdprompts.com](https://myweirdprompts.com)
- **About**: [myweirdprompts.com/about](https://myweirdprompts.com/about)
- **Created by**: [Daniel Rosehill](https://danielrosehill.com)

*Stay curious.*
