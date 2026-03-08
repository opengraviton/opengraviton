<div align="center">
  <img src="https://raw.githubusercontent.com/opengraviton/graviton/main/assets/logo.svg" alt="OpenGraviton" width="200" />
  <h1>OpenGraviton</h1>
  <p><strong>AI belongs to everyone — not just those who can afford a GPU cluster.</strong></p>
  <p>We build the open-source engine that runs powerful AI models on your own computer.</p>
</div>

<br />

## The Problem

Today's best AI models have 70–400 billion parameters. Running them requires GPU servers that cost $10,000–$100,000. The most powerful AI is locked behind a paywall.

**We believe this is the single biggest barrier to the next era of AI.**

## Our Solution

**Graviton** runs the models that shouldn't fit on your hardware. A 72B model that needs 144 GB? Graviton compresses it to 36 GB and loads it piece by piece. No GPU server. No cloud bill. Just your laptop.

## What It Does

| Feature | What You Get |
|---|---|
| **Run 70B+ models on a laptop** | A 72B model compressed from 144 GB to 36 GB — runs on a Mac with 64 GB RAM |
| **Shrink models up to 10x** | Compresses 16-bit models to 4-bit or even 1.58-bit, making them 4–10x smaller |
| **Stream models that don't fit** | Loads one layer at a time from disk, compresses each, and keeps going — never needs full model in memory |
| **Fast text generation** | Predicts multiple tokens at once and skips unnecessary computation — 2–3x faster output |
| **Your data stays private** | Everything runs locally. No cloud. No API keys. No monthly bill |
| **Built for AI agents too** | Headless REST API — agents on cheap hardware can use 70B+ models programmatically |

## The Numbers

| Scenario | Without Graviton | With Graviton |
|---|---|---|
| **Qwen2.5-72B** | 144 GB — needs $10K+ GPU server | **36 GB** — runs on 64 GB Mac |
| **LLaMA-2-70B** | 140 GB — crashes | **35 GB** — fits on a laptop |

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
