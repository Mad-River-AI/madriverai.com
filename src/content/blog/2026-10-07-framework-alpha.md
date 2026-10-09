---
title: "osint-framework — We open-sourced our investigation core"
date: 2026-10-07
summary: Six modular tools, two production agent specs, and the provenance-tagged runner that ties them together. Here's what shipped and why we built it this way.
tags: ["announcement", "osint", "open-source"]
---

We shipped the first real cut of osint-framework today: a Python framework for orchestrating modular OSINT investigations with provenance baked in.

## What's in it

**Core runner.** A DAG-based task runner that accepts tasks with declared dependencies, resolves them in topological order, and attaches a `ProvenanceRecord` to every output. Token, time, and cost budgets enforced on every run. No unbounded agents.

**Six tools.**

- `web.search` — SearXNG (self-hosted), Brave API, or DuckDuckGo. Every result tagged with source URL, collection timestamp, and method.
- `web.fetch` — plain HTTP or JS-rendered (Playwright), with optional Tor SOCKS5 routing.
- `domain.whois` — TCP WHOIS with LRU cache, TLD-server mapping, privacy detection.
- `domain.dns` — A/AAAA/MX/NS/TXT/CNAME resolution plus subdomain enumeration against a wordlist.
- `domain.certs` — Certificate Transparency log queries via crt.sh. Subdomain discovery from issued certs.
- `domain.tech_detect` — 50+ regex signatures across HTTP headers + HTML. No browser required.

**Two agent specs.**

- `domain-recon` — Given a domain, produces a structured dossier: WHOIS, DNS, CT subdomains, tech stack, typosquat detection, security header grading. Six eval scenarios.
- `company-investigator` — Given a company name and optional seed URL, produces a due diligence dossier: leadership, funding signals, risk indicators, online presence, confidence scores. Five eval scenarios including shell company detection and name disambiguation.

**49 tests. All green.**

## Why we built it this way

Every piece of data carries its source. The `ProvenanceRecord` wraps every tool output — source URL, collection timestamp, collection method. This isn't a logging feature; it's the architecture. You can't build a trustworthy intelligence product on untagged data.

The tools are small. The smallest tool is under 100 lines. The pipelines are explicit. The agents are just pipelines with memory and goal-seeking. You can re-mix the parts, audit any step, and trust the outputs.

Agent specs live in git. A change to a system prompt is a version bump with a diff. Evals are required before merge. This is how you get reproducible, improvable agents.

## What's next

Phase 2 brings the social collection tools — Twitter/X, Reddit, Instagram, TikTok — which emit the TrendSignal schema that feeds *Trend Oracle*, our private enterprise product. [Follow along on GitHub](https://github.com/Mad-River-AI/osint-framework).
