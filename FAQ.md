# Frequently Asked Questions

## General

### What is GrayTell?
GrayTell is an AI research agent. You ask a question, and it autonomously searches the web, reads pages, reasons through sources, and writes a fully cited answer — all streamed live so you can watch the research happen in real-time.

### How is GrayTell different from ChatGPT or Claude?
GrayTell isn't a chatbot — it's a **research agent**. While ChatGPT and Claude generate answers from their training data (or a single web search plugin), GrayTell runs a **multi-step tool-calling loop**: it decides what to search, reads multiple pages, cross-references sources, and builds an answer from live data. You see every step.

### Is GrayTell free?
Yes — many models are free and unlocked. Premium models (GPT-5.6, Claude 5, Gemini 3.7, etc.) are gated. Guest users get a daily message limit without needing an account.

### Can I self-host GrayTell?
The code is open-source (MIT). Self-hosting requires API keys for at least one AI provider. Full enterprise self-hosting documentation is on the roadmap.

---

## Models

### Which model should I use?
**Mistral Medium 3.5** is the default and recommended for most queries — it's fast, has strong reasoning, and supports tool calling. For faster responses, try **Nemotron 3.5 Lightning on Groq**. For open-weight options, try **GPT OSS 120B** or **Nemotron 3 Ultra** on Ollama Cloud.

### Why are some models locked?
Locked models require a paid API key (OpenAI, Anthropic, Google, etc.). They're shown in the list so you know they're available if you add your own key.

### Can I add my own model?
Yes. See the project structure — add your model to `MODEL_OPTIONS` in `src/components/model-options.ts`, add a provider module in `src/lib/`, and add the dispatch branch in `src/app/api/chat/route.ts`.

### What's the difference between Search and Deep mode?
- **Search** — up to 8 rounds of tool calling. Good for straightforward questions.
- **Deep** — up to 12 rounds. The agent does more thorough research, reads more pages, and digs deeper into sources.

---

## Providers

### How many providers does GrayTell support?
Five: **Groq**, **OpenRouter**, **Mistral**, **Ollama Cloud**, and **ZAI**. Each has a dedicated client module that normalizes to a common streaming format.

### What is the Ollama Cloud adapter?
Ollama Cloud uses a native NDJSON endpoint, not OpenAI-compatible SSE. GrayTell includes a real-time transform stream that converts Ollama's format into OpenAI-compatible SSE so the agent loop works identically across all providers.

### Can I use GrayTell without any API key?
No — at least one provider API key is required (Mistral is the default). Guest mode limits messages but still needs a server-side key.

---

## Research Tools

### What tools does the agent have access to?
12 tools: web search, page reader, site map, Reddit, X/Twitter, GitHub, YouTube, LinkedIn, Facebook, Instagram, Threads, and Snapchat search.

### Can the agent search social media?
Yes — it has dedicated tools for Reddit, X, GitHub, YouTube, LinkedIn, Facebook, Instagram, Threads, and Snapchat. The model decides when to use them based on your query.

### How do I know the sources are reliable?
The agent shows you every source it used. Each answer includes inline citations linking back to the original pages. You can verify anything yourself.

---

## Research Papers

### What are the weekly research papers?
**Every week we publish a research paper** covering GrayTell's architecture, benchmark results, novel techniques, and real-world findings from running a multi-provider AI agent. Check the [`papers/`](./papers/) directory.

### Can I contribute a paper?
Yes — if you've done interesting work with GrayTell (benchmarks, extensions, novel architectures), we'd love to feature it. Open a PR to the `papers/` directory.

---

## Technical

### Why NDJSON instead of SSE for the client protocol?
NDJSON (one JSON object per line) is simpler to parse than SSE with `data:` prefixes. Fewer edge cases, easier debugging, and the server sends clean JSON objects the client just reads line-by-line.

### Why is TypeScript strict mode required?
The multi-provider system has complex type intersections. Strict mode catches bugs at compile time that would otherwise cause runtime streaming failures.

### Does GrayTell store my conversations?
Conversations are stored in your browser (Zustand persistence) and optionally in the database if you're signed in. Guest conversations stay local.

### What's the guest daily limit?
Guests get a limited number of messages per day (configurable in `src/lib/guest-limit.ts`). Sign in with Supabase to unlock full access.
