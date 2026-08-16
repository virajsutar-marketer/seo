---
name: aeo-geo-citations
description: "Answer Engine Optimization and Generative Engine Optimization: the 4-gatekeeper citation model, machine-readability audits, direct-answer-first content patterns, FAQ/schema for AI eligibility, and a repeatable AI-visibility measurement loop. Use when the user asks to get cited by ChatGPT, Google AI Overviews, Perplexity, or Claude, or asks why a page ranks well but earns no AI citations."
user-invocable: true
license: MIT
metadata:
  author: virajsutar-marketer
  version: "1.0.0"
  category: seo
  parent_sections: "SEO-PLAYBOOK.md Section 7, full AEO-GEO-GUIDE.md"
---

# AEO / GEO: Getting Cited by AI Answer Engines

A narrower, deeper slice of `SEO-PLAYBOOK.md` Section 7 and the full `AEO-GEO-GUIDE.md`. Read both in full before running this on a real task; this file operationalizes them into a step-by-step process.

## When to use this skill

- Someone asks how to get a brand or page cited by ChatGPT, Google AI Overviews, Perplexity, or Claude.
- A page ranks well in traditional search but shows no AI-citation presence.
- Someone asks to measure or track "AI visibility."
- A page's key facts might be technically invisible to a retrieval crawler.

## Why this is a different discipline than traditional SEO

Traditional SEO optimizes for a ranking algorithm that returns a list of links a human then clicks. AEO/GEO optimizes for a retrieval-plus-synthesis pipeline: an AI system decides whether to search/fetch external content at all, which pages to pull into context, and which facts to actually state or cite. A page can dominate traditional rankings and never get cited, and vice versa. Click-through is not the success metric here; citation frequency, accuracy, and share are (see the measurement loop below). The unit of competition is a fact or claim, not a whole page.

## Process

### 1. The 4-gatekeeper model, miss one and nothing else matters

1. Exact topic match, not adjacent-category match. A page must directly address the specific question, not merely sit in the right general subject area.
2. Concrete, specific, checkable facts stated in plain text: a real number, price, or range rather than a vague CTA or "contact us." Answer engines reward pages that state the actual fact in plain, readable HTML text, not gated behind a form or rendered only via JavaScript/images.
3. Genuine, current, visibly-dated freshness. A real, current "last updated" date visible on the page is a cheap, high-leverage lever; stale-dated pages lose citations to more recently updated competitors by a wide margin.
4. Being retrieved at all: traditional findability, not an on-page fix. A page must show up in the shortlist an AI system's retrieval step considers before any on-page gatekeeper can matter. Do not over-invest in on-page citation optimization for a page that never gets retrieved; fix findability first.

Secondary differentiators only matter once all four gatekeepers are satisfied: real specifics beat vague description, one deep comprehensive page beats several thin pages on the same topic, evidence-backed claims beat bare assertions, confident plainly-stated claims outperform hedged language ("might," "possibly," "could") by a large margin, and openly naming/comparing real alternatives in long-form content is a citation advantage in these systems (subject to any brand policy on competitor mentions, see playbook Section 8.2). Formatting has surprisingly little independent effect on citation likelihood; what matters far more is whether the page's actual words closely match the specific phrasing used in the question being asked.

### 2. Determine whether a live fetch even happens for this query class

- Pure knowledge/definitional queries ("what is X") are frequently answered from the model's trained parametric knowledge with no live search; no page, however well-optimized, gets a look-in. Do not over-invest AEO effort chasing these.
- Time-sensitive, comparative, transactional, or "best/top/vs" queries are far more likely to trigger a live search/fetch, because the model cannot reliably know current pricing, current best-in-class rankings, or current availability from training data alone. This is why buyer-intent, comparison, and pricing-adjacent content is disproportionately valuable for AEO.
- Practical test: run the target query against the AI system in question, phrased multiple ways, and observe whether citations/sources appear, and whether they change between runs (live fetch) versus stay identical (cached/parametric answer). If sources never appear for a query class no matter how the page is optimized, the fix is a different query strategy, not better content on that page.

### 3. Machine-readability audit

- Plain, static, server-rendered HTML text is the ground truth for most retrieval crawlers and fetch tools, which frequently use lightweight fetchers, not full headless browsers.
- Every fact that matters for citation (price, spec, number, date, name) must exist in the raw HTML response, not only in an image, a client-side chart, or a PDF with no accompanying text summary.
- Verify directly: fetch the page with a plain HTTP client (no JS execution) and diff what comes back against what a browser renders. Any material difference is a citation blind spot.
- Avoid interaction-gated content for anything citation-critical: accordions, tabs, "read more" truncation, and hover-reveal content are frequently invisible to non-interactive fetchers.
- Confirm `robots.txt` does not inadvertently block the user-agents used by AI crawlers/retrieval systems from pages that matter (author/entity pages, pricing pages, comparison pages). Re-check this periodically since AI crawler user-agent lists change over time.
- Consider a machine-readable content manifest (a plain-text or markdown summary of key pages and facts at a well-known path) as a low-cost way to give retrieval systems a clean, high-density source. Keep it factual and current; it needs the same freshness discipline as any other page.

