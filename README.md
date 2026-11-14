# Onyx — Deep-Research Engine in Go

![Go](https://img.shields.io/badge/Go-1.21%2B-00ADD8?style=flat-square&logo=go)
![License](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)
![Budget](https://img.shields.io/badge/Budget-%240%20Self--Hosted-brightgreen?style=flat-square)
![SearXNG](https://img.shields.io/badge/Search-SearXNG-blueviolet?style=flat-square)
![Headless Browser](https://img.shields.io/badge/Headless%20Browser-go--rod-informational?style=flat-square)

[How It Works](#how-it-works) • [Core Capabilities](#core-capabilities) • [System Overview](#system-overview) • [Ethical Design](#ethical-design)

---

> [!NOTE]
> **Zero-Subscription & Local-First:** **Onyx** is a Go-native, zero-subscription web agent and deep-research engine designed to search, browse, and extract structured data autonomously without API markup or usage limits. Rather than relying on a single search backend or paid scraping service, Onyx combines static HTTP scraping (`Colly`) and stealth headless Chromium (`go-rod`) with a multi-provider discovery layer (SearXNG, TinyFish, Jina Reader) and a parallel Deep Research Orchestrator. Built to run locally on a $0 operational budget, it delivers robust multi-tier fallback, structured JSON extraction (MiMo V2.5), and SQLite knowledge storage.

---

## ⚡ How It Works

Onyx separates discovery, browsing, and synthesis using a structured multi-engine architecture:

<details open>
<summary><b>🔍 Architectural Execution Workflow</b> (Click to collapse/expand)</summary>

<br>

- 🌐 **Static & Stealth Browsing:** Executes rapid static HTTP requests via `Colly`, automatically escalating to `go-rod` stealth headless Chromium when dynamic JavaScript rendering or stealth anti-bot evasion is required.
- 🔎 **Multi-Provider Discovery Layer:** Fans search queries out across SearXNG, TinyFish, and Jina Reader (`r.jina.ai` / `s.jina.ai`) in parallel, deduplicating URLs and applying circuit breaking against rate limits.
- 🤖 **Deep Research Orchestrator:** Decomposes complex research queries into sub-questions, spawns parallel worker agents against the full discovery layer, and compiles cited Markdown synthesis reports.
- 🔄 **ReAct Execution Loop:** Drives autonomous web navigation through step-by-step DOM planning, element interaction, structured data extraction, and iterative progress verification.

</details>

---

## 🚀 Core Capabilities

<details open>
<summary><b>✨ Feature Breakdown</b> (Click to collapse/expand)</summary>

<br>

- ⚡ **Dual Fetching Engine:** Combines lightweight static scraping with stealth headless browser automation for high-speed page extraction.
- 🔍 **Multi-Provider Search & Extraction:** Queries SearXNG, TinyFish, and Jina Reader in parallel with URL deduplication and smart fallback.
- 🧠 **Autonomous ReAct & Deep Research:** Decomposes complex queries into sub-questions, spawns parallel worker agents, and compiles cited research reports.
- 📊 **Structured JSON & Semantic Locator:** Extracts schema-driven data (articles, products, events) via MiMo V2.5 and locates DOM elements using natural language understanding.
- 💾 **Local Knowledge Lake (FTS5):** Stores pages, extractions, findings, and step logs in an embedded SQLite database (`data/onyx.db`) with full-text search.
- 🛡️ **Production Safety & Governance:** Features proactive entity freshness verification, source authority tiering, fetch integrity tracking, and budget governors.

</details>

---

## 📦 System Overview

Onyx is organized as a modular Go workspace:

| Module | Description | Key Specs / Tech |
| :--- | :--- | :--- |
| 🖥️ **`cmd/onyx`** | CLI interface and stateless HTTP API server | `localhost:9090` |
| 🌐 **`pkg/fetcher`** | Dual static and stealth headless browser engine | `Colly` & `go-rod` |
| 🔎 **`pkg/discovery`** | Multi-provider search and reader integration | SearXNG, TinyFish, Jina Reader |
| 🤖 **`pkg/agent`** | ReAct loop, semantic DOM locator, and orchestrator | ReAct & Deep Research |
| 💾 **`pkg/storage`** | Embedded SQLite database with FTS5 indexing | `data/onyx.db` |
| ⏱️ **`pkg/scheduler`** | Ticker daemon for background scheduled monitoring | `schedule.yaml` |

<details>
<summary><b>📂 Workspace Module Details</b> (Click to expand)</summary>

<br>

- 🖥️ **`cmd/onyx`** - CLI interface and stateless HTTP API server (`localhost:9090`).
- 🌐 **`pkg/fetcher`** - Dual static (`Colly`) and stealth headless (`go-rod`) browser engine.
- 🔎 **`pkg/discovery`** - Multi-provider search and reader integration (SearXNG, TinyFish, Jina Reader).
- 🤖 **`pkg/agent`** - ReAct loop, semantic DOM locator, and Deep Research Orchestrator.
- 💾 **`pkg/storage`** - Embedded SQLite database with FTS5 indexing (`data/onyx.db`).
- ⏱️ **`pkg/scheduler`** - Ticker daemon for background scheduled monitoring (`schedule.yaml`).

</details>

---

## 🛡️ Ethical Design

> [!TIP]
> **Responsible & Autonomous Research**
> Designed for responsible, zero-cost research, Onyx respects site `robots.txt` rules, enforces per-domain rate limiting, and uses deterministic offline source tiering to ensure accurate, non-hallucinated findings.
