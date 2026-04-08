---

type: video-summary 
source: https://www.youtube.com/watch?v=eehsSUlXZN4 
channel: Jack Roberts 
date: 2026-04-08 
duration: ~12:00 
tags:

- claude-code
- local-llm
- ollama
- gemma
- ai-tools
- open-source
- developer-tools
- privacy

---

# Gemma 4 + Ollama = FREE Claude Code

> Jack Roberts — entrepreneur who built and sold a tech startup to 60,000+ customers and now runs an AI automation business — walks through how to run the Claude Code framework entirely for free and offline by pairing it with Google's newly released Gemma 4 model via Ollama. The video is a practical beginner-friendly setup guide that also explains the philosophical trade-offs between paying for frontier models and running capable open-source alternatives locally.

<iframe width="560" height="315" src="https://www.youtube.com/embed/eehsSUlXZN4" frameborder="0" allowfullscreen></iframe>

---

## Why Run Claude Code Locally at All?

Jack opens with a useful mental model: Claude Code is the _car_ (the framework, the tooling, the plugins), while the underlying AI model is the _engine_. Because the two are separable, you can swap in a different engine — specifically a local open-source model — and still benefit from everything Claude Code provides.

His case for going local rests on ten compounding reasons: complete privacy, zero ongoing cost, no internet dependency, no rate limits, very low latency, full control over the stack, no vendor lock-in, compliance friendliness, always-on availability, and unlimited experimentation. He is careful to note he still considers the Claude Max plan ($200/month) "unbelievably worth it" for serious users, comparing it to having a full-time employee for a fraction of the cost — but for people who want 80% of the performance at 1% of the cost, the local route is a legitimate and increasingly capable option.

---

## What is Gemma 4 and Why Does It Matter?

Gemma 4 is Google's latest open-source model family, built on the same DNA as Gemini. Jack highlights eight things worth knowing about it:

- **Benchmark ranking** — sits third on the Arena AI leaderboard at the time of recording, making it genuinely competitive.
- **Four sizes** — ranging from a 4-billion-parameter version suited to laptops and tablets, through a 26B workstation variant, up to larger configurations. This means almost any device can run _something_.
- **Apache 2.0 licence** — Jack spends meaningful time on this because it's a sharp departure from Google's previous custom licences. The old licence carried vague "harmful use" carve-outs, proprietary clauses Google could update unilaterally, and commercial ambiguity that pushed enterprise teams toward Mistral or Cohere instead. Apache 2.0 removes all of that: use it however you want, modify it, redistribute the weights, sell access, fine-tune and ship — no hidden restrictions.
- **Reasoning encoding built in** — the model has native chain-of-thought capability.
- **256k context window** — not as large as Claude Opus 4.6's million-token window, but a significant step up from last year's norms.
- **Native multimodality** — it can process images as well as text, directly in the local Ollama interface.
- **100% private** — nothing leaves the device.

### Trade-offs vs Claude Opus 4.6

Jack lays out the honest comparison. On raw intelligence benchmarks, Gemma 4 scores around 85% compared to Opus 4.6's 90.5. It loses ground on complex multi-step reasoning, sustained reasoning chains, instructional precision, context quality at scale, and tool-use sophistication. What it gains is everything in the local-first column: zero cost forever, total privacy, no rate limits, no outages, and full offline operation. His recommended mental split: use Gemma 4 for the roughly 80% of tasks that don't require frontier-level reasoning, and reach for Claude for the hard 20% — "we wouldn't ask Albert Einstein to mop floors."

---

## Setting Up Ollama

Ollama is the runtime that makes running open-source models locally almost trivially easy. The setup process Jack demonstrates has just a few steps.

First, visit **ollama.com** and download the application for your operating system (Mac or Windows). On Mac, this is a drag-and-drop install — you drop the "Happy Llama" icon into your Applications folder, open it, and sign in or create an account.

Once Ollama is running, it exposes a library of downloadable models. If you're unsure which Gemma 4 size to install, Jack's recommended approach is to take a screenshot of your "About This Mac" (or equivalent system info on Windows), open a Claude session in the terminal (Warp/iTerm), paste the screenshot, and ask: _"I would like to run Gemma 4, the brand new model by Google, based on the specifications of this desktop. Which model would you recommend?"_ Claude will read your hardware specs and recommend the appropriate size.

To actually pull the model, open a terminal and run:

```
ollama pull gemma4:e4b
```

