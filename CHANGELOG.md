# Changelog

All notable changes to GrayTell will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/).

---

## [0.2.1] - 2025-07-14

### Added
- 30+ AI models across 5 providers (Groq, OpenRouter, Mistral, Ollama Cloud, ZAI)
- Multi-provider routing with unified SSE parser
- Ollama Cloud adapter (NDJSON → SSE transform)
- 12 research tools (web search, page reader, Reddit, X, GitHub, YouTube, LinkedIn, Facebook, Instagram, Threads, Snapchat, site map)
- Agentic tool-calling loop (8 rounds search, 12 rounds deep)
- Real-time research timeline UI
- Streaming markdown answers with citations
- Model selector with provider logos and search
- Model gating system (free vs premium)
- Guest mode with daily usage limits
- Supabase authentication (OAuth + email)
- User memory system (persistent context across conversations)
- Conversation history with Today/Yesterday/Earlier grouping
- Dark / Light / System theme support
- Mobile-responsive design
- Landing page with hero, feature sections, and stats
- MCP (Model Context Protocol) integration endpoints
- Settings page with memory manager

---

## [0.1.0] - 2025-06-01

### Added
- Initial release
- Basic chat interface with Mistral Medium 3.5 as default model
- Single-provider streaming (Mistral API)
- Web search and page reader tools
- Supabase auth integration
- Conversation persistence
- Dark/light theme
- shadcn/ui component library

---

[0.2.1]: https://github.com/graytellai/graytell/releases/tag/v0.2.1
[0.1.0]: https://github.com/graytellai/graytell/releases/tag/v0.1.0
