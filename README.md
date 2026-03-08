<div align="center">
  <img src="https://raw.githubusercontent.com/opengraviton/graviton/main/assets/logo.svg" alt="OpenGraviton Master Logo" width="200" />
  <h1>Welcome to OpenGraviton</h1>
  <p><strong>Defying the gravitational pull of massive AI models.</strong></p>
</div>

<br />

### 🌌 Our Mission

At OpenGraviton, we believe that the full power of Artificial Intelligence should not be locked behind massive GPU clusters or specialized hardware. 

We build and maintain **Graviton**—the ultimate open-source inference engine—designed ground-up to compress, prune, and execute trillion-parameter AI models natively on consumer hardware like the Apple Silicon Mac Mini.

### ⚡ Core Technologies Built Here

- 🗜️ **Extreme Quantization (1.58-bit Ternary)**: Squeezing 16-bit weights into `{-1, 0, +1}` for a staggering 10x compression in memory footprint.
- 🔩 **QuantizedLinear**: Drop-in `nn.Linear` replacement — stores weights in packed quantized format. INT8 saves 62% memory with near-zero quality loss; mixed-precision routes critical layers to 8-bit, FFN to 4-bit.
- 💿 **Layer Streaming via MMAP**: Surpassing physical RAM limits by directly memory-mapping neural networks from your NVMe SSD.
- 🧠 **Speculative Decoding**: Self-speculative with layer-skip draft model, plus a pluggable framework for external draft models targeting 2-3x throughput.
- 🎛️ **Dynamic Sparsity**: Firing only the absolute necessary neurons (Top-K) and Routing (MoE) dynamically on the fly.
- 🧪 **88 Tests, Full Coverage**: Every component validated — attention masks, device-aware quantizers, speculative rollback, KV cache fast-path + compressed mode, and end-to-end model inference.
- 🖥️ **[Graviton UI](https://github.com/opengraviton/graviton-ui)**: Beautiful dark-themed chat interface — enter a HuggingFace token + model ID, pick quantization settings, and chat with real-time streaming + live tok/s counter.

### 📊 Proven Results

**Real inference on consumer hardware.** Graviton downloads, quantizes, and runs HuggingFace models with full text generation — no GPU cluster required.

| Metric | TinyLlama-1.1B on M1 Max |
|---|---|
| FP16 Baseline | 2.05 GB, ~18 tok/s |
| INT8 QuantizedLinear | **0.78 GB** (62% smaller), ~19 tok/s |
| Mixed-Precision (8/4) | **0.78 GB**, ~10 tok/s |
| INT4 Packed | **0.24 GB** (8.4x smaller) |
| Ternary (1.58-bit) | **0.24 GB** (8.4x smaller) |
| KV Cache | INT8 compressed, sliding window |
| Test Suite | **88 tests, all passing in ~2s** |

### 🚀 Get Started

Check out our repositories and join the revolution:

[![Graviton Engine](https://github-readme-stats.vercel.app/api/pin/?username=opengraviton&repo=graviton&theme=radical&bg_color=050508&title_color=B882FF&text_color=9CA3AF&icon_color=8A2BE2)](https://github.com/opengraviton/graviton)
[![Graviton UI](https://github-readme-stats.vercel.app/api/pin/?username=opengraviton&repo=graviton-ui&theme=radical&bg_color=050508&title_color=B882FF&text_color=9CA3AF&icon_color=8A2BE2)](https://github.com/opengraviton/graviton-ui)

```bash
# Clone and install
git clone https://github.com/opengraviton/graviton.git
cd graviton
pip install -e ".[all]"

# Check your hardware capabilities
python3 -m graviton.cli.main info

# Run with INT8 quantization (62% memory savings)
python3 -m graviton.cli.main run 'TinyLlama/TinyLlama-1.1B-Chat-v1.0' \
    -p 'Explain quantum computing:' -b 8 --no-mixed

# Run with speculative decoding
python3 -m graviton.cli.main run 'TinyLlama/TinyLlama-1.1B-Chat-v1.0' \
    -p 'Hello world' --speculative --spec-tokens 4

# Run the test suite
pytest tests/ -v   # 88 tests in ~2 seconds

# Or use the Web UI instead of CLI
pip install graviton-ui
graviton-ui          # opens http://localhost:7860
```

**Expected output:**
```
Quantized 154 linear layers, saved 1318 MB in packed storage
Model ready: 0.13B params, 0.78 GB on mps
Quantization: INT8 uniform

Prompt: Explain quantum computing:
--------------------------------------------------
Generation: Quantum computing is an emerging field of computing
that operates using quantum mechanics rather than classical
computing principles...
--------------------------------------------------
Generated 80 tokens in 4.28s (18.7 tok/s)
```

> For gated models (LLaMA, Mixtral, etc.), you'll need a HuggingFace token. See the [Graviton README](https://github.com/opengraviton/graviton#huggingface-setup-for-downloading-models) for setup instructions.

### 🌍 Community

- 📖 **Documentation & Website**: [opengraviton.github.io](https://opengraviton.github.io)
- 🤝 **Contributing**: We welcome all hackers, researchers, and developers. Feel free to open a PR on exactly what you want to optimize next in `graviton`.
- ⚖️ **License**: Everything we build is open-source under the Apache 2.0 license.

---

<p align="center">
  <i>"Gravity pulls us down; OpenGraviton sets AI free."</i>
</p>
