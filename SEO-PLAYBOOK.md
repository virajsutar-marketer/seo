# SEO & Content Growth Playbook (Generic / Any Website, Any Industry)

> **Purpose of this document**: a complete, tool-agnostic operating manual for doing real SEO work — keyword research, technical SEO, content production, AI-answer-engine optimization, internal linking, link building, and root-cause diagnostics — distilled from hands-on engagement work across many real audits, migrations, and content builds. Every rule below is written so that **any AI agent, on any website, in any industry, with no prior context**, can pick it up and execute correctly. Nothing here is tied to a specific company, CMS, plugin, or tool brand — where a specific tool class matters (an SEO scoring plugin, a page-builder, a CDN), it's described generically so the underlying rule survives a tool swap.
>
> Read this top to bottom once, then use it as a reference: jump to the numbered section relevant to the task in front of you.

---

## Table of Contents

1. [Core Operating Principles](#1-core-operating-principles)
2. [Keyword Research Methodology](#2-keyword-research-methodology)
3. [Competitor Gap Analysis](#3-competitor-gap-analysis)
4. [Topical Authority, Content Clustering & Programmatic SEO (pSEO)](#4-topical-authority-content-clustering--programmatic-seo-pseo)
5. [On-Page SEO Checklist & Scoring Discipline](#5-on-page-seo-checklist--scoring-discipline)
6. [Required On-Page Elements & Placement Rules](#6-required-on-page-elements--placement-rules)
7. [AEO / GEO — AI Answer-Engine & Generative-Engine Optimization](#7-aeo--geo--ai-answer-engine--generative-engine-optimization)
8. [E-E-A-T and Trust Signals](#8-e-e-a-t-and-trust-signals)
9. [Internal Linking Strategy](#9-internal-linking-strategy)
10. [Technical SEO: Indexing & Sitemap Health](#10-technical-seo-indexing--sitemap-health)
11. [Technical SEO: Site Performance / Core Web Vitals](#11-technical-seo-site-performance--core-web-vitals)
12. [CMS-Specific Technical Gotchas](#12-cms-specific-technical-gotchas)
13. [Consent / Privacy Tooling Audits](#13-consent--privacy-tooling-audits)
14. [Instant Indexing / Crawl-Acceleration](#14-instant-indexing--crawl-acceleration)
15. [Analytics Data Hygiene](#15-analytics-data-hygiene)
16. [Root-Cause Analysis (RCA) for Ranking/Traffic Changes](#16-root-cause-analysis-rca-for-rankingtraffic-changes)
17. [Link Building / Earned-Mentions Methodology](#17-link-building--earned-mentions-methodology)
18. [Multi-Quarter SEO Program / Roadmap Structuring](#18-multi-quarter-seo-program--roadmap-structuring)
19. [Publishing / QA Workflow Discipline](#19-publishing--qa-workflow-discipline)
20. [Structural Conventions for Injectable Page Content](#20-structural-conventions-for-injectable-page-content)
21. [Engagement Hygiene for an AI Agent Doing Ongoing SEO Work](#21-engagement-hygiene-for-an-ai-agent-doing-ongoing-seo-work)

---

## 1. Core Operating Principles

These cut across every section below — internalize them first:

1. **Never fabricate a number.** Every keyword volume, position, click count, competitor claim, or ranking assertion must trace to a named, checkable data source (analytics export, search-console pull, a live SERP check, a keyword-research tool export). If you don't have the data, say so — don't estimate and present it as fact.
2. **Verify, don't trust a single data source.** Any automated tool's index (rank trackers, keyword tools, even a general web-search tool) can be stale or simply wrong. Before asserting a ranking/competitor claim in a deliverable, cross-check it against a live, real-time source (a direct search, a direct HTTP status check). This single habit prevents the most embarrassing class of SEO reporting error.
3. **Distinguish real signal from artifact before concluding causation.** Bot traffic, tracking-parameter fragmentation, AI-answer-surface positional quirks, and multi-listing SERP features all produce metrics that *look* like real ranking/traffic phenomena but aren't. Isolate the variable before you diagnose.
4. **Render-verify anything visual before calling it done.** Never ship an HTML page, diagram, or visual asset without actually opening it in a browser and looking at it — at both desktop and mobile widths.
5. **A technically "clean" audit does not guarantee a fix worked.** Passing every standard technical check (redirects, canonicals, sitemap coverage) can coexist with a real, sustained ranking loss. Keep investigating secondary factors (usually internal link equity) rather than stopping at "everything passed."
6. **Deliver real, durable artifacts.** A finished report or page is a real file on disk with a real path — not an ephemeral chat preview.
7. **Honesty over polish.** Never backdate a "freshness" signal, never invent a testimonial or stat, never claim a fix "worked" without re-measuring. The discipline that keeps a growth program credible over many months is the same discipline that keeps a single deliverable accurate.

---

## 2. Keyword Research Methodology

### 2.1 Classify every keyword by buyer intent before doing anything else

- Split candidate keywords into two buckets:
  - **Definitional / informational** — "what is X," bare category or concept terms, "how does X work," tutorials, certifications, interview-question round-ups.
  - **Vendor-evaluation / buyer-intent** — the same root term modified by "tool," "tools," "platform," "software," "solution," "service," "company," "agency," or a comparison/superlative frame ("best X," "X vs Y," "X alternatives"). The modifier is the signal: the searcher is already evaluating vendors, not learning a concept.
- **Default to deprioritizing generic definitional terms** once the site's existing content (blog, docs, glossary) already tangentially covers the concept. A dedicated new page for a pure definition has low marginal commercial value — that audience is students/researchers, not buyers. Put build effort into the buyer-intent variant of the same root term instead.
- When a stakeholder claims "we already have this," check whether existing coverage matches the *exact vendor-evaluation phrasing* — a page that explains a concept does not satisfy a searcher typing "[concept] + tool/platform/software."
- Prioritize buyer-intent terms whose modifier matches how the business itself would describe its own product category — those are the easiest pages to write with genuine first-party authority and proof.

### 2.2 Determine "zero visibility" vs. "buried ranking" — the impressions-descending cutoff technique

- Pull search-console query data sorted by **impressions descending** for the exact keyword/URL.
- If the keyword returns rows with real impression counts (even single digits) at any position, the site has **some** presence — it's "buried," not absent. Fix = targeting/authority/internal-linking, not a content gap.
- If the keyword returns **zero rows at all** over a reasonable window (60–90 days), that's the true zero-impression signal — but confirm it isn't a plumbing artifact (see 2.3) before treating it as a genuine content gap.
- **Practical cutoff heuristic**: sort by impressions descending; the row where impressions drop to 1 (or where rows stop entirely) is your evidence boundary. Treat anything past it as noise or true zero, not a signal to build strategy on. This same technique works for full result sets (e.g., pulling the top 5,000 rows sorted by impressions) — if row 5,000 already shows only 1 impression, you have proof the dataset captured everything meaningful; anything absent from that set has genuinely zero impressions.

### 2.3 Cross-check indexing/page-existence before trusting analytics-only absence

- A URL appearing in historical analytics with impressions/clicks is **not** proof the page still exists — always run a live HTTP status check (200 vs. 404 vs. redirect) before building a plan (redirects, content refresh, internal linking) on the assumption it's a live page. Analytics tools report the last state they observed, which can be stale by months.
- A 404, a dead redirect to an unrelated page (category root, blog index), or a redirect to a gated asset all count as "no real public page exists" — a stronger, more actionable finding than a search-console-only absence.

### 2.4 Never fabricate or assume demand — verify every volume claim

- Every keyword volume/position/click figure must trace to a named, checkable source. When two sources disagree (a paid keyword tool shows historical volume but live search-console shows zero impressions), report both, labeled — don't merge and don't pick whichever is more convenient.
- Use **three evidence tiers**, not one merged list:
  1. **Tier A — real, current impressions in the site's own search-console data.** Highest confidence; already being shown, just not converting to clicks. Build here first.
  2. **Tier B — zero current impressions, but real historical/external volume data exists** in a third-party keyword tool. Market wants this; site isn't in the conversation. Build here second.
  3. **Tier C — no hard volume in any dataset, but the phrasing is an emerging category term** the business has genuine authority to speak to. Fold into existing Tier A/B page copy rather than building brand-new speculative pages.
- If a keyword shows strong historical data that has since vanished from current data, that's a **regression** (see [Section 16](#16-root-cause-analysis-rca-for-rankingtraffic-changes)), not an unbuilt content gap — the fix is diagnosing what broke, not writing something new.
- Re-pull volume data before committing to a large content build if the export is more than a few months old.

---

## 3. Competitor Gap Analysis

### 3.1 A "gap" requires two things to both be true

1. A competitor is **verified, live, ranking on page 1** (or near it) for the term.
2. The target site has **zero** presence — not buried, not partial, not "ranks for a related variant." If the target site has any real impression/click data for the term, it's a "buried ranking" problem (fix targeting/authority), not a content gap (build new).
- When scoped literally ("only terms where we have literally nothing"), exclude any keyword with even partial existing visibility, even a single impression, even at a terrible position. Keep those in a separate "fix, don't rebuild" list.

### 3.2 Live-SERP verification beats trusting any rank-tracking tool's index

- A keyword tool's cached snippet or "domain X ranks #N" claim can be stale or wrong. **The concrete failure pattern to guard against**: a tool claims a specific position for a domain, but a live, real-time search of the exact term shows a different domain in that slot, or shows the claimed domain absent entirely.
- Before publishing any "competitor X ranks #Y for term Z" claim, run the actual search live, note the real SERP order, and only report what's actually there. Treat any tool-reported ranking as a hypothesis to confirm, not a fact to repeat.
- The same discipline applies to the target site's own historical content: a URL with impressions/position in analytics is not proof it's still live — run a live status check before building on that assumption.

### 3.3 Reverse-engineer competitor structure, not just spot-check queries

- Pull/crawl representative competitor sitemaps and compare slug/URL-pattern frequency against the target site's sitemap for the same topic buckets. A large frequency gap (competitors have dozens of pages on a topic cluster, target has 0–1) is strong evidence of a structural content-type gap, independent of any single keyword's volume.
- **High-value gap pattern to specifically check**: does the competitor set publish a dedicated "[Competitor] Alternatives" or "vs. [Competitor]" ranked-listicle format for rivals the target site already has deep head-to-head content for? If the target has zero/near-zero coverage of this *specific format* even though the underlying research exists elsewhere, this is one of the highest-leverage, lowest-cost gaps — it repackages existing research into a new intent (broad "alternatives" search differs from narrow "X vs Y" comparison) rather than requiring net-new research.

---

## 4. Topical Authority, Content Clustering & Programmatic SEO (pSEO)

### 4.1 Audit before scaling — page count is not the bottleneck if existing pages don't rank

- Pull cluster-level performance (impressions, clicks, average position) for every existing programmatic content type (glossary pages, vertical/industry pages, integration/partner pages, category pages, etc.).
- If most existing clusters show near-zero clicks, low impressions, and average positions in the 20s–30s+, that's the headline finding, and it changes the recommendation: **fix indexation, internal linking, and sitemap coverage on what's already built before adding more of the same type.** A large net-new build on an unproven foundation repeats the same failure at higher cost.

### 4.2 Diagnose *why* a cluster underperforms — the failure states have different fixes

- **"Undiscovered"/"unknown"** — crawler never found the URL. Root cause: missing sitemap entry, no internal links, or a robots exclusion. Fix = internal linking + sitemap fix.
- **"Crawled but not indexed"** — crawler saw it and chose not to index it. This is a quality/differentiation signal (too similar to something else, too thin), not a discovery problem — resubmitting will not fix this.
- **Internal link equity is a distinct, separately-diagnosable root cause.** A page with exactly one inbound internal link (commonly just its own listing/hub page) tends to decay from "discovered" to "unindexed" over time, even after repeated manual re-submission to indexing APIs. **One additional link is often not enough — multiple genuinely relevant inbound links** (sibling pages in the same cluster cross-linking, contextual links from established content) is the threshold that actually flips a page to indexed, typically resolving within about a day of the link change.
- Before treating an existing organically-ranking page as a real cannibalizing competitor to a new cluster, confirm it's actually live (status-code check) — a page can show impressions/position in analytics while being fully 404'd, meaning it's decaying-but-real demand that should be redirected, not cannibalization.

### 4.3 Cannibalization risk

- Two pages targeting the *identical exact phrase* (not just the same broad topic) split ranking signal instead of stacking it. Check explicitly whenever more than one URL could plausibly target the same query; resolve via canonicalization, consolidation/redirect, or clearly differentiating each page's angle.
- **Stronger check than title/keyword overlap**: run both the existing page's target query and the proposed new page's target query through a real search/answer engine and compare whether the *answers and cited sources* actually overlap. Heavy overlap means one page already covers this ground — expand it rather than splitting a new page off.
- Audit an existing page's actual depth on the specific sub-topic (not just its title) before greenlighting an adjacent new page — a third overlapping asset compounds cannibalization rather than closing a gap.

### 4.4 Gating criteria before scaling any pSEO template

- Any templated/mass-produced page category (an error-message library, a prompts library, a directory of similar entries) carries structural thin-content risk under general search-quality guidance. Gate each instance on "is there real, specific, sourced substance behind this one page" before writing it from a generic template with swapped nouns.
- Sequence pSEO work: fix indexation/internal linking on an existing under-indexed batch **before** scheduling an expansion of that same cluster.
- Resolve any naming/URL-pattern disagreements between shipped implementation and any newer planning document before building a large multi-hundred-URL plan — a mismatch here silently creates duplicate/competing pages or 404s.
- Vary layout, imagery, and section emphasis per page within a cluster while keeping underlying research/rigor consistent — an identical template reused across every entry increases perceived thinness/duplication risk.

---

## 5. On-Page SEO Checklist & Scoring Discipline

### 5.1 Run an on-page SEO scoring tool and enforce a minimum score threshold before anything is "done"

- A numeric score (e.g., 80/100 on whatever on-page checker is in use) forces objective, repeatable quality control instead of subjective sign-off, and catches misses easy to skip under deadline pressure.
- Bake the scoring criteria into the drafting process from the first draft, not as a post-hoc patch. Know which signals the checker weighs heavily and write to them:
  1. Focus keyword at the **start** of the SEO title.
  2. Focus keyword in the meta description (~150–160 characters) and in the URL slug.
  3. Focus keyword as an **exact phrase within the first ~10%** of content (worked naturally into the opening summary).
  4. Meets the target length tier for the content type (e.g., 2,500+ words for pillar content).
  5. Focus keyword in at least one subheading and at least one image alt attribute.
  6. **Keyword density in a healthy band (~0.5–2.5%)** — for a ~2,500-word piece that's roughly 12–15 *natural* exact-phrase mentions, spread across the summary, a few subheadings/bodies, a solution section, a closing section, and an image alt. Never mechanically stuff past the top of that range.
  7. Minimum internal link count (e.g., 3+) and outbound external links; make the single most authoritative external source dofollow (nofollow the rest by default).
  8. A number (e.g., current year) in the SEO title.
  9. Short paragraphs (≤~120 words) and media present in the body.
- Lower-weight or unmeasurable signals (power words, sentiment scores, generic "content AI" scores) can be deprioritized relative to the above — not everything a scoring tool surfaces is equally important.
- Treat sub-threshold scores as **rework, not "ship it anyway."** Retrofit the specific misses until the checker passes.

---

## 6. Required On-Page Elements & Placement Rules

### 6.1 Keyword placement (non-negotiable, every page)

- **H1** — focus keyword always present. This is a primary, distinct signal from the title tag.
- **Title tag** — keyword at/near the start, under the platform's display limit (commonly ~60 characters).
- **First paragraph** — exact keyword phrase within roughly the first 10% of content.
- **At least one subheading** (H2/H3).
- **Meta description** — keyword front-loaded, ~150–160 characters.
- **URL slug** — keyword present, kebab-case.
- **Image alt text** — keyword worked naturally into at least one image's alt.

### 6.2 Internal / external linking

- Minimum internal link count per long-form piece (common floor 3–8), placed **contextually throughout**, never grouped in one spot, pointing to real, live product/solution pages.
- External links only to independent, high-authority sources (analyst firms, standards bodies, government/academic sources, major press) — never a competitor's own blog/marketing content as a citation. One domain cited once per piece; don't recycle the same handful of sources across every post.
- One clearly most-authoritative external source may be dofollow; treat the rest as nofollow by default.

### 6.3 Schema / structured data

- Standard content schema (Article/BlogPosting), FAQPage schema for FAQ sections, Organization + Person/author schema, plus type-specific schema (Product, Review, Event, VideoObject, HowTo, DefinedTerm) where relevant.
- All datetime fields (datePublished, dateModified, uploadDate, event start/end) must be full ISO 8601 **with a timezone offset** — a date-only value trips validation warnings even on an otherwise-valid page.
- Video schema needs a real, reachable thumbnail URL — missing thumbnail is a common validation failure.
- Run a structured-data lint pass (parse every JSON-LD block, check required fields per type) after any schema change.

### 6.4 Breadcrumbs — a deliberate site-level decision, not a default

- If the site/theme template already renders breadcrumbs globally, do **not** duplicate them in page-level content — omit both the visible element and any `BreadcrumbList` JSON-LD in the fragment (a second schema node competes with the theme's own).
- If a site has no site-wide breadcrumb mechanism, per-page BreadcrumbList schema is a legitimate signal. The decision hinges entirely on whether the mechanism already exists elsewhere — never end up with breadcrumbs rendered/declared twice.

### 6.5 CTA placement in long-form content

- Every long-form piece needs at least one **visually distinct, styled CTA callout box** in the body — not a plain inline text link, which reads as an afterthought.
- Place it roughly 75–85% through the piece (just before a closing summary/checklist), supplementing (not replacing) a natural closing-paragraph CTA.
- The CTA's headline/copy must reference the **specific topic** of that piece — a generic "book a demo" defeats the purpose.
- For pages with structured lead-gen forms, place the form **in the hero, above the fold** — a two-column hero (value copy + bullets on one side, form on the other), stacking on mobile so the form still sits near the top.

### 6.6 Real in-content imagery vs. generic stock/flat icons

- In-body images on long-form content should be **real, professional photographs** (people at real screens/workstations, genuine work settings) — not flat-vector/cartoon illustrations, which read as generic/templated and undercut trust.
- Every in-body image should be **unique per piece** — maintain a used-image registry; avoid reusing the same photo or near-identical frame across pieces, and avoid over-relying on one dominant, easily-recognized stock series.
- Images should depict the **literal subject matter** (a specific tool's UI, a specific document type, a specific industry's data) rather than a generic interchangeable "person at a laptop."
- Icons used for UI/decoration (not in-body photography) should be real monoline glyphs in styled containers, never plain colored shapes standing in for icons.

---

## 7. AEO / GEO — AI Answer-Engine & Generative-Engine Optimization

### 7.1 The "gatekeeper" model — 4 factors determine whether an AI answer engine cites a source at all

Miss one and nothing else matters:

1. **Exact topic match**, not adjacent-category match. A page must directly address the *specific* question, not merely sit in the right general subject area.
2. **Concrete, specific, checkable facts stated in plain text** — a real number/price/range rather than a vague CTA or "contact us." Answer engines reward pages that state the actual fact in plain, readable HTML text, not gated behind a form or rendered only via JavaScript/images.
3. **Genuine, current, visibly-dated freshness** — a real, current "last updated" date visible on the page is a cheap, high-leverage lever; stale-dated pages lose citations to more recently updated competitors by a wide margin.
4. **Being retrieved at all** — traditional findability, not an on-page fix. A page must show up in the shortlist an AI system's retrieval step considers before any on-page gatekeeper can matter. Don't over-invest in on-page citation optimization for a page that never gets retrieved — fix findability first.

### 7.2 Secondary differentiators (only matter once all 4 gatekeepers are satisfied)

- Real specifics/technical detail beats vague description.
- One deep, comprehensive page beats several thin pages slicing the same topic.
- Evidence/data-backed claims beat bare assertions.
- **Confident, direct, plainly-stated claims outperform hedged language** ("might," "possibly," "could") by a large margin — state genuinely verified facts plainly; this is not license to overclaim unverified facts.
- Openly naming and comparing real alternatives in long-form content is a citation *advantage* in these systems (subject to any brand policy about competitor mentions on core marketing pages — see [8.2](#82-competitor-mentions-and-comparison-content)).
- **Formatting has surprisingly little independent effect on citation likelihood.** What matters far more is whether the page's actual words/phrasing closely match the specific words/ideas used in the question being asked — a content-specificity fix, not a structural/formatting fix.

### 7.3 How answer engines actually source content

- Cleanly scrapable, plain static HTML text wins over JavaScript-rendered content. If key facts (prices, specs, numbers) are rendered only via JS/images/client-side scripts, an AI system effectively cannot see them and will cite a competitor's page that states the fact in plain HTML instead. Any number/fact that matters for citation must appear in plain, crawlable body text, even if also shown in a richer visual format.
- Query phrasing (not just topic) determines whether a system answers purely from trained knowledge (no live fetch — irrelevant how good the page is) vs. actively performing a live search/fetch (where a well-optimized page can compete). Buyer-intent, comparison, "best X," and product-research queries are far more likely to trigger a live fetch than a bare definitional query — reinforcing why buyer-intent content is disproportionately valuable for AI-citation strategy.
- Citation binds to **text**, not video/audio embeds. Pair any video/rich-media content with full substantive text coverage of the same information.
- There is no secret "ranking algorithm" for AI citation beyond (a) can the system technically read the fact, and (b) does the fact satisfy the gatekeepers above.
- Practical inspection: use browser dev tools (network tab) to inspect the actual raw request/response an AI system's crawler makes against target pages, to verify what it can and can't read — verify directly, don't assume.

### 7.4 Buyer-intent content matters differently for AI-answer surfaces than traditional blue-link SEO

- A page can rank position 1 with high impressions yet earn near-zero clicks because the query is being answered directly by an AI overview/answer surface rather than driving a click-through. Separate this positional artifact from a real CTR problem (see [Section 16](#16-root-cause-analysis-rca-for-rankingtraffic-changes)) rather than "fixing" it with title/meta tweaks.
- Traffic/click volume is not the only KPI for AI-answer-surface work — real AI visibility/citation frequency can rise while session/click volume stays flat, because AI assistants answer directly without sending a click.

### 7.5 Measuring whether a site is genuinely AI-citable

- Track three paired KPIs together, never as a single isolated number:
  1. **Citation frequency** — how often the brand/site is cited across a fixed, representative set of real buyer questions run periodically against multiple AI answer engines.
  2. **Sentiment/accuracy** — whether the AI's description (including facts like pricing/positioning) is actually correct; an inaccurate mention is worse than no mention.
  3. **Citation share** — presence relative to named competitors across that same fixed prompt set.
- Track **breadth of cited pages**, not just total citation volume — rising citations concentrated on a shrinking set of pages is a risk signal (fewer assets the answer engine relies on); diversify deliberately (new clusters, more FAQ/schema coverage, more question-format H2s) rather than just adding volume to the same few pages.
- Branded search volume in search-console data is a cheap leading-indicator proxy for AI-citation-driven awareness (people encounter the brand via an AI answer, then search the name directly).
- Label vendor-published statistics (a tool vendor's own claim about traffic-value multipliers) explicitly as vendor-sourced when citing them in a report — don't treat as neutral.
- Check basic technical blockers first when auditing citation-worthy content: confirm no robots.txt rule inadvertently blocks pages that establish topical/author authority (e.g., an author-bio/entity page).

### 7.6 Snippable, self-contained answer format

- Every key answer should be 1–2 sentences that still make complete sense lifted out of context — AI answer engines and featured-snippet algorithms extract Q&A pairs verbatim.
- **Direct-answer-first**: lead each section with its answer/conclusion, then support it.
- A short "quick answers" block near the top (bolded questions each followed by a 1–3 sentence direct answer) functions as a mini-FAQ engines can lift for snippet-style surfaces.
- Question-format subheadings phrased as the actual question a user would ask, not vague labels ("Learn more," "Overview"). Keep H1, title tag, and meta description aligned to the same underlying intent.
- Match content structure/format to query intent: comparison queries → comparison table; planning/how-to → numbered steps; definitional → concise term-first definition ("X is …").
- Replace vague superlative marketing language ("innovative," "seamless," "cutting-edge") with specific numbers, named benchmarks, or concrete examples.
- No decorative noise that degrades machine parsing (arrow glyphs, star-rating text, exclamation strings, stylistic em/en-dashes). Use real bulleted/numbered lists and tables for structured content.
- **Never hide key answers inside tabs, accordions, or expandable/collapsed UI** — engines generally only reliably read visible, non-interactive HTML.
- Put core information in HTML text, not locked only inside an image or PDF — always pair critical facts with real text and alt text.
- Cover the cluster of related "grounding queries" around a topic (not just the primary keyword) and build hub-and-spoke internal linking so a topic's authority concentrates in one place.
- Keep facts/entities/terminology consistent across text, images, and other media describing the same concept.
- A dedicated FAQ section (FAQPage schema) at the end of long-form content, phrased as literal user questions, each with a self-contained complete-sentence answer — one of the highest-leverage places for both featured-snippet and AI-citation eligibility.

---

## 8. E-E-A-T and Trust Signals

### 8.1 Testimonials, quotes, and case-study claims

- **Never independently source a customer quote/testimonial/named-customer statistic from a live website (or any existing published asset) and repurpose it into different content without explicit sign-off for that specific reuse** — even if the quote is genuinely real and public. Permission scope, current relationship status, or specific-reuse approval may not be visible from the published page alone.
- If a piece needs social proof, either ask for a specific quote/customer to use, or use only material already explicitly supplied for that piece.
- This restriction is specific to **customer-attributed** quotes/claims — citing the company's own already-published product facts, aggregate statistics, or public benchmark data is fine.
- Never fabricate a stat, quote, or claim. Use an explicit placeholder/flag rather than inventing a number, and get it confirmed before publishing.

### 8.2 Competitor mentions and comparison content

- On core marketing/product pages, **do not name competitors and do not include "us vs. them" comparison tables** — let marketing copy stand on the company's own strengths.
- A **neutral, dedicated comparison or listicle piece** (a "best tools in category X" roundup, or a structured head-to-head page/post a user would search for by name) is a different, acceptable category — as long as competitor facts (pricing, features, ratings) are verified via research and accurately attributed, never invented.
- Even within comparison content, never cite a competitor's own blog/marketing material as an authoritative source — cite independent third-party authorities instead.

### 8.3 Honest publish/update dates

- **Never bump or backdate a "published"/"modified" date purely to signal freshness without a real, substantive content edit accompanying it.** Repeated date changes with no real content change is a detectable deceptive-freshness pattern and misleads readers about when the piece was actually produced.
- If a refresh request has no accompanying real content change, decline the pure date bump and flag the concern, or only bump the date alongside a genuine addition.
- Don't add a *visible* "Last updated: [date]" line as a manufactured trust signal — genuine freshness belongs in backend metadata and structured-data `dateModified`, not a cosmetic label.
- Treat any published/last-modified date field as tied one-to-one to actual content edits, full stop — regardless of how the request is phrased.

### 8.4 Avoiding search-engine spam-policy violations (generalized categories)

- **Scaled/templated content abuse** — content produced at scale from templates or generative tooling must carry genuine, original, grounded value in every instance; content produced primarily to manipulate rankings without adding reader value is spam regardless of production method.
- **Doorway pages** — don't spin up many near-identical pages targeting minor keyword variations that all funnel to the same destination; each page must stand on its own substantive merit.
- **Keyword stuffing** — keyword-in-H1/title/meta is legitimate; over-repeating or stuffing variant terms unnaturally is not.
- **Hidden text/links** — never hide text via zero opacity, off-screen positioning, or matching background/text color.
- **Sneaky redirects / cloaking** — never show a search engine different content than what a human sees; never redirect a user somewhere other than expected. Legitimate restructuring with proper redirects is fine; disguising the destination is not.
- **Link spam** — never buy links or manipulate anchor text; legitimate sitemap/indexing submissions are not link building and are fine.
- **Site-reputation abuse / parasite content** — any third-party/sponsored content hosted on the domain must be genuinely moderated, not riding the domain's authority to rank unrelated content.
- **Expired-domain abuse** — never repurpose an acquired/expired domain's residual authority for unrelated content.
- General heuristic for any borderline tactic: *would this help a real user even if search engines didn't exist?* If not, don't do it.

---

## 9. Internal Linking Strategy

### 9.1 Run it as a tracked audit, not an ad-hoc pass

Maintain a flat tracking file (CSV) with one row per link, minimum schema:

| Column | Purpose |
|---|---|
| `source_page_url` / `source_page_id` | page carrying the link |
| `anchor_text` | exact visible text used |
| `target_page_url` | page being linked to |
| `target_cluster` | which content cluster/section the target belongs to |
| `target_prior_status` | target's indexing/ranking state *before* the link (e.g. "unknown," "discovered, not indexed," "ranking, page 3") — needed to later prove the link caused a change |
| `live_verified` | whether you actually confirmed the link is live in rendered HTML, not just "saved to the database" |

### 9.2 Prioritization order for which pages should link to which

1. **Orphan-page rescue first.** Before adding content, audit which existing pages have zero/near-zero internal inbound links. A cluster with a much lower indexation rate than every other section is a strong internal-linking-gap signal, not a content-quality problem.
2. **Topical relevance over convenience.** Only link where the anchor text is a natural, already-true statement in the source content — search existing body copy for real mentions of the target topic first, and turn genuine existing mentions into links. Only add new sentences when no natural mention exists, grounded in verified facts about the target page.
3. **Funnel-stage awareness (hub-and-spoke).** Send links from top-of-funnel/high-traffic informational content down into commercial pages, and link laterally within a cluster (pillar pages ↔ supporting/spoke content) so link equity and crawl signals flow both directions.
4. **Diversify anchor text and targets deliberately.** When one asset could plausibly link to several relevant destinations, vary which target and anchor phrase is used across placements rather than repeating the same exact-match anchor everywhere.
5. **Avoid exact-match keyword stuffing in anchors.** Prefer natural, descriptive, or brand/entity-style anchors over the literal target keyword repeated identically across many links.

### 9.3 Verification discipline

- Confirm a link is live in **rendered HTML** with a cache-busting fetch, not just a successful save response — page caches can serve stale content even after a confirmed database write.
- **Re-check outcomes on a delay (1–2+ weeks)**, don't declare success at time of insertion. A single inbound link is often not sufficient to rescue a fully orphaned/deindexed page — track each target's indexing status before and after; if it doesn't move, escalate to more inbound links from multiple sources rather than assuming one was enough.
- Log every placement in the same tracker so a follow-up audit can distinguish "the link exists and worked," "the link exists but wasn't enough," and "the link never went live" without re-deriving state from scratch.

---

## 10. Technical SEO: Indexing & Sitemap Health

### 10.1 Sitemap structural audit (do this first)

- Fetch the sitemap index and every child sitemap; confirm each returns HTTP 200, correct `text/xml` content type, and a real `<lastmod>` per child.
- Confirm `robots.txt` declares the sitemap and blocks non-indexable paths (admin, search, feeds, unused tag archives, query-string variants).
- Check for **duplicate index submissions** in search console (e.g., a legacy sitemap that now redirects plus the current one) — keep only the canonical one.
- Build a per-cluster inventory table: content type → URL count in sitemap → % actually indexed → dominant "not indexed" reason. This single table is the fastest way to see where crawl equity is/isn't landing.

### 10.2 Finding orphaned pages / under-indexed content types

- Cross-reference the full sitemap URL universe against indexing-API/URL-inspection data (batch-check every URL, not a sample) for an authoritative coverage state per URL.
- Segment not-indexed URLs by *cause*, because the fix differs:
  1. **"Discovered — not indexed" / "unknown," never crawled** — engine knows the URL exists but hasn't allocated crawl budget. This is a **weak internal-linking** problem, not content-quality. Disproportionately hits newer/custom content types lacking inbound links from established pages.
  2. **"Crawled — not indexed"** — engine fetched it and judged it not worth indexing. Genuine content-quality/thin-content/duplicate-value signal (or a rendering problem — see JS-gating below), not linking.
  3. **Stale exclusion state** — index shows an old `noindex` signal from a past crawl even though the live page now serves indexable directives; only needs a re-crawl request.
  4. **Correctly excluded** — utility/transactional paths, thin auto-generated archives, permanently-redirecting pages. These should be `noindex`ed and removed from the sitemap, not chased.
- **The fix for bucket 1 (by far the most common) is always the same lever**: add real contextual internal links from indexed, high-authority pages into the orphaned pages. Sitemap presence alone does not cause indexing. Re-submitting to an indexing API only nudges the crawler; it doesn't substitute for internal links.
- Treat a custom content type with zero entries in any sitemap as its own class of bug — explicitly test its own sub-sitemap URL rather than assuming the main index covers it. Many SEO tools require a manual per-content-type toggle to include it in the sitemap.
- Watch for **JS-gated content**: if a page's actual body content only becomes visible after a user interaction (click-to-reveal, tab switch, lazy render) rather than being present in the initial HTML/DOM, crawlers may see a near-empty page and classify it "crawled, not indexed." Fix by ensuring core content is server-rendered or present in raw HTML.

### 10.3 Crawl-budget pollution audit

- Enumerate every sitemap URL and flag: utility/transactional pages, thin auto-generated taxonomy archives (empty terms), and any URL returning a 3xx instead of 200. A sitemap should contain only 200, canonical, indexable URLs.
- A taxonomy term still in the CMS but with zero associated content typically 404s its own archive — if that URL still gets organic clicks (from old backlinks/cached SERP entries), it's both a pollution and a 404-leakage issue.

### 10.4 404 traffic-leak investigation (root-cause, not just detect)

1. Start from analytics, not a crawler — pull "page not found" pageviews/sessions filtered by page path + referrer + source/medium, to rank broken URLs by actual lost traffic.
2. Classify traffic origin per broken URL:
   - **Organic-search referrer** → the engine still has this URL indexed/ranked; highest priority because it's actively burning ranking equity. Needs a 301 to the closest live equivalent.
   - **Direct / no referrer** → likely an old bookmark, external citation/backlink, or stale internal link. Lower urgency but still worth fixing if volume is non-trivial.
3. Use a historical web-snapshot/archive service to check whether the URL ever served a real 200 page, and when it disappeared — distinguishes (a) a page that existed and was removed without a redirect vs. (b) a URL that never had real content (phantom backlink) needing a generic redirect target.
4. Grep the *live, published* content corpus (not drafts) for the broken path fragment to find which live pages contain the dead internal link — the actual root cause; fix both the redirect AND the source link.
5. Before creating a redirect, check whether the "broken" URL is actually a finished draft that was simply never published — sometimes the fastest fix is publishing at the exact broken slug.
6. Redirect target priority: (a) exact content successor if one exists, (b) closest semantic equivalent, (c) generic hub/category page if no direct equivalent. Always 301 for genuinely dead/moved content.
7. **Verify with a live request after every redirect** — confirm each original broken URL now returns a 3xx to the intended target (or a clean 200 if new content was published at that slug).
8. Note: platform-level automatic old-slug redirects can silently fail to fire if not properly registered or if a caching layer intercepts the request first — don't assume automatic redirect behavior is working; verify live.

### 10.5 Indexing issue vs. ranking issue vs. no-demand issue

Decision framework before recommending any fix:

- **Indexing issue**: URL Inspection shows not indexed at all. No on-page optimization matters until resolved. Fix = internal links + content depth + resolving crawl blockers.
- **Ranking issue**: URL confirmed indexed, has impressions, but sits at a low average position. Relevance/authority/on-page problem — compare against SERP competitors and content depth.
- **No-demand issue**: URL indexed and reasonably positioned but near-zero impressions because the target query has negligible search volume. Don't chase "ranking fixes" for a term nobody searches — verify query volume first.
- Quick discriminator: pull impressions + average position together. Zero impressions + never-crawled = indexing issue. Impressions present + poor position = ranking issue. Impressions present + decent position but no clicks = CTR/SERP-feature issue (a distinct fourth category — see [Section 16](#16-root-cause-analysis-rca-for-rankingtraffic-changes)).

### 10.6 Redirect-chain hygiene

- Audit for redirects pointing to other redirects (chains) rather than directly to the final live URL — each hop adds latency and dilutes link equity.
- Audit for redirect targets that are themselves scheduled for removal or already non-200 — a redirect to a dead page is just a slower 404.
- When migrating a URL structure in bulk, grep the entire internal-link corpus (content + template/header/footer includes) for the old path and fix internal links directly rather than relying solely on the redirect — internal links pointing at a redirect still cost a hop on every crawl and click, at scale.

---

## 11. Technical SEO: Site Performance / Core Web Vitals

### 11.1 TTFB isolation technique (plugin/CMS overhead vs. network/TLS)

The key diagnostic for figuring out *why* server response time is slow before spending effort on the wrong layer:

1. Measure TTFB on a fully dynamic, database-driven page (the full plugin/theme stack rendering).
2. Measure TTFB on a **raw static asset served from the same server/host** (a plain image or static text file requiring no server-side execution) — same domain, network path, TLS overhead.
3. **Subtract.** If the static asset's TTFB is fast but the dynamic page's TTFB is high, the bottleneck is application/plugin/PHP-layer (database queries, plugin hooks, missing page cache) — not network/TLS. If both are similarly slow, the bottleneck is server/network/TLS-level (hosting tier, DNS, TLS handshake, server load), and no plugin optimization will fix it.
4. Cross-check with response headers on the dynamic page: look for a page-cache hit indicator (`X-Cache`, vendor-specific cache-debug headers) and `Cache-Control`. If every request returns `max-age=0` or no cache header, **no full-page cache is actually active**, even if a caching tool shows as "active" in its admin panel — a common false-confidence trap.
5. If TTFB is inconsistent across page templates on the same site (some fast, one class slow), that points to a caching-rule/exclusion gap for that template type, not a global infra problem.

### 11.2 General render-blocking / large-media / lazy-load audit

- Get a full page-weight breakdown by asset type (media, fonts, JS, CSS, HTML) — identify the single largest contributor first. One oversized asset (often an autoplaying hero video/image) can be the majority of total weight and simultaneously the LCP element; fixing it outweighs dozens of micro-optimizations.
- For autoplaying hero media: disable autoplay/preload below a reasonable viewport breakpoint (serve a static poster on smaller screens); re-encode video to a fraction of its original size for mobile.
- Count/inventory render-blocking CSS/JS; identify unused CSS delivered on every load (theme + page-builder + every add-on each contribute a stylesheet, often almost entirely unused on any given page) — removing/deferring it is typically one of the biggest render-time wins available.
- Audit font loading for duplication (same typeface loaded from multiple sources) — consolidate to one, host locally where possible, use `font-display: swap`.
- Audit third-party JS (chat widgets, analytics, social embeds, heatmap tools) for size and defer until interaction/scroll rather than blocking initial render.
- Inventory installed plugins for render-tax culprits: any plugin doing a live string-replace/regex scan on every render, duplicate-functionality plugins, staging-only plugins left active in production.

### 11.3 Cache header verification

- Check `Cache-Control`, `Age`, and any CDN/edge-specific header on every page template type being audited, not just the homepage.
- Absence of a HIT indicator + `max-age=0`/no-cache = full-page caching is not actually active for that page regardless of tool settings claims.
- Where a CDN sits in front of origin, confirm it's actually serving fonts/CSS/JS/images (check headers for the CDN's own signature) — a CDN can be "installed" but only partially wired in (covering static assets but not full HTML pages).

### 11.4 Priority order for CWV fixes (highest ROI first, in practice)

1. **LCP media optimization** — compress/resize/reformat the actual LCP element; disable unnecessary autoplay/preload on mobile. Typically the single largest, fastest win.
2. **Server response time / TTFB** — enable/verify actual full-page caching (not just tool installation) at the object-cache and/or edge layer.
3. **Render-blocking CSS/JS** — remove unused CSS, consolidate/dedupe fonts, defer non-critical JS.
4. **Third-party script deferral** — delay chat/analytics/marketing scripts until interaction.
5. Re-run the same measurement tool after **each** fix to confirm the delta before moving to the next item — don't stack multiple changes and re-measure once, or you can't attribute the gain.

**Reference thresholds**: LCP good ≤2.5s / needs-improvement 2.5–4s / poor >4s. CLS good ≤0.1 / needs-improvement 0.1–0.25 / poor >0.25. Performance score good ≥90 / poor <50 (0–100 scale).

**Tooling note**: if a hosted performance-testing API is quota-exhausted, fall back to running the underlying open-source auditing engine locally against the live URL (headless browser, mobile emulation, throttled network/CPU) for the same metrics without rate limits.

---

## 12. CMS-Specific Technical Gotchas

These are generalized to *any* CMS / page-builder / cache stack, not one specific product:

### 12.1 "The edit saved but didn't render"

Many CMSs have more than one storage location for a single page's content: a generic content field the platform keeps in sync for search/API purposes, and a separate structured/serialized field the actual page-builder or theme template reads from at render time. Editing only the generic field via a REST/API path succeeds, a GET reflects the change, but the **live rendered page shows nothing different** because the template ignores that field.

- **Rule**: before editing any page built with a visual/page-builder tool, determine which field the *renderer* actually consumes (often a JSON/serialized blob distinct from the plain content field) and edit that field specifically.
- **Verification discipline**: never trust "the API returned 200" as proof of a live change. After any programmatic update, re-fetch the field you actually edited from the canonical data store (raw context, not a sanitized read view), then separately verify the rendered live page.

### 12.2 REST update mangles rich HTML

Some CMS write paths run content through a sanitizer/filter before saving. Rich elements (inline scripts/styles, inline SVG, embedded structured-data JSON, base64 data-URI images) can be silently stripped, unwrapped (causing contents to render as literal visible text), or truncated by that sanitizer.

- **Rule**: for content with non-standard/rich embedded markup, don't use a generic "update this field" convenience API if a sanitizing filter sits in its write path. Prefer a direct, authenticated raw write (or the platform's native editor) that bypasses convenience-layer sanitization.
- **Never trust the API's own read-back as ground truth** — some "get" methods return an already-stripped view. Confirm the actual raw/edit-context content matches your intended source before treating either the authored file or the API's returned content as trustworthy.
- **Universal lesson**: always verify rendered output after any programmatic content update — a successful API response is necessary but not sufficient evidence of a live, correct change.

### 12.3 Page cache serves stale content after a DB-level update

A full-page cache (a caching tool, a page-builder's own compiled-output cache, or an edge/CDN cache) can keep serving the pre-edit version well after the database changed — sometimes not just an HTTP-cache-header problem but the application serving a stale compiled copy.

- Caching layers commonly maintain post-type-specific purge lists; a cache-invalidation hook that fires correctly for standard content types may not be registered for custom content types at all.
- A page-builder can maintain its own compiled-output cache independent of any site-wide caching tool — clearing one does not clear the other. If a page still shows old content after clearing one layer, check whether a second, independent layer needs its own explicit purge.
- **Mandatory workflow checklist after any programmatic content update**:
  1. Confirm the write landed at the data-store level (raw/edit-context read).
  2. Identify every distinct caching layer in play (site-wide page cache, page-builder/renderer cache, CDN/edge cache) — don't assume there's only one.
  3. Explicitly purge each relevant layer.
  4. Only then verify the live page — ideally via a request that bypasses remaining cache — to distinguish "didn't save" from "saved but cached."
  5. If a specific content type never reflects edits promptly, flag it as a structural cache-purge gap to fix once at the config level, rather than manually purging on every future edit.

---

## 13. Consent / Privacy Tooling Audits

Goal: determine whether a consent-management banner is functionally wired into tag firing, or merely cosmetically present.

1. **Inspect the page `<head>`/early-loading scripts** for actual consent-signal commands executed *before* any analytics/ad tag-manager script loads. If none exist, no consent default is applied before tags fire — data collection happens regardless of user choice.
2. **Inspect the consent-banner vendor's own script.** It can render a UI, store a preference in local storage, and do nothing else — no data-layer push, no consent-API call, no blocking of tag scripts. If it contains none of the consent-API vocabulary and blocks nothing, the banner is cosmetic.
3. **Inspect the live tag-manager container** for: a consent-default command, integration hooks referencing the consent vendor, and generic built-in consent vocabulary belonging to the tag-manager platform itself (present in every container by default — its mere presence doesn't mean it's actively configured).
4. **Distinguish the failure mode precisely when reporting**: "consent gating fully broken" (data fires regardless of choice — a compliance exposure) is different from "consent gating silently blocks data collection" (compliance fine, analytics undercounts).
5. Note interaction with performance-optimization script delay: if the consent banner itself is deferred (loaded only on first interaction), it may not appear before other tags have already fired — a secondary bug independent of consent logic.
6. **Runtime verification**: once static inspection finds gaps, verify at runtime using a tag-debugging tool and inspect the actual outbound analytics-request's consent-state parameter before vs. after accepting/rejecting — this is the authoritative proof, not just static configuration inspection.

**Fix sequencing:**
1. Enable the CMP's actual consent-mode integration (often a first-class toggle left off by default even when the banner is live).
2. Exclude the CMP's own script from any performance-optimization plugin's delay/defer/minify rules, so it always executes first.
3. In the tag manager, explicitly gate each relevant tag behind the consent signal rather than firing unconditionally.
4. If ad-conversion tracking with identity features is active, ensure those signals are wired to the right consent categories too (basic analytics consent and ad-personalization consent are separate categories, both must be wired).
5. Re-verify at runtime after each change.

---

## 14. Instant Indexing / Crawl-Acceleration

**Where this fits**: always the *last* step, after publishing/updating any URL that matters — it accelerates discovery/crawl scheduling, it does not influence ranking, and is not a substitute for structural fixes (internal linking, content depth). Treat it as a nudge.

1. **IndexNow-style protocol** (one submission reaches multiple search engines): requires hosting a verification key file at a specific path, then POSTing a JSON payload (host, key, key-location, URL list) to the shared endpoint. 200 = validated/accepted; 202 = received, not yet validated.
   - **Critical gotcha**: the key's authorized URL scope is tied to *where the key file is hosted*. A key served from a subdirectory only authorizes URLs under that subdirectory. Always host at the **domain root** unless deliberately scoping to one subdirectory.
2. **Search engine's own indexing API** (submitted independently): typically requires the calling credential to have elevated (owner-level) permission, not just read/viewer access. Has a daily submission quota — batch and prioritize accordingly.
3. **Manual fallback**: "request indexing" in the engine's own webmaster-tools UI, one URL at a time — useful for a single high-priority page.
4. Submit to both mechanisms for the same batch whenever publishing/updating something important — independent systems.
5. Always confirm the URL is actually live/published (not draft) before submitting.
6. **Re-check indexing status days later, not immediately** — this accelerates scheduling, not completion. If a batch still shows no index status after that window, look at internal linking (Section 10) rather than resubmitting repeatedly.

---

## 15. Analytics Data Hygiene

### 15.1 Detecting bot/scraper pollution via cache-busting / debug query parameters

- Bots/scrapers frequently append performance-testing, cache-busting, or debug query-string parameters while **spoofing a legitimate organic-search referrer** — inflating that channel's real numbers.
- **Detection method**: pull the full landing-page-plus-query-string dimension for the suspected channel, and look for a **recurring cluster of specific parameter names appearing together** across many unrelated URLs — a consistent fingerprint, not organic variation, signals a single scraper pattern.
- **Strong confirming test**: check whether polluted paths correspond to a page deliberately excluded from indexing (`noindex`) or otherwise structurally incapable of receiving genuine organic traffic. If a `noindex` page racks up "Organic Search" sessions with the suspicious parameter cluster, that's proof the traffic is synthetic.
- **Quantify precisely per time window** — bot share can vary significantly between windows. State the specific date range and percentage; don't quote an older estimate once a newer overlapping measurement exists.
- The same technique contaminates the **search-query dimension** too (unusually long strings, quote characters, prompt-like phrasing, unexpected script mixes, currency/large-number patterns). Filter before computing aggregate CTR/position metrics.

### 15.2 Query-parameter consolidation to prevent URL-variant fragmentation

- Most analytics platforms offer an "exclude URL query parameters" setting to normalize tracked paths so cosmetic query-string variants of the same page collapse into one reporting row instead of fragmenting.
- List every known non-meaningful parameter (cache-busting/debug flags) while leaving legitimate campaign-attribution parameters (UTM-style) untouched.
- **Understand exactly what this does before promising it fixes anything**: it typically replaces each listed parameter's *value* with a placeholder — it does not strip the key and, critically, **does not remove the underlying bot/scraper sessions from totals.** It's a reporting-cleanliness fix, not a bot-exclusion fix.
- To actually exclude sessions (not just consolidate URL representation), a separate mechanism is needed: a client-side guard suppressing the tracking call when the suspicious pattern is present, or a server/platform-side rule tagging matching traffic as internal/excluded.
- Write access for this kind of config change is commonly restricted (read vs. admin/write API scopes differ) — expect to apply the fix via the platform's own admin UI while documenting the before/after state via the read-only API.
- While doing this pass, also check basic UTM/tracking hygiene independent of bot traffic: malformed UTM source values, and a large volume of sessions with no source/medium attribution ("(not set)").

### 15.3 Comparing time periods

- Prefer comparing **three equal, sequential windows** (e.g., 30-vs-30-vs-30 days) over a single long lookback — reveals trend direction and rules out step-change artifacts (a measurement bulge in the oldest window inflating a headline percentage) that a simple two-point before/after comparison would miss.

---

## 16. Root-Cause Analysis (RCA) for Ranking/Traffic Changes

### 16.1 General process — isolate the variable before concluding causation

1. **State the observed anomaly precisely** (which pages, which date range, which metric moved, by how much) before hypothesizing a cause.
2. **Rule out artifacts before accepting a real-signal explanation.** Common artifact sources, in rough frequency order:
   - **Automated/bot traffic** disguised as organic — check for anomalous parameter patterns, geo/device mixes inconsistent with the expected audience, or session shapes inconsistent with human browsing.
   - **Tracking-parameter fragmentation** — the same logical page/source appearing to "change" simply because URL parameters split what should be one measurement into many.
   - **Brand vs. non-brand query split** — always segment separately. A high brand-query CTR next to a near-zero non-branded CTR on the same site is strong evidence the site converts fine once found — titles/snippets/speed/trust aren't the cause of the non-brand problem; the site simply isn't being found for buyer-intent terms.
   - **AI-answer-surface positional artifacts** — a page/query showing an unusually high (even #1) position with large impressions but near-zero clicks, especially when impressions cluster in tight bursts, position is pinned unnaturally at exactly 1.0 with no variance, device mix is skewed unnaturally (e.g., 100% desktop), or geo mix doesn't match the expected audience. Treat as an inferred fingerprint of automated/AI-surface retrieval (most analytics tools don't label this as a dimension — it must be inferred from data shape). **Exclude these rows before calculating "real" position/CTR performance**, or genuine improvement elsewhere gets masked or offset in aggregate reporting.
3. **Hold one variable constant to test a hypothesis.** The most robust evidence is a **within-page, before/after comparison** across a known change event (a URL migration, template change, content update) — holds content quality/topical relevance constant and isolates the specific change's effect, more reliable than noisy cross-page correlation.
4. **Distinguish "technically flawless" from "actually working."** A migration can pass every standard technical audit (correct redirects, canonicals, index directives, sitemap coverage) and still cause a real, sustained loss. Technical correctness rules out certain causes but doesn't explain a drop by itself — keep investigating secondary factors (typically internal link equity/authority transfer) rather than concluding "it was clean, so nothing is wrong."
5. **Report correlations honestly as directional, not deterministic**, especially with small samples/outliers — state the correlation and flag it as suggestive, relying on the within-page before/after evidence (point 3) as the stronger claim.
6. **Don't conflate "page-1 position" with "ranking success" without checking clicks.** A large share of nominally top-10 positions can receive zero clicks — always check click-through, not just position, before declaring a set of rankings a win.
7. **Never revert a legitimate technical change (redirects, canonicalization) as a "fix" for a correlated ranking drop** unless direct evidence shows the technical change itself is broken. Reverting a clean migration restarts the migration clock and compounds the problem — the correct fix for a link-equity-caused drop is *additive* internal linking, not reversion.
8. **Treat a regression differently from a gap.** A keyword/page that previously had confirmed real rankings/traffic and has since dropped to zero is a **regression** requiring diagnosis of what broke (canonical, redirect, noindex, deindexing fault) — don't file it alongside genuine "never had a page for this" content gaps; the fixes are completely different.
9. **Explicitly separate what has been directly verified** (live status checks, live crawler-simulated fetches, direct data pulls) **from what is inferred or assumed** when reporting — label inferred conclusions as such, and flag any step not yet completed so the audience doesn't over-read confidence into an incomplete analysis.

### 16.2 RCA reporting structure

- **Lead with the verdict, not the data trail.** The first sentence should state plainly whether the premise driving the investigation was even true. Stakeholders should never read five paragraphs to learn whether there's actually a problem.
- **Structure findings into three explicit, labeled tiers:**
  - **Confirmed causes** — root-caused with direct evidence and a concrete fix.
  - **Contributing factors / open questions** — plausible but not fully proven; flag explicitly as unresolved rather than asserting an unverified cause.
  - **Non-issues** — things that look like problems but are explainable by normal mechanics (e.g., a CTR percentage dropping only because impressions grew faster than clicks) or causes outside the system entirely (e.g., a demand-side decline needing a different owner). Calling these out prevents wasted remediation effort.
- **Always re-verify a prior finding against fresh live data before reusing it** — never assume an old diagnosis still holds. Pull the current period's data and re-derive the number rather than repeating an earlier headline.
- Watch for two additional artifact classes specific to reporting:
  - **Multi-listing / SERP-feature CTR artifacts** — a page can show position-1 impressions for a query purely because it's rendering as a sitelink under a different result. Pull the actual query mix before treating a "high position, zero click" page as a CTR-fix opportunity; any automated CTR-gap tool unaware of multi-listing SERPs will overstate recoverable clicks.
  - **Vanity impressions from generic/adjacent queries** — a page can show huge impression volume spread across hundreds of loosely related queries that don't match its actual target intent. Judge real performance only on the intended target term(s).
  - **Answer-engine capture as a non-fixable CTR cause** — when a page ranks well but has near-zero CTR even with a strong title, check whether the SERP is giving a synthesized/direct answer before any organic link shows. If so, a title/meta rewrite won't move CTR — restructure the on-page answer (crisp quotable block, FAQ structure) to compete for the answer/citation slot instead.
- **Close every RCA with an explicit "why this matters" / "how to apply going forward" section** — state what a naive reading of the same data would have gotten wrong, and give a repeatable checklist (e.g., "always segment traffic on X before quoting growth") so the next person inherits the discipline, not just the one-time conclusion.

---

## 17. Link Building / Earned-Mentions Methodology

### 17.1 Evaluate inbound reciprocal/exchange opportunities systematically

- Score each candidate placement (a "best/top N tools" roundup, listicle, directory-style page) on: topical relevance to the specific target page, the host page's own traffic/authority signal, and whether the format matches proven high-citation formats for that query type (named-entity lists, comparison tables, pricing, FAQ).
- Map each opportunity to the *most topically matched* page on your own site — don't send every placement to the same flagship page. Vary the target landing page and anchor phrase across placements from the same partner; an identical anchor+target pair sent to many pages creates a detectable, penalizable pattern.
- **Ask for a subset, not the full inventory offered.** Request only the top 4–6 highest-value placements rather than every available slot — taking everything from one source is itself a footprint signal.
- **Keep the reciprocal side deliberately light.** If a link exchange is proposed, give back one editorial-context link (a blog/resource page, not a product/marketing page), never sitewide. Reciprocal linking at scale is a recognized link-scheme risk regardless of relevance — asymmetry (getting more than you give, giving from low-commercial-value pages) is the safer posture.
- Only pursue exchanges with real topical overlap; skip off-topic or link-farm-style directories even if they offer to link back.

### 17.2 Prioritize link-building channels by controllability and asset leverage

- Third-party "best tools" roundup inclusion (pitch the strongest, most fact-dense page — e.g., real named comparisons/testing data — as the pitch asset).
- Guest appearances / podcast placements tied to a subject-matter spokesperson with existing public presence — lower volume, higher trust per placement.
- Journalist/press pitches built around genuinely original data/analysis already possessed (a proprietary study, benchmark, internal dataset) rather than generic commentary — original data is what gets picked up.
- Purpose-built "linkable assets" (a citable original chart, calculator, or dataset) proactively pitched for outreach, not just reacting to inbound offers.
- Treat link building as the program's typically weakest/slowest-moving stream and plan accordingly: diversify across channels so no single channel's slippage sinks the target; log realistic monthly targets, not aspirational ones.

---

## 18. Multi-Quarter SEO Program / Roadmap Structuring

### 18.1 Maintain one canonical "state of the engagement" document

Every session should start by reading it. It should contain, in one place:
- Every deliverable produced, with a one-line description of what it contains and its current status (applied live / drafted, not yet applied / superseded).
- A running "Done this engagement" list and a running "Pending / Next" list, updated in place rather than re-derived.
- Explicit callouts when a later finding *corrects* an earlier one — note "corrects the prior assumption that X" rather than silently overwriting, so the history of why the plan changed is preserved.
- Cross-references to related trackers/CSVs/reports so no single document has to contain everything, but the index always points to the current version of the truth.

### 18.2 Sequence the program in phases — state the sequencing itself as a principle

1. **Technical/indexation health first** (crawlability, duplicate tracking, indexing status, orphan pages, cannibalization) — content and link-building investment is wasted on pages that can't be crawled, indexed, or properly measured.
2. **Fix what already ranks before scaling new content** (title/meta/CTR rewrites, on-page restructuring for existing high-impression pages) — the highest-confidence, fastest lever because it monetizes demand already there, versus new content that takes weeks to earn any position.
3. **Then scale net-new content production** (organized by funnel stage: bottom-of-funnel/commercial, middle-of-funnel gated assets, top-of-funnel informational), built on a small number of proven, human-reviewed templates rather than one-off pages, so volume scales without a quality drop.
4. **Link building runs in parallel but is explicitly named the weakest signal** — least controllable stream (outreach-dependent) — but start early because it has the longest lead time.

### 18.3 Structure quarterly/period plans with

- A one-page executive summary: headline result, honest caveats (what part of any "win" is real vs. inflated by since-corrected data or deliberate content pruning), committed numbers for the next period.
- A current-state table (actuals, period-over-period), explicitly distinguishing genuine growth from base-effect or cleanup-driven swings.
- A workstream breakdown by funnel stage/type (content, technical, links, AEO/citation) with an owner and a stated guardrail for any programmatic/at-scale work (e.g., "every templated page passes individual human review; an index-coverage anomaly pauses the batch immediately").
- A calendar/cadence mapping specific weeks to specific shipped items, so the plan is falsifiable against a real publish log.
- A measurement plan naming every metric, its data source, its check cadence, and its owner.
- A risks/mitigations table naming concrete risks (seasonal algorithm-update windows, a slipping metric, an underperforming outreach channel, execution capacity) each with a stated mitigation and priority-order fallback if capacity tightens.
- **Explicit projection honesty**: state which numbers are conservative math vs. optimistic assumptions; note new pages typically take many weeks to earn ranking and should only be credited a fraction of their eventual value in near-term projections; flag any known risk window (historical algorithm-update seasons) as a stated downside scenario rather than ignoring it.

---

## 19. Publishing / QA Workflow Discipline

### 19.1 Render-verify before declaring anything done

- **Never share, push, or publish any custom visual (HTML page, diagram, chart, image composite) without first rendering it in an actual browser and visually inspecting it** — zoomed in on details, not just a glance. Presentation matters as much as substance: spacing, alignment, cropping, whether "icons" are real icons (not colored placeholder shapes).
- Render at **both desktop and true mobile width** — a fixed-width container can visually clamp/hide overflow that would otherwise break the live responsive layout; use a script-based overflow probe in addition to eyeballing (a narrow browser window can render inaccurately at very small emulated widths).
- For pages destined for an existing CMS/theme, also render against a simulated "hostile" version of the target theme's global styles (competing color/line-height rules) to catch collisions a clean local render would hide.
- Fix issues found, re-render, and only then treat the piece as ready to ship — a hard gate, not optional polish.

### 19.2 Deliver finished, production-ready artifacts on disk

- Save a complete, standalone, self-contained file (full document structure, all styling/scripting inlined, no dependency on external hosting unless that's the actual target) to a real location on disk, and hand over that file path.
- Avoid delivering only through an ephemeral hosted-preview mechanism when the actual need is ownership of the underlying file — a hosted preview link doesn't substitute for a durable, editable file the recipient can open and redistribute on their own terms.

### 19.3 Never touch a "final" timestamp without a real underlying change

- Restated from Section 8.3 as a workflow gate: the check is enforced at the point of any date-field write, not just at content-review time.

---

## 20. Structural Conventions for Injectable Page Content

### 20.1 Self-contained "body-only" fragments for CMS insertion

- When a new page/block is meant to be pasted into an existing CMS template (which already supplies global nav, header, footer), deliver **body-only** markup — no duplicated `<nav>`, header, or `<footer>`, typically no `<!DOCTYPE>/<html>/<head>/<body>` scaffolding either.
- All CSS must be **scoped under a single wrapper class** specific to that fragment — never bare global element selectors (`body`, `a`, `h1`, `section`, `*`) — the fragment will be dropped into a page whose existing theme/global styles will otherwise cascade in and collide.
- Where the host theme is known to aggressively override styling (heading fonts/colors, link colors, button text color, image sizing), lock the fragment's critical properties with `!important` at the scoped-class level rather than assuming plain CSS will win the cascade. Don't rely on CSS custom properties resolving correctly on the host page — provide literal fallback values.
- Keep the fragment responsive on its own (mobile breakpoints included) since it renders inside the live, already-responsive host page.

### 20.2 Inline SVG instead of icon-font / web-component icon tags

- Use inline `<svg>` markup for all icons in injectable content, never custom icon-font elements or icon web components depending on a runtime `<script>` or external stylesheet/CDN.
- **Why**: content destined for a rich-text field or page-builder/HTML-to-builder conversion pipeline commonly has its `<script>` tags and custom elements **stripped** during conversion/paste — any icon depending on a script or web-component tag silently disappears, while inline SVG paths survive because they're just markup.
- Practical pattern: author the icon as raw SVG path data, strip hardcoded root `width`/`height`, set `fill`/`stroke` to `currentColor` so it inherits surrounding text color, size purely via CSS relative to font-size.

---

## 21. Engagement Hygiene for an AI Agent Doing Ongoing SEO Work

### 21.1 Check memory/prior research before re-deriving an analysis or building a recurring asset from scratch

- Before starting any recurring task (a report format, content template, data pipeline, scoring rubric), search prior session records/notes for an already-established, previously-approved approach. If one exists, follow it exactly rather than approximating a "good enough" substitute — silently improvising a near-miss version of an already-agreed method is a real quality failure, producing rework and eroding trust. If none exists, build one and explicitly record it as the new standard.

### 21.2 Operate token-/cost-conscious and assume high scrutiny on every deliverable

- Do the cheap verification steps (confirm data sources exist, check for a prior approved method, sanity-check a headline number) **before** committing to expensive multi-step work — this avoids paying the expensive cost twice.
- Avoid visible trial-and-error in front of the reviewer; debug/probe quietly and efficiently rather than iterating live.
- When a task has real breadth (many similar pages/reports/assets), prefer careful sequential execution over blind mass-parallel fan-out when a single early mistake could otherwise compound across every unit of output before anyone catches it.
- **Being cost-conscious means cutting waste** (redundant redos, unverified loops, re-deriving known facts) — it never means cutting corners on substance (real citations, real data verification, real quality bar). Assume the reviewer is technical, reads closely, and has low tolerance for rework: precision and accuracy beat speed or padding every time.

### 21.3 Scoping discipline

- When a stakeholder narrows or corrects the scope of a request (e.g., "only show me X, excluding Y"), apply that scope literally and re-derive the deliverable rather than lightly editing the previous, broader version — a scope correction is a signal the previous framing was actually wrong for the decision being made, not merely a preference.
- When in doubt about whether a finding belongs in scope, err toward a separate, clearly-labeled section rather than either silently including it or silently dropping it.

---

*End of playbook. This document is intended to be extended over time — as new patterns, gotchas, and disciplines are discovered in real engagements, they belong here in generalized form (no company names, no specific URLs), filed under the most relevant existing section or as a new numbered section if the topic doesn't fit anywhere above.*