The command fetches the manifest and downloads the model weights. Once complete, the model appears in the Ollama app interface and you can query it directly there — Jack demonstrates a live multimodal example, pasting a screenshot into the chat and asking what the image shows, which Gemma 4 answers correctly entirely on-device.

---

## Running Claude Code with a Local Model

With Gemma 4 running in Ollama, the final step is pointing Claude Code at it instead of the Anthropic API. Jack uses the following launch pattern in his terminal (Warp):

```
ollama run claude gemma4:e4b
```

He notes a practical prerequisite: you still need an Anthropic API key with a small balance (roughly $5–10) loaded at **console.anthropic.com**. The local model handles all actual inference and you won't be billed for it — the key is needed only to satisfy the Claude Code authentication layer. Go to **platform.anthropic.com**, sign in, deposit the minimum amount, and copy your key.

Once inside the Claude Code session, everything works as normal — plan mode, edit approval, session-wide edit acceptance. Jack demonstrates by prompting it to create a `hello.html` file with a centred "Hello World" heading on a dark background, then asking it to open the result in localhost. It executes both steps successfully. The model is slower than Opus 4.6 and the smaller E4B variant occasionally needs more coaxing, but the workflow is functionally identical.

His closing framing: installing a larger model (27B or above) on a capable machine gets you meaningfully closer to frontier performance, and the entire stack works with no internet — on a plane, in a remote location, or anywhere connectivity is unreliable.

---

## Key Takeaways

- **The Claude Code framework is model-agnostic** — you can substitute any compatible local model for the Anthropic-hosted one, keeping all tooling and workflows intact.
- **Apache 2.0 licensing is a genuine unlock for enterprises** — it removes the commercial ambiguity that made earlier Google model licences a liability for production use.
- **Ollama makes local model deployment beginner-friendly** — the entire download-and-run process takes minutes and requires no ML infrastructure knowledge.
- **Size matters more than people think** — the smallest Gemma 4 variant (E4B) works but is noticeably weaker; go as large as your hardware allows.
- **A small Anthropic API balance is still required** — the local setup doesn't eliminate the API key requirement; it just means you won't consume tokens or incur meaningful cost.
- **The 80/20 rule applies cleanly here** — routine coding, scaffolding, and file manipulation tasks are well within Gemma 4's capability; reserve Claude Opus for genuinely complex multi-step reasoning.
- **Multimodality works locally** — Gemma 4's image understanding runs entirely on-device, enabling screenshot-to-analysis workflows without any data leaving the machine.

---

## Notable Quotes

> "It is like the equivalent of having a 50k salary person for $200 a month. It's incredible."

— **Jack Roberts** (~[02:10](https://www.youtube.com/watch?v=eehsSUlXZN4&t=130))

> "You may be of the view: Jack, I will be happy with 80% of the performance for 1% of the cost. That might be a trade-off you personally like to make."

— **Jack Roberts** (~[02:45](https://www.youtube.com/watch?v=eehsSUlXZN4&t=165))

> "We wouldn't ask Albert Einstein to mop the floors. He might be best served on a whiteboard figuring out maths equations and physics questions."

— **Jack Roberts** (~[07:30](https://www.youtube.com/watch?v=eehsSUlXZN4&t=450))

> "Whether we are flying overseas and there's no internet, or we're deep in the bunker — we can have these conversations now about anything that we want to."

— **Jack Roberts** (~[10:00](https://www.youtube.com/watch?v=eehsSUlXZN4&t=600))

---

## Chapters

|Time|Topic|
|---|---|
|~00:00|Introduction — the pitch for free, private, local AI coding|
|~01:30|The car vs engine analogy — Claude Code framework explained|
|~02:00|Trade-offs: when to pay for Claude Max vs going local|
|~03:00|Gemma 4 overview — what it is and why it matters|
|~04:00|Apache 2.0 licence deep-dive — old vs new licensing compared|
|~05:30|Gemma 4 vs Claude Opus 4.6 — benchmark comparison|
|~06:30|Downloading and installing Ollama|
|~08:00|Choosing the right Gemma 4 model size for your hardware|
|~09:00|Pulling Gemma 4 via terminal and testing multimodal queries|
|~10:30|Connecting Gemma 4 to Claude Code — full local setup|
|~11:30|Live demo — creating and serving a Hello World HTML file|

---

## Resources

- [Ollama](https://ollama.com/) — desktop app for downloading and running open-source LLMs locally on Mac and Windows
- [Anthropic Console](https://console.anthropic.com/) — where to create an API key and load a small balance (required for Claude Code auth even in local mode)
- [Anthropic Platform](https://platform.anthropic.com/) — sign-in and account management for API access