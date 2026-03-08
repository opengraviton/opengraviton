<div align="center">
  <img src="https://raw.githubusercontent.com/opengraviton/graviton/main/assets/logo.svg" alt="OpenGraviton" width="200" />
  <h1>OpenGraviton</h1>
  <p><strong>500B+ parameter LLMs. Locally. On a Mac Mini.</strong></p>
  <p>The most powerful AI shouldn't belong to corporations. We're making it accessible to everyone.</p>
</div>

<br />

## The Mission

AI is being monopolized. The most capable models are locked behind cloud APIs, subscriptions, and corporate gatekeepers. We believe this is the single biggest barrier to the next era of AI.

**Graviton breaks that barrier.** It's an open-source engine that takes the models corporations run on server farms and makes them run on your desk. A 72B model compressed to 36 GB, streamed layer by layer onto a Mac Mini.

## What It Does

| Feature | What You Get |
|---|---|
| **Run 500B+ models locally** | Stream, compress, and run models that were never meant for consumer hardware |
| **Shrink models up to 10x** | 16-bit to 4-bit or 1.58-bit — models become 4–10x smaller |
| **Stream what doesn't fit** | Loads one layer at a time, compresses each — model never has to fit in memory all at once |
| **2–3x faster generation** | Predicts multiple tokens at once, skips unnecessary computation |
| **Your data, your machine** | No cloud. No API keys. No corporate surveillance. Everything local |
| **Built for AI agents** | Headless REST API — agents on low-budget hardware can use 500B+ models programmatically |

## The Numbers

| Scenario | Without Graviton | With Graviton |
|---|---|---|
| **Qwen2.5-72B** | 144 GB — locked in data centers | **36 GB** — runs on your Mac |
| **LLaMA-2-70B** | 140 GB — crashes on consumer hardware | **35 GB** — fits on a laptop |

## Get Started — One Command

**For you** — install and start chatting:

```bash
pip install graviton-ui && graviton-ui
```

Your browser opens. Pick a model. Start chatting. That's it.

**For AI agents** — headless API, no UI:

```bash
pip install "graviton-ai[api]" && graviton-api
```

REST API on `0.0.0.0:7860`. Load models, send messages, get streaming responses.

| Endpoint | Method | What It Does |
|---|---|---|
| `/health` | GET | Check if the server is running |
| `/api/models/load` | POST | Load a model: `{"model_id": "Qwen/Qwen2.5-72B-Instruct", "bits": 4}` |
| `/api/models/status` | GET | Check loading progress |
| `/api/chat` | POST | Send a message, get streaming response |
| `/api/models/cancel` | POST | Cancel an in-progress load |
| `/api/models/unload` | POST | Unload the model and free memory |

### Repositories

[![Graviton Engine](https://github-readme-stats.vercel.app/api/pin/?username=opengraviton&repo=graviton&theme=radical&bg_color=050508&title_color=B882FF&text_color=9CA3AF&icon_color=8A2BE2)](https://github.com/opengraviton/graviton)
[![Graviton UI](https://github-readme-stats.vercel.app/api/pin/?username=opengraviton&repo=graviton-ui&theme=radical&bg_color=050508&title_color=B882FF&text_color=9CA3AF&icon_color=8A2BE2)](https://github.com/opengraviton/graviton-ui)

> For gated models (LLaMA, Mixtral, etc.), you'll need a HuggingFace token. See the [setup guide](https://github.com/opengraviton/graviton#huggingface-setup-for-downloading-models).

## Community

- **Website**: [opengraviton.github.io](https://opengraviton.github.io)
- **Contributing**: PRs welcome. Open a PR on exactly what you want to optimize next.
- **License**: Apache 2.0.

---

<p align="center">
  <em>"The age of AI starts when it reaches everyone's desk — not just the data center."</em>
</p>
