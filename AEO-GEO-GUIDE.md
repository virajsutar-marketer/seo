# AEO/GEO Deep-Dive: Getting Cited by AI Answer Engines

> A focused expansion on **Answer Engine Optimization (AEO)** and **Generative Engine Optimization (GEO)** — the discipline of making a website's content retrievable and citable by AI systems (chat assistants, AI Overviews, answer boxes, agentic browsing/research tools), as distinct from ranking a blue link in traditional search. Read [`SEO-PLAYBOOK.md`](./SEO-PLAYBOOK.md) §7 first for the core gatekeeper model — this file goes deeper on implementation.

---

## 1. Why AEO/GEO is a different discipline than traditional SEO

Traditional SEO optimizes for a **ranking algorithm** that returns a list of links a human then clicks. AEO/GEO optimizes for a **retrieval + synthesis pipeline**: an AI system decides (a) whether to search/fetch external content at all, (b) which pages to pull into its context window, and (c) which facts from those pages to actually state or cite in its answer. A page can dominate traditional rankings and still never get cited, and vice versa. Three consequences follow:

- **Click-through is not the success metric.** A user can get a complete, satisfying answer without ever visiting the source page. Citation frequency, citation accuracy, and brand mention are the metrics that matter (see §6).
- **The unit of competition is a fact/claim, not a page.** An AI system assembles an answer from fragments across multiple sources — you're competing to be the source of a specific sentence, not to "win" the whole query.
- **Freshness and plain-text machine-readability matter more, formatting matters less** than classic on-page SEO wisdom suggests. See §3.

---

## 2. The retrieval question: does a live fetch even happen?

Before any on-page optimization matters, determine whether the target query class triggers a live search/fetch at all:

- **Pure knowledge/definitional queries** ("what is X") are frequently answered from the model's trained parametric knowledge with no live search — no page, however well-optimized, gets a look-in. Don't over-invest AEO effort chasing these.
- **Time-sensitive, comparative, transactional, or "best/top/vs" queries** are far more likely to trigger a live search/fetch, because the model can't reliably know current pricing, current best-in-class rankings, or current availability from training data alone. **This is why buyer-intent, comparison, and pricing-adjacent content is disproportionately valuable for AEO** — it's the content category most likely to actually get fetched.
- **Practical test**: run the target query against the AI system in question, phrased multiple ways, and observe whether citations/sources appear at all, and whether they change between runs (indicating a live fetch) versus staying identical (indicating a cached/parametric answer). If sources never appear for a query class no matter how the page is optimized, the fix is a different query strategy, not better content on that page.

---

## 3. Machine-readability: what a retrieval system can actually see

