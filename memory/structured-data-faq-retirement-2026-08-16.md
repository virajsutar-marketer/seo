# FAQ rich results retired from Google Search; schema shifts from SERP-display trigger to AI trust signal

**Date researched:** 2026-08-16
**Source:** [Google Is Not Diminishing The Use Of Structured Data In 2026](https://www.searchenginejournal.com/google-is-not-diminishing-the-use-of-structured-data-in-2026/560516/), Search Engine Journal

## Finding

Google removed support for the practice-problem structured-data type in January 2026 (dropped from Search Console rich-result reporting, the Rich Result Test, and Search-appearance filters). The March 2026 core update reduced rich-result display for several schema types that were widely abused, including FAQ, Review, and How-To on non-primary content pages. As of May 7, 2026, FAQ rich results stopped appearing in Google Search entirely, with the FAQ search appearance, rich-result report, and Rich Results Test support dropping in June 2026. Google's own position, per the article, is that this does not diminish the value of structured data overall; it shifts what structured data is used for, from a SERP-display trigger toward an AI trust and entity-verification signal.

## Why it matters for SEO/AEO/GEO work

This directly affects the `schema-structured-data` and `aeo-geo-citations` sub-skills' guidance to add FAQPage schema for citation eligibility: FAQPage schema is still worth implementing for the reasons in `AEO-GEO-GUIDE.md` Section 5 (entity disambiguation, machine-parseable Q&A pairs for AI retrieval), but nobody should promise a client a FAQ rich snippet in classic Google Search results as of mid-2026; that specific SERP feature is gone. Anyone auditing an older SEO plan that lists "FAQ rich results" as an expected win needs to update that expectation and reframe the deliverable around AI-citation eligibility rather than blue-link SERP enhancement.
