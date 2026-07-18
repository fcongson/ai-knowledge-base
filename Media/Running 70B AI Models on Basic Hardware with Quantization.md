---

type: video-summary 
source: https://youtu.be/K75j8MkwgJ0 
channel: Matt Williams 
date: 2026-04-03 
duration: ~10:00 
tags:

- knowledge
- ai
- local-ai
- ollama
- quantization
- llm
- hardware-optimization
- context-management
- flash-attention
- memory-optimization
- self-hosted-ai

---

# Running 70B AI Models on Basic Hardware with Quantization

> A practical explainer on AI model quantization — the technique that makes large language models runnable on consumer hardware. Covers Q2/Q4/Q8 quantization levels, k-quants, and Ollama's newer context quantization feature using Flash Attention and KV cache compression.

<iframe width="560" height="315" src="https://www.youtube.com/embed/K75j8MkwgJ0" frameborder="0" allowfullscreen></iframe>

---

## The Core Problem

AI models store billions of numbers at high precision. A **7B parameter model at full 32-bit precision needs ~28 GB of RAM** — more than most gaming PCs, and requiring a $2,000–$3,000 GPU just to load. Quantization solves this by reducing the numerical precision of those stored values.

> _"I think the biggest mistake that I do — that everyone does — is they try to rush through the context where you just don't have the patience to tell the AI what it actually needs to know to solve your problem."_

---

## Quantization Levels Explained

Think of quantization like choosing different rulers for measurement:

|Level|Analogy|Notes|
|---|---|---|
|**FP32**|Millimetre ruler|Full precision; enormous RAM cost|
|**Q8**|Centimetre ruler|Very close to full quality|
|**Q4**|Marker every 5 cm|Best balance of size and quality; Ollama default|
|**Q2**|Random stick from the yard|Extreme compression; works better than you'd expect|

---

## K-Quants — Smarter Compression

Models tagged with **K** (e.g. `Q4_KM`) use **k-quant** quantization — a more intelligent approach that creates specialised memory zones rather than forcing all values into the same box.

- Small numbers get their own precise area
- Large numbers get appropriately sized space
- **KS / KM / KL** = Small / Medium / Large detail levels

Ollama currently defaults to **Q4_KM** for most models.

---

## Context Quantization — The New Trick

Beyond model weights, your **conversation history (context)** also consumes significant RAM. Modern models supporting 128K+ token contexts make this a real problem.

Two Ollama features address this:

### Flash Attention

```
OLLAMA_FLASH_ATTENTION=true
```

### KV Cache Quantization

```
OLLAMA_KV_CACHE_TYPE=Q8
```

### Demo Results — Qwen 2.5 7B with 32K Context

|Configuration|RAM Used|Context Memory|
|---|---|---|
|32K context, no Flash Attention|~40.9 GB|~15 GB|
|32K context + Flash Attention|~33.7 GB|~7 GB savings|
|32K context + Flash Attention + Q8 KV cache|~30.6 GB|~10 GB savings|
|Default 2K context, no Flash Attention|~30.3 GB|~2 GB|

> ⚠️ Not every model benefits equally — one IBM model actually used _more_ memory with KV cache quantization enabled. Test your specific model.

---

## How to Set Up a Custom Context Size in Ollama

```bash
# Pull the model
ollama pull qwen2.5

# Create a custom modelfile
ollama run qwen2.5
/set parameter num_ctx 32768
/save qwen2.5-max

# Run with Flash Attention
OLLAMA_FLASH_ATTENTION=true ollama serve
```

---

## Practical Recommendation

1. **Start with Q4_KM** — Ollama's default, good balance for most tasks
2. **Enable Flash Attention** and test your use case
3. If quality is poor → move up to **Q8**
4. If quality is fine → try dropping to **Q2** (surprisingly capable)
5. For large contexts → experiment with **Q8 KV cache quantization**

> _"It's amazing how often a Q2 model will work just as well for most tasks for most people — and the memory usage is so much lower."_

---

## Key Takeaways

- **Quantization is the unlock** — it's what makes 70B models run on a laptop
- **Q4_KM is the sweet spot** for most users
- **Context memory is often overlooked** — and now fixable with Flash Attention + KV cache quant
- **Test, don't assume** — results vary by model and use case
- **Q2 is underrated** — worth trying before spending more on hardware

---

## Notable Quotes

> _"Here's what nobody tells you about AI models — they're just giant collections of huge numbers. Billions of them. Each one needs to be stored with incredible precision."_

> _"The best setup isn't about using the highest settings — it's about finding what works for your specific needs."_

---

## Links

- 🤖 **Ollama:** [ollama.com](https://ollama.com/)
- 📺 **Video:** [youtu.be/K75j8MkwgJ0](https://youtu.be/K75j8MkwgJ0)