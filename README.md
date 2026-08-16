# SEO / AEO / GEO Skill Repo

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Claude Code Skill](https://img.shields.io/badge/Claude%20Code-Skill-blue)](SKILL.md)
[![Format](https://img.shields.io/badge/format-Markdown%20Skill-lightgrey)](SKILL.md)

Detailed, tool-agnostic SEO skill set for AI agents (and humans): traditional search SEO plus **AEO (Answer Engine Optimization)** and **GEO (Generative Engine Optimization)** for getting cited by AI chat assistants, AI Overviews, and agentic research tools.

Everything here is **generic and industry-agnostic**: no company names, no specific URLs, no proprietary client data. It's written so any AI agent, on any website, in any industry, can pick it up and execute correctly with zero prior context.

## Table of Contents

- [Why This Skill Exists](#why-this-skill-exists)
- [Install as a Claude Code Skill](#install-as-a-claude-code-skill)
- [Contents](#contents)
- [How to use this repo as an AI agent skill](#how-to-use-this-repo-as-an-ai-agent-skill)
- [Best Use Cases](#best-use-cases)
- [What This Skill Is Not](#what-this-skill-is-not)
- [Scope and limitations](#scope-and-limitations)
- [Methodology](#methodology)
- [Contributing](#contributing)
- [License](#license)

## Why This Skill Exists

Most "SEO skill" write-ups for AI agents are either a vague checklist ("write good meta descriptions") or a thin wrapper around one paid API's output. Neither survives contact with a real audit. The actual failure modes in SEO work are almost always judgment failures, not knowledge gaps: trusting a stale rank-tracker's cached position, treating a CTR drop as a title problem when it's actually an AI-answer-surface artifact, shipping a "gap" list that's really just a buried-ranking problem, publishing a page nobody render-checked at mobile width.

This repo exists to codify those judgment calls once, in generalized form, distilled from real audits, migrations, and content builds, so an agent (or a person) picking it up doesn't have to relearn them by making the same mistake in production. It's public because the discipline is more valuable shared than kept proprietary, and because a skill this detailed is easier to trust once other people can read exactly what it does and doesn't claim.

## Install as a Claude Code Skill

```bash
git clone https://github.com/virajsutar-marketer/seo.git ~/.claude/skills/seo
```

Restart Claude Code. The skill is discovered automatically via `SKILL.md` and invoked whenever a task matches its description (SEO audits, keyword research, AEO/GEO optimization). No plugin marketplace, no install script, no dependencies: it's pure markdown, so there's nothing to break and nothing to run.

## Contents

| File | What it's for |
|---|---|
| [`SKILL.md`](./SKILL.md) | The Claude Code Skill manifest: what triggers this skill, its persona boundaries, its authority model, and the process to follow. Start here if you're an agent. |
| [`SEO-PLAYBOOK.md`](./SEO-PLAYBOOK.md) | The core 25-section operating manual: keyword research, competitor gap analysis, topical authority/pSEO, on-page standards, AEO/GEO fundamentals, E-E-A-T, internal linking, technical SEO (indexing, Core Web Vitals, CMS gotchas, consent, instant indexing), analytics hygiene, root-cause analysis, link building, program structuring, publishing QA, AI-agent engagement discipline, local SEO/GBP, e-commerce SEO, international SEO/hreflang, and a Schema.org structured-data deep-dive. |
| [`AEO-GEO-GUIDE.md`](./AEO-GEO-GUIDE.md) | A focused deep-dive on getting cited by AI answer engines: retrieval mechanics, machine-readability, content patterns that win citations, structured data, and a measurement framework for AI visibility. |
| [`CHECKLISTS.md`](./CHECKLISTS.md) | Condensed, copy-pasteable pre-publish and audit checklists distilled from the two files above. Use these for fast gates, use the playbooks for the reasoning behind each rule. |

## How to use this repo as an AI agent skill

1. **Before doing any SEO task** (keyword research, technical audit, content build, RCA, link building), read the relevant section of `SEO-PLAYBOOK.md` first. It encodes the reasoning and thresholds behind each rule, not just the rule.
2. **Before publishing anything**, run it against `CHECKLISTS.md`.
3. **For anything AI-search/citation-specific**, read `AEO-GEO-GUIDE.md` alongside Section 7 of the playbook.
4. **Never fabricate a number.** Every rule in this repo that references a metric or threshold assumes you're pulling from a real, checkable data source (Search Console, an analytics tool, a keyword-research export, a live SERP check), not estimating.
5. **Verify, don't trust a single source.** Any automated tool's index (rank trackers, keyword tools, a general web-search tool) can be stale or wrong. Cross-check ranking/competitor claims against a live source before asserting them.

## Best Use Cases

Grounded directly in what `SEO-PLAYBOOK.md`'s 25 sections actually cover:

- Keyword research with intent classification and a three-tier evidence model (real impressions, external volume data, emerging category terms), instead of one merged, unlabeled list.
- Competitor gap analysis that requires both a verified live competitor ranking and a confirmed absence on the target site, not a buried-ranking problem mislabeled as a gap.
- Technical SEO audits: sitemap/indexing health, orphan-page diagnosis, redirect-chain hygiene, Core Web Vitals via TTFB isolation, CMS-specific gotchas (stale caches, sanitized rich HTML, dual storage fields).
- Root-cause analysis on a ranking or traffic drop, using the artifact-elimination sequence (bot traffic, tracking fragmentation, brand-vs-non-brand split, AI-surface positional artifacts) before accepting a real-signal explanation.
- AEO/GEO work: auditing whether content is machine-readable, structuring direct-answer-first and FAQ content, and building a repeatable AI-citation measurement loop.
- Local SEO and Google Business Profile audits: NAP consistency, geo-grid rank checks, duplicate-listing detection, per-location page depth.
- E-commerce SEO: category-page content strategy, faceted-navigation indexing control, product schema/inventory sync, out-of-stock handling.
- International SEO and hreflang: URL-structure decisions, bidirectional hreflang graph audits, localization-quality review beyond machine translation.
- Schema.org structured-data validation: required-field completeness, datetime formatting, entity cross-referencing by `@id`, choosing the right type for the actual content.
- Topical authority, content clustering, and pSEO gating: auditing existing cluster performance before scaling, diagnosing cannibalization, gating templated pages on real substance.
- Internal linking audits run as a tracked, verifiable program rather than an ad-hoc pass.
- Multi-quarter SEO program and roadmap structuring, with an explicit phase sequence (technical health first, then fix what already ranks, then scale new content, link building in parallel).

## What This Skill Is Not

This skill is scoped to SEO/AEO/GEO methodology only. It sits alongside a set of sibling repos, each scoped to its own discipline, all under [github.com/virajsutar-marketer](https://github.com/virajsutar-marketer/):

- **Not a content writer.** This skill defines what a piece needs to satisfy (keyword placement, structure, schema, CTA discipline) but doesn't draft the finished long-form copy. That's `content-writing-agent`.
- **Not a social media manager.** Distribution, scheduling, and platform-specific social copy live in `social-media-agent`.
- **Not a paid-ads specialist.** Budget, bidding, and campaign-spend decisions are out of scope here entirely. That's `paid-ads-agent`.
- **Not a general-purpose research agent.** Open-ended research outside SEO/AEO/GEO (market sizing, product research, unrelated competitive intelligence) belongs to `research-agent`.
- **Not a reporting/dashboard builder.** This skill produces SEO deliverables (audits, briefs, RCAs); assembling recurring cross-channel reporting dashboards is `reporting-agent`'s job.
- **Not a presentation designer.** Turning findings into a polished deck is `presentation-design-agent`.
- **Not an email/newsletter writer.** Newsletter composition and send discipline live in `email-newsletter-agent`.
- **Not a crawler or an API integration.** See [Scope and limitations](#scope-and-limitations) below; this is a judgment layer, not a data-fetching tool.

When a task crosses one of these boundaries, the right move is to flag it to the owning skill/agent rather than improvising past the boundary.

## Scope and limitations

This repo is a **methodology reference**, not a crawler, a rank tracker, or an API integration. It won't fetch a live SERP, run Lighthouse, or pull Search Console data for you: it tells you what to do with that data once you (or another tool/agent) have it, and how to reason about it correctly. If your workflow needs live data fetching, pair this skill with whatever crawling/API/MCP tooling you already have; this repo is the judgment layer on top, not the data layer.

## Methodology

Every recommendation here is written to be **falsifiable, not promotional**: each rule states the concrete failure pattern it prevents and, where applicable, a verification step or threshold (e.g., "sort by impressions descending; the row where impressions drop to 1 is your evidence boundary"). Section 1's core principles (never fabricate a number, verify before trusting a single source, distinguish real signal from artifact) apply to every other section; they're the constraint everything else in this repo has to satisfy.

## Contributing

This is a living document. If you (human or agent) discover a new pattern, gotcha, or discipline in real SEO/AEO/GEO work, add it here **in generalized form**: no company names, no client-specific URLs or data, filed under the most relevant existing section, or as a new section if it doesn't fit anywhere.

## License

MIT, see [`LICENSE`](./LICENSE). Use, adapt, and redistribute freely.