- **Plain, static, server-rendered HTML text is the ground truth for most retrieval crawlers and fetch tools.** If a fact only appears after client-side JavaScript execution, many retrieval systems (which frequently use lightweight fetchers, not full headless browsers) will never see it.
- **Every fact that matters for citation (price, spec, number, date, name) must exist in the raw HTML response**, not only in an image, a chart rendered client-side, or a PDF with no accompanying text summary.
- **Verify directly**: fetch the page with a plain HTTP client (no JS execution) and diff what comes back against what a browser renders. Any material difference is a citation blind spot.
- Avoid interaction-gated content for anything citation-critical: accordions, tabs, "read more" truncation, and hover-reveal content are frequently invisible to non-interactive fetchers. If it matters, it should be visible in the initial DOM.
- **`robots.txt` and crawler access**: confirm no rule inadvertently blocks the user-agents used by AI crawlers/retrieval systems from the pages that matter (author/entity pages, pricing pages, comparison pages). A blocked page cannot be cited regardless of content quality. Periodically re-check this — crawler user-agent lists change over time as new AI systems launch.
- **Consider a machine-readable content manifest** (a plain-text or markdown summary of a site's key pages and facts, served at a well-known path) as a low-cost way to give retrieval systems a clean, high-density source to pull from — this pattern is emerging specifically to solve the JS-rendering and noise problem described above. Keep it factual and current; treat it as another page that needs freshness discipline, not a one-time artifact.

---

## 4. Content patterns that win citations

### 4.1 Direct-answer-first structure
Every section should front-load its conclusion, then support it. AI summarization consistently favors extracting the first clear, complete-sentence claim in a block of text — bury the answer under three sentences of throat-clearing and it's likely to be skipped in favor of a competitor's page that states it plainly.

### 4.2 Self-contained, quotable claims
A sentence that requires the reader to have already read the previous three sentences to make sense is unsuitable for extraction. Write claims that stand alone: name the subject explicitly rather than relying on a pronoun referring to something two sentences up.

### 4.3 Specificity beats hedging
"May help improve X" loses to "reduces X by 40% in Y conditions, per [source]." State genuinely known facts plainly and confidently; reserve hedged language for claims that are actually uncertain. This is a citation-eligibility lever, not a license to overstate — a plainly-stated false claim is worse than a hedged true one.

### 4.4 Numbers, named entities, and comparisons over adjectives
Replace "industry-leading," "innovative," "best-in-class" with a specific number, a named competitor comparison, a certification, or a cited third-party benchmark. Vague superlative language is both low-citation-value and a general content-quality smell.

### 4.5 FAQ blocks phrased as real questions
A FAQ section with genuine, specific, literally-phrased user questions (not generic prompts) each followed by a complete, self-contained answer is one of the highest-density citation surfaces on a page — it's already pre-chunked into exactly the Q→A pairs a retrieval system wants.

### 4.6 Comprehensive single pages over fragmented series
A retrieval system pulling from one authoritative page that covers a topic in full depth has an easier time producing a coherent answer than stitching together three thin pages. When in doubt between splitting a topic into a series or writing one comprehensive page, prefer comprehensive — matches the topical-authority guidance in the main playbook (§4).

### 4.7 Visible, genuine freshness signals
A real, current, visibly-stated last-updated date (backed by an actual edit, not manufactured — see main playbook §8.3 on the freshness-honesty rule) is one of the cheapest, highest-leverage levers available. Stale-dated pages lose citation share to more recently updated competitors even when the underlying facts haven't materially changed.

### 4.8 Consistency across modalities
If a number, name, or claim appears in body text, an image, and a video transcript describing the same thing, keep them identical. Inconsistency across modalities on the same page reduces a retrieval/synthesis system's confidence in extracting a clean, singular answer — and can cause it to skip the source entirely in favor of one with internally consistent facts.

---

## 5. Structured data & schema for AI-answer eligibility

- **FAQPage schema** on genuine FAQ sections — pairs the visible Q&A content with a machine-parseable version of the same structure.
- **Article/BlogPosting schema** with accurate `datePublished`/`dateModified` (full ISO 8601 with timezone offset — a date-only value trips validation warnings even on an otherwise-correct page).
- **Organization schema** with accurate `sameAs` links to verified profiles (this is one of the stronger entity-disambiguation signals available — it tells a retrieval system which real-world entity this domain corresponds to).
- **Person/author schema** on any page where authorship matters for trust (attributed guides, expert commentary) — an author entity with a real bio and a consistent identity across pages is a trust signal that compounds; a byline with no backing entity is close to worthless.
- **Product/Review/HowTo/DefinedTerm schema** where the content type genuinely matches — don't force a schema type onto content that isn't actually that type; mismatched schema is a spam signal, not a citation booster.
- Run a structured-data lint pass (parse every JSON-LD block on the page, verify required fields per type) after any schema change — a broken or incomplete schema block is often silently ignored rather than partially credited.

---

## 6. Measuring AI visibility (the AEO/GEO equivalent of rank tracking)

There is no single universally-agreed "AI SEO score." Build your own measurement loop:

1. **Build a fixed prompt bank** — 20–50 real buyer/user questions representative of your actual target audience's information needs (not just your own product name). Keep the exact wording stable across measurement periods so results are comparable over time.
2. **Run the same prompt bank against multiple AI systems on a fixed cadence** (e.g., monthly) and log, per prompt per system:
   - Was the brand/site mentioned at all? (**citation frequency**)
   - Was it mentioned accurately? (**sentiment/accuracy** — a confidently wrong mention is worse than no mention; flag and try to correct the source of the error)
   - Which specific page/URL was cited, if any? (**source diversity** — track this across the whole prompt bank; if citations concentrate on 2–3 pages out of a large site, treat that as a risk, not a win, and deliberately build/improve more citable pages)
   - How did the brand compare to named competitors in the same answer? (**citation share**)
3. **Track a leading-indicator proxy in traditional analytics**: branded search volume/trend. A rise in direct brand-name searches with no corresponding marketing spend increase often correlates with people encountering the brand via an AI answer and searching the name afterward to verify/learn more.
4. **Re-run the exact same prompt bank after any major content change** to attribute cause and effect — treat this the same way you'd treat before/after RCA methodology in traditional SEO (see main playbook §16): hold the prompt set constant, change one thing, remeasure.
5. **Label any vendor-published AI-traffic statistic explicitly as vendor-sourced** when citing it externally — don't treat a tool vendor's own marketing claim about "AI answer traffic value" as an independent, neutral benchmark.

---

## 7. Common AEO/GEO failure modes (and their fixes)

| Failure mode | How it shows up | Fix |
|---|---|---|
| Content only rendered via JS | Plain HTTP fetch of the page returns near-empty body | Server-render or statically pre-render citation-critical facts |
| Key facts locked in an image/chart | A price, spec, or stat is only visible as a graphic | Restate the fact in plain HTML text near the image, with matching alt text |
| Facts hidden behind interaction | Accordion/tab/hover content invisible to non-interactive fetchers | Make citation-critical content visible in the default DOM state |
| Stale "last updated" date | Page hasn't been genuinely touched in a long time, freshness signal is absent or clearly outdated | Genuinely update the content (see main playbook §8.3 — never fake this) |
| Hedged, vague language | "May help," "could improve," "innovative solution" | Replace with specific, confidently-stated, checkable facts |
| Citations concentrated on 1–2 pages | Measurement loop (§6) shows the same URL cited across most of the prompt bank | Build out more topically-adjacent, individually citable pages/FAQ sections rather than funneling everything to one asset |
| robots.txt blocks a key page | The page never appears as a citation despite strong content | Audit and fix crawl access for the relevant user-agents |
| Inconsistent facts across page/image/video | The same stat differs between the body copy and an infographic on the same page | Reconcile to one canonical, current number everywhere it appears |
