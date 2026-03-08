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
- 💿 **Layer Streaming via MMAP**: Surpassing physical RAM limits by directly memory-mapping neural networks from your NVMe SSD.
- 🧠 **Speculative Decoding**: Shattering autoregressive memory-bandwidth bottlenecks by verifying parallel predictions on a target model.
- 🎛️ **Dynamic Sparsity**: Firing only the absolute necessary neurons (Top-K) and Routing (MoE) dynamically on the fly.

### 📊 Proven Compression (v0.1.0)
In our latest benchmarks on Apple Silicon, **Graviton routinely achieves 8.4x memory reduction** without significant quality degradation.
For example, **TinyLlama-1.1B** footprint drops from `2.05 GB` down to just `0.24 GB` under 1.58-bit Ternary mode, mapping instantly via SSD MMAP.

### 🚀 Get Started

Check out our flagship engine repository and join the revolution:

[![Graviton Engine](https://github-readme-stats.vercel.app/api/pin/?username=opengraviton&repo=graviton&theme=radical&bg_color=050508&title_color=B882FF&text_color=9CA3AF&icon_color=8A2BE2)](https://github.com/opengraviton/graviton)

```bash
# Clone and install
git clone https://github.com/opengraviton/graviton.git
cd graviton
pip install -e ".[all]"

# Check your hardware capabilities
python3 -m graviton.cli.main info

# Run a small open model to test
python3 -m graviton.cli.main run "TinyLlama/TinyLlama-1.1B-Chat-v1.0" -p "Explain quantum gravity"
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
