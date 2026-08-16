---
name: technical-seo-audit
description: "Technical SEO audits: sitemap and indexing health, orphan-page and cannibalization diagnosis, redirect-chain hygiene, Core Web Vitals via TTFB isolation, and CMS-specific gotchas (stale caches, sanitized rich HTML, dual storage fields). Use when the user asks to audit indexing, fix crawl/sitemap issues, diagnose slow page speed, or figure out why a saved edit isn't rendering live."
user-invocable: true
license: MIT
metadata:
  author: virajsutar-marketer
  version: "1.0.0"
  category: seo
  parent_sections: "SEO-PLAYBOOK.md Sections 10, 11, and 12"
---

# Technical SEO Audit: Indexing, Core Web Vitals, CMS Gotchas

A narrower, deeper slice of `SEO-PLAYBOOK.md` Section 10 (Indexing & Sitemap Health), Section 11 (Site Performance / Core Web Vitals), and Section 12 (CMS-Specific Technical Gotchas). Read those sections in full before running this on a real task.

## When to use this skill

- Someone asks for a technical SEO audit, an indexing audit, or "why isn't this page ranking" when the underlying cause could be crawlability.
- A page or content type shows near-zero clicks and impressions across an entire cluster.
- Core Web Vitals or page-speed diagnosis is needed.
- A CMS edit "saved" via an API but the live page shows no change.

## Process

### 1. Sitemap structural audit, always first

- Fetch the sitemap index and every child sitemap; confirm each returns HTTP 200, correct `text/xml` content type, and a real `<lastmod>` per child.
- Confirm `robots.txt` declares the sitemap and blocks non-indexable paths (admin, search, feeds, unused tag archives, query-string variants).
- Check for duplicate sitemap submissions in Search Console (for example a legacy sitemap that now redirects, alongside the current one); keep only the canonical one.
- Build a per-cluster inventory table: content type, URL count in sitemap, percent actually indexed, dominant "not indexed" reason. This single table is the fastest way to see where crawl equity is or is not landing.
- Treat a custom content type with zero entries in any sitemap as its own bug class; test its own sub-sitemap URL directly rather than assuming the main index covers it.

### 2. Bucket every not-indexed URL by cause, because the fix differs

1. Discovered, never crawled: the engine knows the URL exists but has not allocated crawl budget. This is a weak internal-linking problem, not a content-quality problem. Disproportionately hits newer or custom content types lacking inbound links from established pages. Fix: add real contextual internal links from indexed, high-authority pages. One additional link is often not enough; multiple genuinely relevant inbound links (sibling pages cross-linking, contextual links from established content) is the threshold that actually flips a page to indexed, typically within about a day of the link change.
2. Crawled, not indexed: the engine fetched it and judged it not worth indexing. A genuine content-quality or duplicate-value signal (or a rendering problem, see JS-gating below), not a linking problem. Resubmitting will not fix this.
3. Stale exclusion state: the index shows an old noindex signal from a past crawl even though the live page now serves indexable directives; only needs a re-crawl request.
4. Correctly excluded: utility/transactional paths, thin auto-generated archives, permanently-redirecting pages. These should be noindexed and removed from the sitemap, not chased.

Watch for JS-gated content: if a page's actual body content only becomes visible after a user interaction (click-to-reveal, tab switch, lazy render) rather than being present in the initial HTML/DOM, crawlers may see a near-empty page and classify it "crawled, not indexed." Fix by ensuring core content is server-rendered or present in raw HTML.

### 3. Decision framework: indexing issue vs. ranking issue vs. no-demand issue

Pull impressions and average position together:
- Zero impressions, never crawled: indexing issue. No on-page optimization matters until resolved.
- Impressions present, poor position: ranking issue. Relevance/authority/on-page problem, compare against SERP competitors and content depth.
- Impressions present, decent position, no clicks: a CTR/SERP-feature issue, a distinct category (route to the `ranking-rca` sub-skill).
- Impressions near zero despite decent indexing/position: no-demand issue. Verify query volume before chasing a "ranking fix" for a term nobody searches.

### 4. 404 traffic-leak investigation, root-cause not just detect

1. Start from analytics, not a crawler; pull "page not found" pageviews/sessions filtered by page path, referrer, and source/medium, ranked by actual lost traffic.
2. Classify traffic origin: organic-search referrer means the engine still has this URL indexed/ranked, highest priority since it is actively burning ranking equity, needs a 301 to the closest live equivalent. Direct/no referrer is lower urgency, likely a bookmark or stale internal link.
3. Use a historical web-snapshot service to check whether the URL ever served a real 200 page and when it disappeared.
4. Grep the live, published content corpus (not drafts) for the broken path fragment to find the source of the dead internal link; fix both the redirect and the source link.
5. Redirect target priority: exact content successor first, then closest semantic equivalent, then a generic hub/category page if no direct equivalent. Always 301 for genuinely dead/moved content.
6. Verify with a live request after every redirect: confirm the original broken URL now returns a 3xx to the intended target.

