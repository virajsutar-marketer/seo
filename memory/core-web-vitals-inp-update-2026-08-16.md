# INP measurement tightened to capture sustained interaction latency; only 55.9% of origins pass all three Core Web Vitals

**Date researched:** 2026-08-16
**Source:** [Core Web Vitals Update 2026: What Changed, What to Fix First](https://webvitals.tools/blog/google-core-web-vitals-update-2026/), WebVitals.tools

## Finding

Google's 2026 update refined the INP (Interaction to Next Paint) measurement methodology to better capture sustained interaction latency on input-heavy pages, rather than just the first interaction, and expanded soft-navigation support in Chrome UX Report (CrUX) for single-page applications. This means heavy filters, chat widgets, personalization scripts, sticky headers, and form logic now show up more clearly in INP scores than before, since teams can no longer optimize only the first interaction and assume the whole page is covered. The March 2026 core update confirmed INP now carries equal ranking weight alongside LCP and CLS. As of the May 2026 CrUX release (published June 9, 2026), only 55.9% of tracked origins pass all three Core Web Vitals thresholds, with roughly 68.6% passing LCP, 81.3% passing CLS, and 86.6% passing INP individually.

## Why it matters for SEO/AEO/GEO work

This updates the `technical-seo-audit` sub-skill's Core Web Vitals fix-priority process: since INP now measures sustained interaction across the whole page lifecycle (not just first input delay), a page with a fast initial LCP/CLS but heavy client-side interactivity later on (filters, personalization, chat widgets) can still fail INP in ways a first-interaction-only test would have missed. When running the TTFB isolation and CWV audit process, test interaction responsiveness on the specific interactive elements a real user would use mid-session, not only the page's initial load. The 55.9% aggregate pass rate is also a useful sanity-check baseline: a site failing one or more Core Web Vitals is currently in the majority, not an outlier, so a failing CWV audit result alone is not evidence a site is unusually broken relative to the web.
