# SEO / AEO / GEO Skill Repo

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Claude Code Skill](https://img.shields.io/badge/Claude%20Code-Skill-blue)](SKILL.md)
[![Format](https://img.shields.io/badge/format-Markdown%20Skill-lightgrey)](SKILL.md)

Detailed, tool-agnostic SEO skill set for AI agents (and humans) — traditional search SEO plus **AEO (Answer Engine Optimization)** and **GEO (Generative Engine Optimization)** for getting cited by AI chat assistants, AI Overviews, and agentic research tools.

Everything here is **generic and industry-agnostic** — no company names, no specific URLs, no proprietary client data. It's written so any AI agent, on any website, in any industry, can pick it up and execute correctly with zero prior context.

## Table of Contents

- [Install as a Claude Code Skill](#install-as-a-claude-code-skill)
- [Contents](#contents)
- [How to use this repo as an AI agent skill](#how-to-use-this-repo-as-an-ai-agent-skill)
- [Scope and limitations](#scope-and-limitations)
- [Methodology](#methodology)
- [Contributing](#contributing)

## Install as a Claude Code Skill

```bash
git clone https://github.com/virajsutar-marketer/seo.git ~/.claude/skills/seo
```

Restart Claude Code. The skill is discovered automatically via `SKILL.md` and invoked whenever a task matches its description (SEO audits, keyword research, AEO/GEO optimization). No plugin marketplace, no install script, no dependencies — it's pure markdown, so there's nothing to break and nothing to run.

## Contents

| File | What it's for |
|---|---|
| [`SKILL.md`](./SKILL.md) | The Claude Code Skill manifest — what triggers this skill and the process to follow. Start here if you're an agent. |
| [`SEO-PLAYBOOK.md`](./SEO-PLAYBOOK.md) | The core 21-section operating manual: keyword research, competitor gap analysis, topical authority/pSEO, on-page standards, AEO/GEO fundamentals, E-E-A-T, internal linking, technical SEO (indexing, Core Web Vitals, CMS gotchas, consent, instant indexing), analytics hygiene, root-cause analysis, link building, program structuring, publishing QA, and AI-agent engagement discipline. |
| [`AEO-GEO-GUIDE.md`](./AEO-GEO-GUIDE.md) | A focused deep-dive on getting cited by AI answer engines — retrieval mechanics, machine-readability, content patterns that win citations, structured data, and a measurement framework for AI visibility. |
| [`CHECKLISTS.md`](./CHECKLISTS.md) | Condensed, copy-pasteable pre-publish and audit checklists distilled from the two files above — use these for fast gates, use the playbooks for the reasoning behind each rule. |

## How to use this repo as an AI agent skill

1. **Before doing any SEO task** (keyword research, technical audit, content build, RCA, link building), read the relevant section of `SEO-PLAYBOOK.md` first — it encodes the reasoning and thresholds behind each rule, not just the rule.
2. **Before publishing anything**, run it against `CHECKLISTS.md`.
3. **For anything AI-search/citation-specific**, read `AEO-GEO-GUIDE.md` alongside §7 of the playbook.
4. **Never fabricate a number.** Every rule in this repo that references a metric or threshold assumes you're pulling from a real, checkable data source (Search Console, an analytics tool, a keyword-research export, a live SERP check) — not estimating.
5. **Verify, don't trust a single source.** Any automated tool's index (rank trackers, keyword tools, a general web-search tool) can be stale or wrong. Cross-check ranking/competitor claims against a live source before asserting them.

## Scope and limitations

This repo is a **methodology reference**, not a crawler, a rank tracker, or an API integration. It won't fetch a live SERP, run Lighthouse, or pull Search Console data for you — it tells you what to do with that data once you (or another tool/agent) have it, and how to reason about it correctly. If your workflow needs live data fetching, pair this skill with whatever crawling/API/MCP tooling you already have; this repo is the judgment layer on top, not the data layer.

## Methodology

Every recommendation here is written to be **falsifiable, not promotional** — each rule states the concrete failure pattern it prevents and, where applicable, a verification step or threshold (e.g., "sort by impressions descending; the row where impressions drop to 1 is your evidence boundary"). Section 1's core principles (never fabricate a number, verify before trusting a single source, distinguish real signal from artifact) apply to every other section — they're the constraint everything else in this repo has to satisfy.

## Contributing

This is a living document. If you (human or agent) discover a new pattern, gotcha, or discipline in real SEO/AEO/GEO work, add it here **in generalized form** — no company names, no client-specific URLs or data — filed under the most relevant existing section, or as a new section if it doesn't fit anywhere.

## License

MIT — see [`LICENSE`](./LICENSE). Use, adapt, and redistribute freely.
