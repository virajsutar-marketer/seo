---
name: international-seo-hreflang
description: "International SEO: URL-structure decisions (ccTLD/subdomain/subdirectory), bidirectional hreflang graph audits, canonical/hreflang agreement, and localization-quality review beyond machine translation. Use for any site serving more than one country, region, or language."
user-invocable: true
license: MIT
metadata:
  author: virajsutar-marketer
  version: "1.0.0"
  category: seo
  parent_sections: "SEO-PLAYBOOK.md Section 24"
---

# International SEO & Hreflang

A narrower, deeper slice of `SEO-PLAYBOOK.md` Section 24. Read that section in full before running this on a real task. Applies to any site serving more than one country, region, or language.

## When to use this skill

- Someone asks to set up or audit hreflang.
- A multi-market or multi-language expansion is being planned and needs a URL-structure decision.
- Localized pages exist but rankings or indexing look inconsistent across markets.
- Content was machine-translated and needs a quality gate before publishing.

## Process

### 1. Pick one URL structure deliberately, apply it consistently

Do not mix approaches across the site.
- Country-code top-level domains (`example.de`, `example.fr`): the strongest geo-targeting signal, but the highest operational overhead, since each ccTLD needs its own domain authority and its own hosting/DNS management.
- Subdomains (`de.example.com`): moderate geo-targeting signal, easier to manage than separate ccTLDs, but subdomains can be treated as semi-independent properties by some analytics/SEO tooling, which needs to be accounted for in reporting.
- Subdirectories (`example.com/de/`): the most common practical choice for most sites, consolidates domain authority into one property, simplest to maintain, the standard recommendation when there is not a strong specific reason to fragment authority across ccTLDs or subdomains.

### 2. Audit hreflang as a graph, not a per-page checklist item

Every localized version of a page needs a complete, mutually-consistent set of hreflang tags referencing every other language/region variant of that same page, including a self-referencing tag. The most common, highest-impact hreflang bug is an asymmetric/broken return-tag relationship: if page A declares an hreflang relationship to page B, page B must declare the matching relationship back to page A. A one-directional hreflang reference is invalid and gets ignored by search engines, silently defeating the entire implementation. A broken link anywhere in the graph can undermine the whole set for that page cluster, so audit the full graph, not one page at a time.

Use a generic, catch-all `x-default` hreflang value to specify which version to serve to a searcher whose language/region does not match any explicitly declared variant, commonly the primary-market version or a genuine international/language-selector landing page.

### 3. Confirm hreflang and canonical tags agree

A page's canonical tag should point to itself, each localized variant is its own canonical, distinct page, not to one "master" version, when the pages are genuinely localized (different language, meaningfully adapted content) rather than pure duplicates.

### 4. Review localization quality, not just translation completeness

Machine-translated content with zero human review is a real quality and trust risk, not just a nice-to-have polish step. Literal or awkward machine translation is detectable by both users and content-quality systems, and reads as low-effort in the same way generic AI-templated content does under the scaled-content-abuse guardrail (see playbook Section 8.4). At minimum, have a native or fluent speaker review machine-translated output before publishing, especially for commercial/high-intent pages.

Localization is not just translation: currency, units of measurement, date formats, cultural references/idioms, region-specific proof points (local customer logos/testimonials, region-specific compliance/certifications, local payment methods and shipping/return policy details) all need genuine adaptation per market, not a literal word-for-word translation of the primary-market version.

### 5. Redo keyword research per target market

Keyword research must be redone per target language/market, not translated from the primary market's keyword list. The same underlying concept can have a completely different search-volume distribution, different exact phrasing, and even a different primary search intent across languages/markets. A keyword list translated word-for-word from the primary language frequently misses the actual phrasing real searchers in that market use. Pair this with the evidence-tier discipline in the `keyword-research` sub-skill, re-run per market rather than assumed to carry over.

### 6. Verify performance and compliance per target market, not just the primary market

Server location and CDN configuration affect perceived page speed per region; a site hosted in one region with no CDN/edge presence will show materially worse Core Web Vitals for users physically far from that server. Verify performance from within each target market. Region-specific legal/compliance requirements (cookie-consent law variations, data-residency requirements, region-specific accessibility law) need checking per target market before launch; a consent-banner implementation satisfying one jurisdiction's law may not satisfy another's, independent of the technical consent-tooling audit itself. Currency and payment-method localization is both a conversion-rate and a trust signal for e-commerce specifically.

## Checklist (international SEO)

- [ ] One URL structure (ccTLD / subdomain / subdirectory) used consistently sitewide
- [ ] Every localized page has a complete, mutually-consistent hreflang set including self-reference
- [ ] hreflang return-tag relationships verified bidirectional (A to B implies B to A)
- [ ] `x-default` hreflang set for unmatched languages/regions
- [ ] Canonical tags agree with hreflang, each genuine localization is its own canonical
- [ ] Machine-translated content reviewed by a native/fluent speaker before publishing
- [ ] Keyword research redone per target market, not translated from the primary market's list
- [ ] Page speed verified from within each target region, not just the primary market

## Deliverable format: International SEO / Hreflang Audit

```
## International SEO Audit: [site/market set]

**Verdict:** [one sentence: strongest actionable finding]

### URL structure
- Current approach: [ccTLD / subdomain / subdirectory]. Consistency: [consistent/mixed, where it breaks]

### Hreflang graph audit
| Page cluster | Variants | Self-reference present | Bidirectional confirmed | x-default set |
|---|---|---|---|---|

### Localization quality spot-check
- [market]: machine-translated? [yes/no]. Human-reviewed? [yes/no]. Currency/units/proof points localized: [yes/no]

### Per-market performance
- [market]: [CWV metrics], server/CDN location: [...]

### Fix priority
1. [fix]
```
