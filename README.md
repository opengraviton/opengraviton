<div align="center">
  <img src="https://raw.githubusercontent.com/opengraviton/graviton/main/assets/logo.svg" alt="OpenGraviton" width="200" />
  <h1>OpenGraviton</h1>
  <p><strong>AI belongs to everyone — not just those who can afford a GPU cluster.</strong></p>
  <p>We build the open-source inference engine that runs 70B+ parameter LLMs on hardware you already own.</p>
</div>

<br />

## The Problem

Today's most capable language models have 70–400 billion parameters. Running them requires GPU servers that cost $10,000–$100,000. That means the most powerful AI is locked behind a paywall, accessible only to well-funded companies and research labs.

**We believe this is the single biggest barrier to the next era of AI.**

## Our Solution

**Graviton** is an inference engine built from the ground up to break that barrier. It combines six technologies — streaming layer-by-layer loading, extreme quantization, QuantizedLinear, speculative decoding, dynamic sparsity, and memory-mapped layer streaming — to run massive models on consumer hardware.

**The result:** A 72B-parameter model that would normally need 144 GB of VRAM loads into **36 GB** on a Mac with 64 GB of unified memory. No GPU cluster. No cloud bill. Just your laptop.

## Core Technologies

| Technology | What It Does |
|---|---|
| **Streaming Layer-by-Layer Loading** | Builds model skeleton on meta device, streams each transformer layer from safetensors shards, quantizes in-flight, frees originals. Peak memory = 1 FP16 layer + all previously quantized layers. |
| **Extreme Quantization (1.58-bit Ternary)** | Collapses 16-bit weights to `{-1, 0, +1}` for 10x compression. Also supports INT4, INT8, and mixed-precision modes. |
| **QuantizedLinear** | Drop-in `nn.Linear` replacement with packed quantized weights. INT8 saves 62% memory with near-zero quality loss. |
| **Speculative Decoding** | Self-speculative with layer-skip draft model. Full model verifies in one forward pass. 2-3x throughput. |
| **Dynamic Sparsity** | Top-K neuron activation and MoE routing. Only fires the neurons that matter — 70%+ compute savings per token. |
| **Layer Streaming via MMAP** | Memory-maps weights from NVMe SSD with async prefetching. Even a 1 TB model runs with 16 GB RAM. |
| **Graviton UI** | Dark-themed [chat interface](https://github.com/opengraviton/graviton-ui) with real-time streaming, live tok/s counter, and layer-by-layer loading progress. |
| **88 Tests, Full Coverage** | Attention masks, quantizer device consistency, speculative rollback, KV cache, streaming loading, end-to-end inference — all passing in ~2 seconds. |

## Proven Results

| Scenario | Before Graviton | After Graviton |
|---|---|---|
| **72B model (Qwen2.5-72B)** | 144 GB FP16 — needs $10K+ GPU server | **36 GB** — runs on 64 GB Mac |
| **TinyLlama-1.1B** | 2.05 GB FP16, ~18 tok/s | **0.78 GB** INT8 (62% smaller), ~19 tok/s |
| **TinyLlama-1.1B** | 2.05 GB FP16 | **0.24 GB** INT4 (8.4x smaller) |
| **KV Cache** | Full FP16 | INT8 compressed, sliding window |
| **Test Suite** | — | 88 tests, all passing in ~2s |

## Get Started — One Command

### For Humans

Install everything and open the chat UI in your browser:

```bash
pip install graviton-ui && graviton-ui
```

That's it. One command installs the engine, quantization stack, HuggingFace integration, and the chat interface. Your browser opens at `http://localhost:7860` — pick a model, choose quantization, and start chatting.

### For AI Agents

No UI, no browser, no unnecessary dependencies. Just the engine and a REST API:

```bash
pip install "graviton-ai[api]" && graviton-api
```

The headless API server starts on `0.0.0.0:7860`. An agent on a low-budget machine can load a 70B+ model via streaming quantization and use it programmatically — no GPU cluster, no cloud bill.

| Endpoint | Method | Description |
|---|---|---|
| `/health` | GET | Liveness check |
| `/api/models/load` | POST | Load a model: `{"model_id": "Qwen/Qwen2.5-72B-Instruct", "bits": 4}` |
| `/api/models/status` | GET | Check loading progress (layer-by-layer status) |
| `/api/chat` | POST | Send a message: `{"message": "Hello", "temperature": 0.7}` (SSE stream) |
| `/api/models/unload` | POST | Unload the current model |

### Repositories

[![Graviton Engine](https://github-readme-stats.vercel.app/api/pin/?username=opengraviton&repo=graviton&theme=radical&bg_color=050508&title_color=B882FF&text_color=9CA3AF&icon_color=8A2BE2)](https://github.com/opengraviton/graviton)
[![Graviton UI](https://github-readme-stats.vercel.app/api/pin/?username=opengraviton&repo=graviton-ui&theme=radical&bg_color=050508&title_color=B882FF&text_color=9CA3AF&icon_color=8A2BE2)](https://github.com/opengraviton/graviton-ui)

> For gated models (LLaMA, Mixtral, etc.), you'll need a HuggingFace token. See the [setup guide](https://github.com/opengraviton/graviton#huggingface-setup-for-downloading-models).

## Community

- **Website & Docs**: [opengraviton.github.io](https://opengraviton.github.io)
- **Contributing**: We welcome all hackers, researchers, and developers. Open a PR on exactly what you want to optimize next.
- **License**: Everything is open-source under Apache 2.0.

---

<p align="center">
  <em>"The age of AI starts when it reaches everyone's desk — not just the data center."</em>
</p>
