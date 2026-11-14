# Onyx — A Zero-Subscription Web Agent & Deep-Research Engine in Go

**Onyx** is a Go-native, zero-subscription web agent and deep-research engine designed to search, browse, and extract structured data autonomously without API markup or usage limits. Rather than relying on a single search backend or paid scraping service, Onyx combines static HTTP scraping (`Colly`) and stealth headless Chromium (`go-rod`) with a multi-provider discovery layer (SearXNG, TinyFish, Jina Reader) and a parallel Deep Research Orchestrator. Built to run locally on a $0 operational budget, it delivers robust multi-tier fallback, structured JSON extraction (MiMo V2.5), and SQLite knowledge storage.

## How It Works

Onyx separates discovery, browsing, and synthesis using a structured multi-engine architecture:

- **Static & Stealth Browsing:** Executes rapid static HTTP requests via `Colly`, automatically escalating to `go-rod` stealth headless Chromium when dynamic JavaScript rendering or stealth anti-bot evasion is required.
- **Multi-Provider Discovery Layer:** Fans search queries out across SearXNG, TinyFish, and Jina Reader (`r.jina.ai` / `s.jina.ai`) in parallel, deduplicating URLs and applying circuit breaking against rate limits.
- **Deep Research Orchestrator:** Decomposes complex research queries into sub-questions, spawns parallel worker agents against the full discovery layer, and compiles cited Markdown synthesis reports.
- **ReAct Execution Loop:** Drives autonomous web navigation through step-by-step DOM planning, element interaction, structured data extraction, and iterative progress verification.

## Core Capabilities

- **Dual Fetching Engine:** Combines lightweight static scraping with stealth headless browser automation for high-speed page extraction.
- **Multi-Provider Search & Extraction:** Queries SearXNG, TinyFish, and Jina Reader in parallel with URL deduplication and smart fallback.
- **Autonomous ReAct & Deep Research:** Decomposes complex queries into sub-questions, spawns parallel worker agents, and compiles cited research reports.
- **Structured JSON & Semantic Locator:** Extracts schema-driven data (articles, products, events) via MiMo V2.5 and locates DOM elements using natural language understanding.
- **Local Knowledge Lake (FTS5):** Stores pages, extractions, findings, and step logs in an embedded SQLite database (`data/onyx.db`) with full-text search.
- **Production Safety & Governance:** Features proactive entity freshness verification, source authority tiering, fetch integrity tracking, and budget governors.

## System Overview

Onyx is organized as a modular Go workspace:

- **`cmd/onyx`** - CLI interface and stateless HTTP API server (`localhost:9090`).
- **`pkg/fetcher`** - Dual static (`Colly`) and stealth headless (`go-rod`) browser engine.
- **`pkg/discovery`** - Multi-provider search and reader integration (SearXNG, TinyFish, Jina Reader).
- **`pkg/agent`** - ReAct loop, semantic DOM locator, and Deep Research Orchestrator.
- **`pkg/storage`** - Embedded SQLite database with FTS5 indexing (`data/onyx.db`).
- **`pkg/scheduler`** - Ticker daemon for background scheduled monitoring (`schedule.yaml`).

## Ethical Design

Designed for responsible, zero-cost research, Onyx respects site `robots.txt` rules, enforces per-domain rate limiting, and uses deterministic offline source tiering to ensure accurate, non-hallucinated findings.
