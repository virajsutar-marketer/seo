# Quick-Reference Checklists

Condensed, copy-pasteable checklists distilled from [`SEO-PLAYBOOK.md`](./SEO-PLAYBOOK.md) and [`AEO-GEO-GUIDE.md`](./AEO-GEO-GUIDE.md). Use these for fast pre-publish/pre-audit gates; use the full playbook when you need the reasoning behind a rule or a step-by-step process.

---

## Pre-publish checklist (every page/post)

- [ ] Focus keyword in H1
- [ ] Focus keyword at/near the start of the title tag (< ~60 chars)
- [ ] Focus keyword in meta description (~150–160 chars, front-loaded)
- [ ] Focus keyword in URL slug (kebab-case)
- [ ] Focus keyword in the first ~10% of body content
- [ ] Focus keyword in at least one subheading
- [ ] Focus keyword in at least one image alt attribute
- [ ] Keyword density in the ~0.5–2.5% band — natural, not stuffed
- [ ] 3+ contextual internal links to real, live pages (not grouped together)
- [ ] External links only to independent, high-authority sources — never a competitor's own content
- [ ] One dofollow to the single most authoritative external source; rest nofollow
- [ ] On-page SEO scoring tool run, minimum threshold met (e.g. 80/100)
- [ ] Schema present and valid (Article/BlogPosting + FAQPage if applicable), datetimes are full ISO 8601 with timezone
- [ ] Breadcrumbs present in exactly one place (theme OR page-level schema, never both)
- [ ] At least one styled CTA callout box, placed ~75–85% through the piece, topic-specific copy
- [ ] In-body images are real photos of the actual subject matter, not generic stock/flat icons, and unique (not reused elsewhere on the site)
- [ ] No fabricated stat, quote, or customer testimonial — every claim traces to a real, checkable source
- [ ] Published/modified date reflects a real edit — never bumped for cosmetic freshness alone
- [ ] Rendered and visually inspected at both desktop and mobile width before shipping
- [ ] After publish: submitted to IndexNow + the relevant search engine's indexing API

## AEO/GEO pre-publish add-on

- [ ] Every citation-critical fact (price, spec, number, date) exists in plain server-rendered HTML, not only in JS/image/PDF
- [ ] No citation-critical content hidden behind an accordion/tab/hover state
- [ ] At least one direct-answer-first paragraph or "quick answers" block near the top
- [ ] FAQ section (if present) uses FAQPage schema and literal, self-contained Q&A pairs
- [ ] Claims are stated plainly and confidently where genuinely verified — no unnecessary hedging
- [ ] robots.txt does not block the crawler/user-agents relevant to AI retrieval systems for this page

## Technical SEO health-check (run periodically, e.g. monthly)

- [ ] Sitemap index + all child sitemaps return 200, correct content type, real `<lastmod>`
- [ ] No duplicate sitemap submissions in Search Console
- [ ] Every content type/CPT has its own coverage in the sitemap (verify the sub-sitemap URL directly)
- [ ] Batch URL-inspection pull done; not-indexed URLs bucketed by cause (undiscovered vs. crawled-not-indexed vs. stale exclusion vs. correctly excluded)
- [ ] 404 report pulled from analytics (not just a crawler), ranked by real lost traffic, referrer-classified
- [ ] Redirect chains audited — every redirect points directly to the final live URL, not another redirect
- [ ] TTFB isolation test run (dynamic page vs. static asset) if performance is suspect
- [ ] Cache headers checked on every page template type, not just the homepage
- [ ] Consent-management tool verified to actually gate tag firing (not just cosmetically present)
- [ ] Analytics query-string dimension checked for bot/scraper parameter clusters

## Competitor gap / keyword research sanity checks

- [ ] Every keyword volume/position number traces to a named, checkable source
- [ ] "Zero visibility" confirmed via impressions-descending Search Console pull, not assumed
- [ ] Any URL used as evidence of "the page exists" is live-status-checked (200), not just present in old analytics
- [ ] Any "competitor ranks #N" claim is verified with a live, real-time search before it goes in a report
- [ ] Gap list scope matches exactly what was asked (e.g. "zero presence only" excludes anything with even 1 impression)

## Root-cause-analysis (RCA) discipline

- [ ] Anomaly stated precisely (pages, date range, metric, magnitude) before any cause is proposed
- [ ] Bot/scraper traffic ruled out or quantified before trusting a raw traffic number
- [ ] Brand vs. non-brand queries segmented separately
- [ ] AI-answer-surface positional artifacts (pinned position 1.0, tight burst impressions, skewed device/geo mix, near-zero clicks) checked and excluded from "real" performance calculations
- [ ] Within-page before/after comparison used where a clear change event exists, not just cross-page correlation
- [ ] Findings labeled as confirmed / contributing-unproven / non-issue — not all lumped together
- [ ] Report leads with the verdict, not the data trail
