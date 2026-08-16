---
name: schema-structured-data
description: "Schema.org structured-data validation: required-field completeness, ISO 8601 datetime formatting, entity cross-referencing by @id, choosing the right schema type for the actual content, and monitoring rich-result appearance over time. Use when validating, implementing, or debugging any JSON-LD/schema markup."
user-invocable: true
license: MIT
metadata:
  author: virajsutar-marketer
  version: "1.0.0"
  category: seo
  parent_sections: "SEO-PLAYBOOK.md Section 25 (cross-referenced from 6.3, 7.5, 22, 23)"
---

# Schema.org / Structured Data

A narrower, deeper slice of `SEO-PLAYBOOK.md` Section 25, which itself consolidates schema guidance referenced throughout the playbook (Section 6.3 on-page requirements, Section 7.5 AEO schema, Section 22 local, Section 23 e-commerce). Read Section 25 in full before running this on a real task.

## When to use this skill

- Someone asks to implement, validate, or debug schema/JSON-LD markup.
- A rich result that used to appear has disappeared.
- Someone wants to add schema purely to try to earn a rich-result appearance.
- A site update (theme, plugin, migration) may have silently broken existing schema.

## Process

### 1. Choose the schema type that genuinely matches the content

Do not apply `Product` schema to a page that is not actually selling a product, or `Review` schema to a page that is not a genuine third-party review, purely to try to earn a rich-result appearance. Mismatched or manipulative schema is both a spam-policy risk (misleading structured data is explicitly against most search engines' structured-data guidelines) and a risk to the credibility of the site's other genuine schema on the same domain.

Common schema types and their fit: `Article`/`BlogPosting` for editorial content, `Product`/`Offer`/`AggregateRating` for e-commerce, `LocalBusiness` (or subtype) for physical/service locations, `FAQPage` for genuine FAQ sections, `HowTo` for genuine step-by-step instructional content, `VideoObject` for video content (with a real, reachable thumbnail, a common validation failure), `Event` for real scheduled events, `JobPosting` for real open roles, `Review`/`Recipe`/`Course` for their respective genuine content types.

One dominant schema type per page, supporting types layered underneath: a page can legitimately carry `Article` schema as its primary type plus a nested `FAQPage` for an FAQ section within it, but should not declare multiple competing primary types for the same page's core content.

### 2. Validate the complete required-field set, not just the easy fields

A schema type declared but missing its required fields is often worse than no schema at all; an incomplete or invalid schema block can cause a search engine to distrust or ignore all structured data on that page, not just the broken block. Validate the complete required-field set for every schema type in use.

### 3. Fix datetime formatting first, since it is the most common failure

Datetime fields (datePublished, dateModified, uploadDate, event start/end) need full ISO 8601 format with a timezone offset. A bare date with no time/timezone component reliably trips validation warnings, the single most common schema validation failure across every content type.

### 4. Cross-reference related entities by @id

Nested/related schema types should cross-reference by `@id` where the underlying entities are genuinely the same real-world thing across multiple schema blocks on a site (for example the same `Organization` referenced from `Article` author schema and from a `LocalBusiness` block). This creates an explicit entity graph rather than several disconnected, duplicated declarations of the same entity, and is a stronger signal for entity disambiguation, the same principle as the AEO/GEO entity-consistency guidance (see the `aeo-geo-citations` sub-skill).

### 5. Test and monitor, do not treat implementation as one-time

Test new schema against the search engine's own structured-data testing/validation tool before publishing, not just a generic third-party JSON-LD linter; search engines periodically add support for new properties or deprecate old ones, and only the platform's own tool reflects current requirements accurately. Monitor rich-result appearance in search-console-style tooling over time, not just at initial implementation. A rich result that was appearing can silently stop appearing due to a schema regression, a policy change, or a manual/algorithmic quality action; this is a distinct, worth-tracking metric separate from ranking position or click volume.

Run a structured-data lint/validation pass after every schema change, and periodically even without a known change: schema can silently break from an unrelated site update (a theme update, a plugin update, a migration) without anyone noticing until a rich-result feature disappears from search results weeks later.

## Checklist (schema.org validation)

- [ ] Structured-data lint/validation pass run after every schema change
- [ ] All required fields present for every declared schema type, not just the easy ones
- [ ] Datetime fields full ISO 8601 with timezone offset
- [ ] Schema type genuinely matches the page's actual content, never applied purely to chase a rich result
- [ ] Related entities cross-referenced by `@id` where they are the same real-world entity across blocks
- [ ] Tested against the search engine's own structured-data validation tool, not only a generic linter
- [ ] Rich-result appearance monitored over time, not just checked once at implementation

## Deliverable format: Schema Validation Report

```
## Schema Validation Report: [page/site section]

**Verdict:** [one sentence: is the current schema valid, appropriate, and intact]

### Per-page findings
| URL | Schema type(s) declared | Type appropriate? | Required fields complete? | Datetime format OK? | @id cross-references used? |
|---|---|---|---|---|---|

### Rich-result monitoring
- [feature]: appearing as of [date]? [yes/no]. Prior state: [...]

### Fix priority
1. [fix], validation tool used: [...]
```
