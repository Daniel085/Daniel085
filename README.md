# Daniel O'Rorke

**Product Manager | AI Systems Architect | Developer Tools**

I design and operate AI systems hands-on — multi-agent pipelines, agentic workflows, and developer tools that multiply team capability. 10+ years shipping API platforms and developer products; currently building with Claude across everything from PM operating systems to OBD diagnostics to on-device ML.

📍 Boise | 💼 [LinkedIn](https://linkedin.com/in/danielororke) | 📧 daniel@ororke.com

---

## Docs-as-Code — Agentic Engine for OpenAPI → Developer Portals

*Source is private — [live case study: AlianzaDocs](https://github.com/Daniel085/AlianzaDocs)*

A five-loop pipeline that turns a terse OpenAPI spec into a branded developer portal. The core bet: stop trying to fix the LLM — fix the inputs and outputs around it.

**The problem:** LLMs hallucinate when specs are silent. Point a model at an incomplete OpenAPI spec and it invents plausible-sounding sentences for missing fields, undocumented error codes, and unspecified defaults. A reference page that's 95% correct is unusable when you can't tell which 5% is wrong.

**The architecture:** Five event-triggered loops, each owning one transformation. Every LLM call is bracketed by deterministic steps — gap detection before, accuracy review after. Gaps surface as visible admonitions rather than invented prose. Regeneration is scoped to only the pages whose spec dependencies changed, so cost scales with what changed rather than spec size.

| | |
|---|---|
| **Agent roster** | 10 agents across 5 loops; Opus for judgement-critical roles, Sonnet for structured transformations |
| **Cost** | ~$0.65/op cold full run; ~$1.50 for a typical incremental spec change |
| **Tests** | 167 Python test functions, 25 Node tests, WCAG A/AA validated via Playwright + axe-core |
| **Key rule** | No product-specific logic in the engine — every per-product behaviour lives in three config files |

[See it in production: AlianzaDocs →](https://github.com/Daniel085/AlianzaDocs)

---

## Active Projects

### [MCP](https://github.com/Daniel085/MCP)
**Base toolkit for building Model Context Protocol servers**

Parallel TypeScript and Python templates that wrap an existing API and expose it as an MCP server. Ships deployment recipes for Claude Code, Claude Desktop, the Claude API MCP connector, and Docker Compose. Includes a YAML-driven tool-selection eval suite that runs real prompts through the Claude API against any stdio MCP server to confirm the model picks the right tool.

**Tech:** Python, TypeScript, Docker, Claude API | **Updated:** October 2026

---

### [ProductExpert](https://github.com/Daniel085/ProductExpert)
**PM operating system with evaluation harness**

A system of expert sub-agents organised across three phases — Opportunity Discovery, Problem Validation, Solution Validation. Agents cover the full PM workflow: ODI interviewing, outcome editing, survey building, lean experiments, PR/FAQ, experimentation, and metrics. A `/navigate` skill routes initiatives through gated phases; an evaluation harness ships with 30 routing cases and three gate fixtures.

Absorbs and extends [Product-Discovery-ODI](https://github.com/Daniel085/Product-Discovery-ODI) — the ODI agents are now one phase of a bigger system.

**Tech:** Python, Markdown agent definitions | **Updated:** October 2026

---

### [PrettyGoodManAIger](https://github.com/Daniel085/PrettyGoodManAIger)
**Ritualised AI assistant for product and design managers**

Three scheduled daily rituals (`/start`, `/sync`, `/wrap-up`) plus pre-meeting prep commands (`/prep-1on1`, `/prep-boss-1on1`). Loads a manage-up canon (Gabarro & Kotter, Cohen & Bradford, Neffinger & Kohut, Annie Duke) and a decision log, and gets sharper the longer you use it. Core design bet: ritualised capture beats willpower.

**Tech:** Markdown skills | **Updated:** September 2026

---

### [OBD_Battery-diagnostics](https://github.com/Daniel085/OBD_Battery-diagnostics)
**Cross-platform Flutter app for EV/PHEV battery diagnostics**

Connects to a vehicle's OBD-II port via a BLE ELM327 adapter and reads detailed BMS / high-voltage battery data — state of charge, state of health, pack voltage/current, per-cell voltages, module temperatures, cell balancing, cycle count, isolation resistance — then exports a battery health report. Vehicle-specific knowledge lives in JSON signal sets (OBDb v3 schema) rather than code. Primary targets: 2018 BMW 330e and 2025 Cadillac Lyriq. Read-only by design: UDS 0x22/0x19 and J1979 mode 01 only — never writes.

**Tech:** Flutter/Dart, Swift, Kotlin, BLE, UDS/ISO-TP | **Status:** Active, on-vehicle validated | **Tests:** 54 offline tests + demo mode

---

### [Job](https://github.com/Daniel085/Job)
**Claude Code-driven job search pipeline**

Generates a master `Profile.md` from a resume plus LinkedIn export, discovers postings, fit-scores them with a documented algorithm, and produces per-company tailored resumes and cover letters.

**Tech:** HTML resume templates, Claude Code workflows | **Updated:** October 2026

---

## Other Notable Projects

### [dadJokeGenerator](https://github.com/Daniel085/dadJokeGenerator) — [Live Demo](https://daniel085.github.io/dadJokeGenerator/)
Three sources: live API (1000+ jokes), local vault (750+), and an **AI Generated mode** running Qwen2.5-1.5B fine-tuned on dad jokes, served on-device via ONNX Runtime Web (WebGPU, ~1.1GB one-time download). Built as a new-dad warm-up; now a real on-device LLM demo.

**Tech:** Vanilla JS, Python (fine-tune pipeline), ONNX Runtime Web, WebGPU | ✅ Live

---

### [Hearth](https://github.com/Daniel085/Hearth)
Privacy-first iOS relationship assistant using on-device Core ML and Vision. Upgraded from concept to **working prototype** — ~200KB of Swift running on-device. Face clustering and Vision FeaturePrint vs. Core ML face-model tradeoffs documented from real prototype findings.

**Tech:** Swift, SwiftUI, Core ML, Vision, PhotoKit | **Status:** Prototype phase

---

### [iOS-WebRTC-Demo](https://github.com/Daniel085/iOS-WebRTC-Demo)
Native iOS dialer with CallKit, VoIP push, Contacts integration, and a complete Node.js signaling backend. Swift source grew ~40% since May 2026. Ships 14 long-form technical guides.

**Tech:** Swift 5.9+, SwiftUI, GoogleWebRTC, CallKit, PushKit, Node.js, Socket.io, PostgreSQL

---

### [SocialMediaManager](https://github.com/Daniel085/SocialMediaManager)
Local pipeline that turns a folder of dog photos into Instagram-ready captioned content. Stages (ingest → dedupe → filter → caption → review) are independently invokable; state is a hand-editable `queue.json`; captions generated via Claude Sonnet against a persona file. Human-in-the-loop approval before anything publishes.

**Tech:** Python, Click, Flask, Claude API

---

### [WorkdayResumeParser](https://github.com/Daniel085/WorkdayResumeParser)
Chrome extension that parses a resume locally using Chrome's built-in on-device Gemini Nano and auto-fills Workday job applications. No server, no API keys — host permissions limited to `*.myworkdayjobs.com`.

**Tech:** Chrome Manifest V3, JavaScript, Chrome AI (Gemini Nano), PDF.js

---

### [GrocerySelector](https://github.com/Daniel085/GrocerySelector) — [Live Demo](https://daniel085.github.io/GrocerySelector/)
Browser-based 5-day meal planner running Phi-3-mini entirely on-device via WebLLM (WebGPU). Optimises meals for ingredient reuse and exports a Walmart-compatible grocery list. Optional SDXL-Turbo for recipe images, loaded lazily.

**Tech:** React 19, TypeScript, WebGPU, Phi-3-mini, SDXL-Turbo | ✅ Live

---

## Future Projects

### [Hearth](https://github.com/Daniel085/Hearth) — Full iOS App
Prototype is running; next phase is validating face clustering against a real photo library and shipping the communication-rhythm engine.

---

## Background

10+ years building developer tools and API platforms at Vonage (TokBox), SendGrid, VoiceBase, Aerohive Networks, and Charter Communications. Managed SDKs across iOS, Android, Web, Windows, Linux, and HoloLens. Deep background in WebRTC and real-time communications.

$3M revenue captured through API migration automation at Vonage · 60% reduction in integration time at VoiceBase · ISTE "Best in Show" for a WebRTC education app · 2 patents in WiFi credential automation (15/073,593 & 62/350,158)

---

## Contact

📧 daniel@ororke.com | 💼 [linkedin.com/in/danielororke](https://linkedin.com/in/danielororke)

---

*I don't just manage products — I build them.*
