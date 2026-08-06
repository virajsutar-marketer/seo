---
name: seo
description: "Complete SEO, AEO (answer-engine optimization), and GEO (generative-engine optimization) methodology — keyword research, competitor gap analysis, technical SEO audits, Core Web Vitals, AI-citation optimization, internal linking, root-cause analysis for ranking/traffic drops, local SEO/Google Business Profile, e-commerce SEO, international SEO/hreflang, and Schema.org structured data. Use when the user says audit my site, why isn't this page ranking, do keyword research, find competitor gaps, fix indexing, improve Core Web Vitals, get cited by AI answer engines, optimize local/GBP rankings, fix e-commerce category pages, set up hreflang, or validate schema markup."
user-invocable: true
license: MIT
metadata:
  author: virajsutar-marketer
  version: "1.1.0"
  category: seo
---

# SEO / AEO / GEO Skill

## When to use this skill

Any task involving organic search visibility: keyword research, technical SEO audits, Core Web Vitals/performance diagnosis, on-page optimization, internal linking strategy, root-cause analysis of a ranking or traffic change, competitor gap analysis, or optimizing content to be cited by AI answer engines (ChatGPT, Google AI Overviews, Perplexity, Claude).

## Process

1. **Read the relevant playbook file(s) in full before acting** — don't skim for a single rule out of context:
   - [`SEO-PLAYBOOK.md`](./SEO-PLAYBOOK.md) — the 21-section core manual (keyword research, competitor gaps, topical authority/pSEO, on-page standards, E-E-A-T, internal linking, technical SEO, analytics hygiene, RCA methodology, link building, program structuring, publishing QA).
   - [`AEO-GEO-GUIDE.md`](./AEO-GEO-GUIDE.md) — deep-dive specifically on getting cited by AI answer engines. Read this alongside playbook §7 for any AI-citation/AEO task.
2. **Run the task through [`CHECKLISTS.md`](./CHECKLISTS.md)** before declaring it done — pre-publish, technical health-check, keyword-research sanity checks, and RCA discipline checklists are all there.
3. **Never fabricate a number.** Every keyword volume, position, click count, or competitor claim must trace to a real, checkable data source (Search Console, an analytics export, a live SERP check). If you don't have live data access, say so explicitly rather than estimating.
4. **Verify, don't trust a single source.** Cross-check any automated tool's ranking/competitor claim against a live, real-time check before asserting it in a deliverable.
5. **For a root-cause investigation** (ranking drop, traffic anomaly), follow playbook §16 in order: state the anomaly precisely, rule out artifacts (bot traffic, tracking fragmentation, brand-vs-non-brand split, AI-surface positional artifacts) before accepting a real-signal explanation, then isolate the variable with a within-page before/after comparison where possible.

## Methodology

Every recommendation in this skill is meant to be **falsifiable, not promotional** — each rule states the failure pattern it prevents and, where applicable, a concrete threshold or verification step (e.g., "sort by impressions descending; the row where impressions drop to 1 is your evidence boundary"). If a task can't be grounded in a real, checkable data source, this skill's discipline is to say so rather than fill the gap with a plausible-sounding estimate.

## Files

- `SEO-PLAYBOOK.md` — core 21-section methodology
- `AEO-GEO-GUIDE.md` — AI-citation deep dive
- `CHECKLISTS.md` — condensed pre-publish/audit checklists