### 5. Redirect-chain hygiene

Audit for redirects pointing to other redirects rather than directly to the final live URL; each hop adds latency and dilutes link equity. Audit for redirect targets that are themselves scheduled for removal or already non-200. When migrating a URL structure in bulk, grep the entire internal-link corpus for the old path and fix internal links directly rather than relying solely on the redirect.

### 6. TTFB isolation technique (find the real performance bottleneck)

1. Measure TTFB on a fully dynamic, database-driven page.
2. Measure TTFB on a raw static asset served from the same server/host.
3. Subtract. Fast static asset plus slow dynamic page means the bottleneck is application/plugin/PHP-layer (database queries, plugin hooks, missing page cache), not network/TLS. Both similarly slow means server/network/TLS-level, no plugin optimization will fix it.
4. Cross-check response headers for a page-cache hit indicator and `Cache-Control`. Every request returning `max-age=0` or no cache header means no full-page cache is actually active, even if a caching tool shows "active" in its admin panel.
5. Inconsistent TTFB across page templates on the same site points to a caching-rule/exclusion gap for that template type, not a global infra problem.

### 7. Core Web Vitals fix priority order

1. LCP media optimization: compress/resize/reformat the actual LCP element, disable unnecessary autoplay/preload on mobile. Typically the single largest, fastest win.
2. Server response time / TTFB: enable/verify actual full-page caching (not just tool installation).
3. Render-blocking CSS/JS: remove unused CSS, consolidate/dedupe fonts, defer non-critical JS.
4. Third-party script deferral: delay chat/analytics/marketing scripts until interaction.
5. Re-run the same measurement tool after each fix to confirm the delta before moving to the next item; do not stack multiple changes and re-measure once.

Reference thresholds: LCP good is at or under 2.5s, needs improvement 2.5 to 4s, poor over 4s. CLS good is at or under 0.1, needs improvement 0.1 to 0.25, poor over 0.25. Performance score good is 90 or above, poor under 50 on a 0 to 100 scale.

### 8. CMS-specific gotchas

- "The edit saved but didn't render": many CMSs keep more than one storage location for a page's content, a generic field the platform keeps in sync, and a separate structured/serialized field the actual page-builder or theme reads at render time. Determine which field the renderer consumes before editing, and re-fetch that specific field from the canonical data store after any update, then separately verify the rendered live page.
- REST update mangles rich HTML: some CMS write paths sanitize content on save, silently stripping or unwrapping inline scripts/styles, inline SVG, embedded JSON-LD, or base64 data-URI images. Use a direct authenticated raw write or the platform's native editor for rich/non-standard markup, never trust the API's own read-back as ground truth, and always verify rendered output.
- Page cache serves stale content after a DB-level update: identify every distinct caching layer (site-wide page cache, page-builder/renderer cache, CDN/edge cache), explicitly purge each one, and only then verify the live page via a request that bypasses remaining cache.

## Checklist (technical SEO health-check, run periodically)

- [ ] Sitemap index and all child sitemaps return 200, correct content type, real `<lastmod>`
- [ ] No duplicate sitemap submissions in Search Console
- [ ] Every content type/CPT has its own coverage in the sitemap, verified via the sub-sitemap URL directly
- [ ] Batch URL-inspection pull done; not-indexed URLs bucketed by cause (undiscovered vs. crawled-not-indexed vs. stale exclusion vs. correctly excluded)
- [ ] 404 report pulled from analytics (not just a crawler), ranked by real lost traffic, referrer-classified
- [ ] Redirect chains audited, every redirect points directly to the final live URL
- [ ] TTFB isolation test run (dynamic page vs. static asset) if performance is suspect
- [ ] Cache headers checked on every page template type, not just the homepage
- [ ] After any programmatic CMS edit: raw data-store read confirmed, every caching layer identified and purged, rendered page re-checked

## Deliverable format: Technical SEO Audit

```
## Technical SEO Audit: [site/section]

**Verdict:** [one sentence: is this an indexing, ranking, no-demand, performance, or CMS-mechanics problem]

### Sitemap / indexing findings
- [content type]: [N] URLs in sitemap, [N]% indexed, dominant cause: [undiscovered / crawled-not-indexed / stale exclusion / correctly excluded]

### Core Web Vitals findings
- LCP: [value] ([good/needs improvement/poor]), largest contributor: [asset]
- TTFB isolation: dynamic [ms] vs. static [ms], bottleneck layer: [app/plugin vs. network/server]

### Fix priority (highest ROI first)
1. [fix], expected effect: [what metric it moves]

### Re-measurement plan
- [metric], [tool], [cadence]
```