### 4. Write for citation-eligible content patterns

- Direct-answer-first: front-load each section's conclusion, then support it. AI summarization consistently favors extracting the first clear, complete-sentence claim in a block of text.
- Self-contained, quotable claims: name the subject explicitly rather than relying on a pronoun referring to something two sentences up.
- Specificity beats hedging: "reduces X by 40% in Y conditions, per [source]" beats "may help improve X." State genuinely known facts plainly; reserve hedged language for claims that are actually uncertain. This is a citation-eligibility lever, not license to overstate.
- Replace vague superlative language ("industry-leading," "innovative," "best-in-class") with a specific number, a named competitor comparison, a certification, or a cited third-party benchmark.
- A short "quick answers" block near the top (bolded questions each followed by a 1 to 3 sentence direct answer) functions as a mini-FAQ engines can lift for snippet-style surfaces.
- Question-format subheadings phrased as the actual question a user would ask, not vague labels.
- Match content structure to query intent: comparison queries get a comparison table, planning/how-to queries get numbered steps, definitional queries get a concise term-first definition.
- No decorative noise that degrades machine parsing (arrow glyphs, star-rating text, exclamation strings). Use real bulleted/numbered lists and tables for structured content.
- Never hide key answers inside tabs, accordions, or expandable/collapsed UI.
- Keep facts/entities/terminology consistent across text, images, and other media describing the same concept; inconsistency across modalities reduces a system's confidence in extracting a clean answer and can cause it to skip the source entirely.
- A dedicated FAQ section (FAQPage schema) at the end, phrased as literal user questions, each with a self-contained complete-sentence answer, is one of the highest-leverage places for both featured-snippet and AI-citation eligibility.

### 5. Structured data for AI-answer eligibility

FAQPage schema on genuine FAQ sections, Article/BlogPosting schema with accurate datePublished/dateModified (full ISO 8601 with timezone offset), Organization schema with accurate `sameAs` links for entity disambiguation, Person/author schema where authorship matters for trust, and Product/Review/HowTo/DefinedTerm schema only where the content type genuinely matches. Run a structured-data lint pass after any schema change; a broken or incomplete block is often silently ignored rather than partially credited.

### 6. Measure AI visibility on a fixed cadence

1. Build a fixed prompt bank: 20 to 50 real buyer/user questions representative of the actual target audience, not just the brand name. Keep exact wording stable across periods so results are comparable.
2. Run the same prompt bank against multiple AI systems on a fixed cadence (for example monthly) and log per prompt per system: citation frequency (was the brand mentioned at all), sentiment/accuracy (was it mentioned correctly, a confidently wrong mention is worse than no mention), which specific page was cited (source diversity), and citation share versus named competitors.
3. Track a leading-indicator proxy in traditional analytics: branded search volume/trend, which often rises when people encounter the brand via an AI answer and search the name afterward.
4. Re-run the exact same prompt bank after any major content change to attribute cause and effect, holding the prompt set constant.
5. Label any vendor-published AI-traffic statistic explicitly as vendor-sourced when citing it externally.

Track breadth of cited pages, not just total citation volume. Rising citations concentrated on a shrinking set of pages is a risk signal; diversify deliberately (new clusters, more FAQ/schema coverage, more question-format H2s) rather than adding volume to the same few pages.

## Checklist (AEO/GEO pre-publish add-on)

- [ ] Every citation-critical fact (price, spec, number, date) exists in plain server-rendered HTML, not only in JS/image/PDF
- [ ] No citation-critical content hidden behind an accordion/tab/hover state
- [ ] At least one direct-answer-first paragraph or "quick answers" block near the top
- [ ] FAQ section (if present) uses FAQPage schema and literal, self-contained Q&A pairs
- [ ] Claims are stated plainly and confidently where genuinely verified, no unnecessary hedging
- [ ] robots.txt does not block the crawler/user-agents relevant to AI retrieval systems for this page
- [ ] Facts are consistent across text, images, and any video/media on the page

## Deliverable format: AI-Citation Audit / Brief

```
## AI-Citation Audit: [page or topic]

**Verdict:** [is this page currently citable, and if not, which gatekeeper is failing]

### Gatekeeper check
1. Topic match: [pass/fail, why]
2. Concrete facts in plain HTML: [pass/fail, which facts are missing/gated]
3. Freshness: [visible last-updated date, genuinely current or stale]
4. Retrievability: [confirmed retrieved in a live test, or never appears]

### Machine-readability findings
- [fact]: visible in plain HTTP fetch? [yes/no]. Located in: [HTML text / image only / PDF only / accordion]

### Measurement loop results (prompt bank run on [date])
| Prompt | System | Cited? | Accurate? | Page cited | vs. competitor |
|---|---|---|---|---|---|

### Fix priority
1. [fix], gatekeeper addressed: [1-4]
```
