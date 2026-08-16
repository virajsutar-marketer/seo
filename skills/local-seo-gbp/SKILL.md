---
name: local-seo-gbp
description: "Local SEO and Google Business Profile audits: NAP consistency, geo-grid rank checks, duplicate-listing detection, per-location page depth, and review management as a ranking signal. Use for any business with a physical location, a service area, or 'near me' search intent."
user-invocable: true
license: MIT
metadata:
  author: virajsutar-marketer
  version: "1.0.0"
  category: seo
  parent_sections: "SEO-PLAYBOOK.md Section 22"
---

# Local SEO & Google Business Profile

A narrower, deeper slice of `SEO-PLAYBOOK.md` Section 22. Read that section in full before running this on a real task. Applies to any business with a physical location, a service area, or "near me" search intent: brick-and-mortar, service-area businesses, multi-location chains.

## When to use this skill

- Someone asks for a local SEO audit or a Google Business Profile (GBP) audit.
- A multi-location business wants to know why one location ranks and another does not.
- Local pack visibility looks strong at headquarters but weak elsewhere in the service area.
- Reviews, NAP data, or listing duplicates need auditing.

## Process

### 1. Audit Google Business Profile completeness

Claim and fully complete every available field: primary and secondary categories (the single most-weighted local ranking factor after proximity), business description, attributes, service list, products, opening hours including holiday hours, and at least one photo set per category (exterior, interior, team, product/service in action). An incomplete profile competing against a fully-completed competitor loses on relevance signal alone, independent of website quality.

### 2. Audit NAP (Name, Address, Phone) consistency

Check consistency across every surface it appears: the GBP listing, the website footer/contact page, and every third-party directory/citation. A mismatched suite number, a phone number format inconsistency, or an old address left live on one directory after a move all dilute this signal. Treat NAP consistency as its own discrete recurring audit, not a one-time setup step; it decays as the business moves, rebrands, or changes phone providers.

### 3. Audit review signal

Volume, recency, average rating, and response rate to reviews (especially negative ones) all matter as both a ranking and conversion signal. A response to a negative review that is calm, specific, and non-defensive is itself a trust signal to future searchers reading the thread, not just damage control. Never delete a legitimate negative review; respond to it.

### 4. Audit local schema markup

`LocalBusiness` (or a more specific subtype), plus `PostalAddress`, `GeoCoordinates`, and `OpeningHoursSpecification` on the website should exactly match what is declared on the GBP listing. A discrepancy between structured data and the live GBP listing is a consistency red flag search engines can detect.

### 5. Audit on-site local relevance signals

Every physical location or service area needs its own unique page, never one generic "locations" page listing all cities in a bulleted list with no unique content per location. Each location page needs genuinely local-specific content: that location's team, that location's specific service area, local landmarks/neighborhoods served, location-specific reviews. A shared template with swapped city names is the local-SEO version of the thin-content/doorway-page risk (see playbook Section 8.4). Embed a location-specific map and the exact NAP for that location on its own page, not just a central "contact us" page. Genuinely local backlinks/citations (chamber of commerce, local news mentions, local business associations, sponsorships) carry more local-relevance weight than generic, non-local backlinks.

### 6. Run geo-grid rank tracking, not a single-point check

Geo-grid rank tracking (checking ranking position from multiple simulated locations across a service area, not just one central point) is the correct methodology for local rank measurement. A single "where do we rank" check from company headquarters can look completely different from the same query run 10 miles away, and an uneven geo-grid (strong near the office, weak at the edges of the actual service area) is a real, actionable finding. Apply the same verify-before-trusting-a-single-source discipline used elsewhere in this repo (see the `keyword-research` sub-skill) to local rankings: a rank-tracking tool's cached position can be stale, so spot-check with a live, geo-simulated search before reporting a local ranking claim.

### 7. Audit for duplicate or suspended GBP listings

A common failure mode after a rebrand, a move, or an agency creating a second listing by mistake. A duplicate listing splits reviews and relevance signal across two profiles instead of consolidating it into one authoritative one. This is a real, self-inflicted ranking loss and should be checked before any other local optimization work.

## Checklist (local SEO)

- [ ] Every GBP field completed (categories, description, attributes, services, hours, photos per category)
- [ ] NAP consistent across GBP, website, and every directory/citation
- [ ] Local schema (LocalBusiness/subtype) matches the live GBP listing exactly
- [ ] Every location/service-area has its own unique page, no generic shared "locations" list page
- [ ] Geo-grid rank check run (multiple simulated points), not a single central-point check
- [ ] Checked for duplicate/suspended GBP listings splitting review/relevance signal
- [ ] Negative reviews have calm, specific, non-defensive responses, none deleted

## Deliverable format: Local SEO Audit

```
## Local SEO Audit: [business/location set]

**Verdict:** [one sentence: strongest actionable finding]

### GBP completeness
- [location]: [% fields complete], missing: [list]

### NAP consistency
- [location]: [consistent/inconsistent], discrepancies found: [where, what]

### Geo-grid results
- [location]: strong at [center], weak at [edge], evidence: [live search results, date]

### Duplicate/suspended listings
- [finding, or "none found"]

### Location page depth
- [location]: [unique content present/absent], risk: [thin/doorway if absent]

### Fix priority
1. [fix]
```
