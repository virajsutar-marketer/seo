---
name: keyword-research
description: "Keyword research and competitor gap analysis with buyer-intent classification, an impressions-descending evidence check, and a three-tier evidence model (real impressions, external volume data, emerging category terms). Use when the user asks to find keywords, size demand for a topic, build a content gap list, or verify whether a competitor gap is real."
user-invocable: true
license: MIT
metadata:
  author: virajsutar-marketer
  version: "1.0.0"
  category: seo
  parent_sections: "SEO-PLAYBOOK.md Sections 2 and 3"
---

# Keyword Research & Competitor Gap Analysis

A narrower, deeper slice of `SEO-PLAYBOOK.md` Section 2 (Keyword Research Methodology) and Section 3 (Competitor Gap Analysis). Read those sections in full before running this on a real task; this file is the operating process, not a replacement.

## When to use this skill

- Someone asks for keyword research on a new topic, page, or campaign.
- A stakeholder asks whether a content gap versus a competitor is real.
- A keyword list needs prioritizing before a content build.
- A stakeholder claims "we already cover this" and it needs checking against the exact buyer-intent phrasing, not just the general topic.

## Process

### 1. Classify every keyword by buyer intent before anything else

Split candidates into two buckets:
- Definitional/informational: "what is X," bare category terms, "how does X work," tutorials, certifications.
- Vendor-evaluation/buyer-intent: the same root term modified by "tool," "platform," "software," "solution," "service," "company," "agency," or a comparison/superlative frame ("best X," "X vs Y," "X alternatives"). The modifier is the signal: the searcher is already evaluating vendors, not learning a concept.

Default to deprioritizing generic definitional terms once existing site content already tangentially covers the concept; that audience is students/researchers, not buyers. Put build effort into the buyer-intent variant of the same root term instead. Prioritize buyer-intent terms whose modifier matches how the business itself describes its own product category, since those are the easiest pages to write with genuine first-party authority.

### 2. Run the impressions-descending cutoff technique for zero-visibility claims

- Pull Search Console query data sorted by impressions descending for the exact keyword or URL.
- Rows with real impressions at any position, even single digits, mean the site has some presence: it is buried, not absent. The fix is targeting, authority, or internal linking, not new content.
- Zero rows at all over a 60 to 90 day window is the true zero-impression signal, but confirm it is not a plumbing artifact (step 3) before treating it as a genuine content gap.
- Practical cutoff heuristic: sort by impressions descending; the row where impressions drop to 1, or where rows stop entirely, is the evidence boundary. Treat anything past it as noise or true zero. The same technique works on a full result set (for example the top 5,000 rows): if row 5,000 already shows 1 impression, the dataset captured everything meaningful.

### 3. Cross-check page existence before trusting analytics-only absence

A URL with historical impressions or clicks is not proof the page still exists. Run a live HTTP status check (200 vs. 404 vs. redirect) before building a plan (redirects, content refresh, internal linking) on the assumption it is a live page. A 404, a dead redirect to an unrelated page, or a redirect to a gated asset all count as "no real public page exists," a stronger, more actionable finding than a Search-Console-only absence.

### 4. Apply the three evidence tiers, never one merged list

1. Tier A: real, current impressions in the site's own Search Console data. Highest confidence, already being shown, just not converting to clicks. Build here first.
2. Tier B: zero current impressions, but real historical or external volume data exists in a third-party keyword tool. Market wants this, the site is not in the conversation. Build here second.
3. Tier C: no hard volume in any dataset, but the phrasing is an emerging category term the business has genuine authority to speak to. Fold into existing Tier A/B page copy rather than building a brand-new speculative page.

If a keyword shows strong historical data that has since vanished from current data, that is a regression (see the `ranking-rca` sub-skill), not an unbuilt content gap. Re-pull volume data before committing to a large content build if the export is more than a few months old.

### 5. Competitor gap analysis: both conditions must be true

A real gap requires:
1. A competitor verified, live, ranking on page 1 or near it, for the term.
2. The target site has zero presence, not buried, not partial, not "ranks for a related variant." Any real impression or click data on the target site means it is a "buried ranking" problem (fix targeting/authority), not a content gap (build new).

When scoped literally ("only terms where we have literally nothing"), exclude any keyword with even partial existing visibility, even a single impression at a terrible position. Keep those in a separate "fix, don't rebuild" list.

Verify every "competitor ranks #N" claim with a live, real-time search before it goes in a report. A keyword tool's cached snippet or ranking claim can be stale or wrong; treat any tool-reported ranking as a hypothesis to confirm, not a fact to repeat. The same discipline applies to the target site's own historical content.

For structural gaps, compare competitor sitemap/URL-pattern frequency against the target site's sitemap for the same topic buckets. A large frequency gap (competitors have dozens of pages on a topic cluster, target has 0 to 1) is strong evidence of a structural content-type gap, independent of any single keyword's volume. Specifically check whether the competitor set publishes a dedicated "Alternatives" or "vs" ranked-listicle format for rivals the target already has deep head-to-head content for: if the target has zero or near-zero coverage of this specific format even though the underlying research exists elsewhere, this repackages existing research into a new intent at low incremental cost, one of the highest-leverage gaps available.

## Checklist (competitor gap / keyword research sanity checks)

- [ ] Every keyword volume/position number traces to a named, checkable source
- [ ] "Zero visibility" confirmed via impressions-descending Search Console pull, not assumed
- [ ] Any URL used as evidence of "the page exists" is live-status-checked (200), not just present in old analytics
- [ ] Any "competitor ranks #N" claim is verified with a live, real-time search before it goes in a report
- [ ] Gap list scope matches exactly what was asked (for example "zero presence only" excludes anything with even 1 impression)
- [ ] Keywords are labeled by evidence tier (A/B/C), never merged into one undifferentiated list
- [ ] Any keyword with vanished historical data is flagged as a regression, not filed as a content gap

## Deliverable format: Keyword / Gap Brief

```
## Keyword Research Brief: [topic/cluster]

| Keyword | Intent | Evidence tier | Source | Current status | Priority |
|---|---|---|---|---|---|
| [phrase] | definitional / buyer-intent | A / B / C | [Search Console / keyword tool / live SERP check] | [buried / true gap / regression] | [build / fix targeting / fold into existing page] |

### Verified competitor gaps
- [keyword]: [competitor] confirmed live at position [N] via live search on [date]. Target site: zero presence confirmed via impressions-descending pull, [date range].

### Buried rankings (not gaps, do not rebuild)
- [keyword]: target has [N] impressions at position [N]. Fix = targeting/authority/internal linking, not new content.

### Structural format gaps
- [format, e.g. "Alternatives" listicle]: competitor count [N] vs. target count [N].
```
