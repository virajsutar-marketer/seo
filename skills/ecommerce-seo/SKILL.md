---
name: ecommerce-seo
description: "E-commerce SEO: category-page content strategy, faceted-navigation indexing control, product schema and inventory sync, out-of-stock handling, and pagination strategy. Use for any site with a product catalog, category/collection pages, and a purchase flow."
user-invocable: true
license: MIT
metadata:
  author: virajsutar-marketer
  version: "1.0.0"
  category: seo
  parent_sections: "SEO-PLAYBOOK.md Section 23"
---

# E-Commerce SEO

A narrower, deeper slice of `SEO-PLAYBOOK.md` Section 23. Read that section in full before running this on a real task. Applies to any site with a product catalog, category/collection pages, and a purchase flow.

## When to use this skill

- Someone asks for an e-commerce SEO audit or a category-page content strategy.
- Faceted navigation is generating duplicate-content risk.
- A product's schema, pricing, or availability data looks out of sync.
- An out-of-stock or discontinued product page needs a decision on whether to redirect or keep live.

## Process

### 1. Prioritize category pages over individual product pages for non-branded traffic

Category pages are the primary SEO asset for e-commerce for most non-branded, higher-volume commercial queries ("[category] for [use case]," "best [category] under [price]"), since a searcher looking for a category of product is rarely searching for one specific SKU by name. Prioritize category-page depth and optimization before product-page optimization for non-branded traffic capture.

Category pages need genuine, unique on-page content beyond a product grid: a real intro paragraph explaining the category, genuine buying-guide content, real FAQs specific to that category. A category page that is purely a filtered product list with zero unique text is thin content and struggles against a competitor's category page with real editorial content around the grid.

### 2. Control faceted/filter URL sprawl

Filter combinations (color by size by price range, and so on) can generate an effectively unbounded number of near-duplicate, low-value URL variants that both waste crawl budget and create massive duplicate-content exposure. Use canonical tags pointing filtered variants back to the base category URL, and/or robots.txt/parameter-handling rules to prevent crawling of low-value filter combinations, while still allowing genuinely valuable, high-search-volume filter combinations (a specific, frequently-searched size or color) to be indexed as their own canonical page if real demand data supports it.

### 3. Product schema and inventory sync

Product schema (`Product` type with `Offer`, `AggregateRating`, `Review`) is close to mandatory: it enables rich-result price/availability/rating display, which meaningfully lifts CTR independent of ranking position. Keep price and availability fields in the structured data synced in real time with actual inventory/pricing systems; a rich result showing stale pricing or "in stock" for an out-of-stock item is a trust and conversion problem the moment the searcher clicks through.

### 4. Write unique product descriptions, never manufacturer boilerplate

Never publish a product page with purely manufacturer-supplied boilerplate description duplicated verbatim across every retailer selling the same product; this is a textbook duplicate-content problem at internet scale and a real differentiation opportunity. A genuinely unique description, real customer-usable details (fit, sizing, real use-case guidance), and real photos/video of the actual product both avoid the duplicate-content problem and out-compete other retailers running unchanged manufacturer copy.

### 5. Handle out-of-stock and discontinued products without losing equity

Never let an out-of-stock page silently 404 or disappear if it has real accumulated ranking/backlink equity. Keep it live with clear "out of stock" messaging and either a restock-notification signup or genuine alternative-product recommendations. Only fully remove/redirect a product URL once it is confirmed permanently discontinued, redirecting to the closest current equivalent product or the parent category (see the redirect-target priority logic in the `technical-seo-audit` sub-skill).

### 6. Use real reviews and user-generated content

Reviews, real customer photos, and Q&A sections on product pages are both a conversion-rate lever and a fresh, unique-content lever that manufacturer boilerplate cannot replicate. Never fabricate or seed fake reviews; this is both a platform-policy violation on most review systems and a straightforward trust violation.

### 7. Set a deliberate pagination indexing strategy

Category-page pagination (page 2, 3, 4) needs a clear indexing strategy: either self-canonical each paginated page (appropriate when each page's product set could plausibly match distinct long-tail queries) or canonical all pages back to page 1 (appropriate when deep pagination pages have little independent search value). Pick one strategy deliberately and apply it consistently rather than leaving pagination indexing to inconsistent default behavior.

### 8. Additional structural checks

Site search result pages should generally be excluded from indexing (noindex or blocked in robots.txt); indexed internal site-search URLs create thin, low-quality, often near-duplicate pages at scale. Marketplace/feed-based structured data (for sites also syndicating to third-party marketplaces or shopping feeds) must stay in sync with on-site structured data; divergent pricing, availability, or product identifiers between on-site schema and the syndicated feed is a data-integrity problem that can trigger platform-level penalties independent of organic SEO impact. Seasonal/limited-time category pages should follow the same never-let-good-equity-404 discipline as discontinued products: prefer updating the same evergreen URL in place year over year over creating a new dated URL each cycle, unless there is a genuine reason the content must be a permanent historical snapshot.

## Checklist (e-commerce SEO)

- [ ] Category pages have genuine unique content, not just a product grid
- [ ] Faceted/filter URLs canonicalized or blocked to prevent duplicate-content sprawl
- [ ] Product schema present with price/availability synced to real inventory in real time
- [ ] Product descriptions are unique, not manufacturer boilerplate duplicated site-to-site
- [ ] Out-of-stock pages kept live (not silently 404'd) unless permanently discontinued
- [ ] Pagination indexing strategy chosen deliberately and applied consistently
- [ ] Site-search result pages excluded from indexing
- [ ] No fabricated or seeded reviews

## Deliverable format: E-Commerce SEO Audit

```
## E-Commerce SEO Audit: [site/category]

**Verdict:** [one sentence: strongest actionable finding]

### Category page findings
- [category]: unique content present? [yes/no]. Faceted URL count in index: [N]

### Product schema / data integrity
- [product set]: schema present? [yes/no]. Price/availability sync verified: [yes/no, method]

### Out-of-stock / discontinued handling
- [product]: current state: [live with messaging / 404 / redirected]. Recommended action: [...]

### Pagination strategy
- Current approach: [self-canonical / canonical to page 1 / inconsistent]. Recommendation: [...]

### Fix priority
1. [fix]
```
