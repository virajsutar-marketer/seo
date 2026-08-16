---
name: ranking-rca
description: "Root-cause analysis for ranking or traffic drops: an artifact-elimination sequence (bot traffic, tracking fragmentation, brand-vs-non-brand split, AI-surface positional artifacts) before accepting a real-signal explanation, plus within-page before/after isolation and a three-tier reporting structure. Use when investigating any ranking drop, traffic anomaly, or CTR collapse."
user-invocable: true
license: MIT
metadata:
  author: virajsutar-marketer
  version: "1.0.0"
  category: seo
  parent_sections: "SEO-PLAYBOOK.md Sections 15 and 16"
---

# Ranking / Traffic Root-Cause Analysis (RCA)

A narrower, deeper slice of `SEO-PLAYBOOK.md` Section 16 (Root-Cause Analysis) and Section 15 (Analytics Data Hygiene, the artifact sources RCA has to rule out). Read both in full before running this on a real task.

## When to use this skill

- A ranking, traffic, or CTR metric moved and someone needs to know why.
- A page ranks well but gets suspiciously few clicks.
- A migration or template change happened and someone wants to know if it caused a drop.
- A stakeholder wants to declare a fix "worked" and it needs re-measurement before that claim ships.

## Process

### 1. State the anomaly precisely before hypothesizing a cause

Which pages, which date range, which metric moved, by how much. Never start from a hypothesis and go looking for supporting data.

### 2. Rule out artifacts before accepting a real-signal explanation, in this rough frequency order

1. Automated/bot traffic disguised as organic: check for anomalous parameter patterns, geo/device mixes inconsistent with the expected audience, or session shapes inconsistent with human browsing. Detection method: pull the full landing-page-plus-query-string dimension for the suspected channel and look for a recurring cluster of specific parameter names appearing together across many unrelated URLs, a consistent fingerprint rather than organic variation. Strong confirming test: check whether polluted paths correspond to a page deliberately excluded from indexing (noindex); a noindex page racking up "organic search" sessions with the suspicious parameter cluster is proof the traffic is synthetic. Quantify precisely per time window; bot share can vary significantly between windows, so state the specific date range and percentage rather than quoting an older estimate once a newer overlapping measurement exists.
2. Tracking-parameter fragmentation: the same logical page/source appearing to "change" simply because URL parameters split what should be one measurement into many. A query-parameter consolidation setting normalizes reporting rows but does not by itself remove bot sessions from totals; understand the difference between a reporting-cleanliness fix and an actual bot-exclusion fix.
3. Brand vs. non-brand query split: always segment separately. A high brand-query CTR next to a near-zero non-branded CTR on the same site is strong evidence the site converts fine once found; titles, snippets, speed, and trust are not the cause of the non-brand problem, the site simply is not being found for buyer-intent terms.
4. AI-answer-surface positional artifacts: a page/query showing an unusually high (even #1) position with large impressions but near-zero clicks, especially when impressions cluster in tight bursts, position is pinned unnaturally at exactly 1.0 with no variance, device mix is skewed unnaturally (for example 100% desktop), or geo mix does not match the expected audience. Treat this as an inferred fingerprint of automated/AI-surface retrieval, since most analytics tools do not label it as a dimension; it must be inferred from data shape. Exclude these rows before calculating "real" position/CTR performance, or genuine improvement elsewhere gets masked or offset in aggregate reporting.

### 3. Hold one variable constant to test a hypothesis

The most robust evidence is a within-page, before/after comparison across a known change event (a URL migration, template change, content update): it holds content quality/topical relevance constant and isolates the specific change's effect, more reliable than noisy cross-page correlation. Prefer comparing three equal, sequential windows (for example 30 versus 30 versus 30 days) over a single long lookback; this reveals trend direction and rules out step-change artifacts that a simple two-point before/after comparison would miss.

### 4. Distinguish "technically flawless" from "actually working"

A migration can pass every standard technical audit (correct redirects, canonicals, index directives, sitemap coverage) and still cause a real, sustained loss. Technical correctness rules out certain causes but does not explain a drop by itself; keep investigating secondary factors, typically internal link equity/authority transfer, rather than concluding "it was clean, so nothing is wrong." Never revert a legitimate technical change (redirects, canonicalization) as a "fix" for a correlated ranking drop unless direct evidence shows the technical change itself is broken; reverting a clean migration restarts the migration clock and compounds the problem. The correct fix for a link-equity-caused drop is additive internal linking, not reversion.

### 5. Treat a regression differently from a gap

A keyword/page that previously had confirmed real rankings/traffic and has since dropped to zero is a regression requiring diagnosis of what broke (canonical, redirect, noindex, deindexing fault); do not file it alongside genuine "never had a page for this" content gaps (see the `keyword-research` sub-skill), the fixes are completely different.

### 6. Watch for two additional artifact classes specific to reporting

- Multi-listing/SERP-feature CTR artifacts: a page can show position-1 impressions for a query purely because it is rendering as a sitelink under a different result. Pull the actual query mix before treating a "high position, zero click" page as a CTR-fix opportunity; any automated CTR-gap tool unaware of multi-listing SERPs will overstate recoverable clicks.
- Answer-engine capture as a non-fixable CTR cause: when a page ranks well but has near-zero CTR even with a strong title, check whether the SERP is giving a synthesized/direct answer before any organic link shows. If so, a title/meta rewrite will not move CTR; restructure the on-page answer (crisp quotable block, FAQ structure) to compete for the answer/citation slot instead (see the `aeo-geo-citations` sub-skill).

### 7. Report honestly and explicitly

Report correlations as directional, not deterministic, especially with small samples/outliers, relying on the within-page before/after evidence as the stronger claim. Do not conflate "page-1 position" with "ranking success" without checking clicks; a large share of nominally top-10 positions can receive zero clicks. Explicitly separate what has been directly verified (live status checks, live crawler-simulated fetches, direct data pulls) from what is inferred or assumed, and flag any step not yet completed so the audience does not over-read confidence into an incomplete analysis. Always re-verify a prior finding against fresh live data before reusing it; never assume an old diagnosis still holds.

## Checklist (RCA discipline)

- [ ] Anomaly stated precisely (pages, date range, metric, magnitude) before any cause is proposed
- [ ] Bot/scraper traffic ruled out or quantified before trusting a raw traffic number
- [ ] Brand vs. non-brand queries segmented separately
- [ ] AI-answer-surface positional artifacts (pinned position 1.0, tight burst impressions, skewed device/geo mix, near-zero clicks) checked and excluded from "real" performance calculations
- [ ] Within-page before/after comparison used where a clear change event exists, not just cross-page correlation
- [ ] Findings labeled as confirmed / contributing-unproven / non-issue, not all lumped together
- [ ] Report leads with the verdict, not the data trail

## Deliverable format: SEO / RCA Review

```
## SEO / RCA Review: [page, query, or site]

**Verdict:** [one sentence stating plainly whether the premise driving the investigation was even true]

### Confirmed causes
- [cause]. Evidence: [data source, date range, verification method]

### Contributing factors / open questions
- [factor]. Plausible but not fully proven, flagged as open.

### Non-issues
- [thing that looked like a problem but isn't]. Why: [explanation]

### Why this matters / apply going forward
- [repeatable checklist item, so the next person inherits the discipline, not just the one-time conclusion]
```
