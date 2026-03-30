# SEO + AEO Audit — dominion.digital
**Date:** 2026-03-30
**Auditor:** Claude Code (SEO-AEO Skill)
**URL:** https://dominion.digital

---

## Executive Summary

- **CRITICAL BUG:** Canonical tag outputs `http://localhost:4321/` on every page — Google will not index the real domain until fixed
- **Zero AI/SEO infrastructure:** No robots.txt, no sitemap, no schema markup, no llms.txt — all four are missing
- **Strong foundation:** SSR content in HTML source, good title/meta, keyword-aligned copy — once the infrastructure is fixed, this site is well-positioned

---

## Traditional SEO Findings

### On-Page

| Element | Status | Notes |
|---------|--------|-------|
| Title tag | PASS | "dominion.digital \| Kansas City Digital Marketing Agency" — keyword-rich |
| Meta description | PASS | 157 chars, includes keywords + soft CTA ("results or you don't pay") |
| H1 | PASS | Present in HTML source — SSR confirmed |
| H2 structure | PASS | Multiple H2s per service section — semantic hierarchy looks correct |
| Canonical URL | FAIL | Points to `http://localhost:4321/` — critical indexing failure |
| Open Graph tags | MISSING | No og:title, og:description, og:image — social shares will be unformatted |
| Robots meta tag | N/A | Not present (acceptable, defaults to index/follow) |

### Technical

| Check | Status | Notes |
|-------|--------|-------|
| HTTPS | PASS | Vercel provides valid TLS |
| SSR rendering | PASS | Key content present in raw HTML — fully crawlable |
| robots.txt | MISSING | 404 — bots have no crawl guidance |
| sitemap.xml | MISSING | 404 — Google/Bing cannot discover pages |
| Canonical tag | CRITICAL | `http://localhost:4321/` on every page — fix is adding `site` to astro.config.mjs |
| Favicon | PASS (partial) | /images/logo-icon.png referenced — verify this file exists in public/images/ |
| Internal linking | NOT AUDITED | Only homepage built currently |
| Core Web Vitals | NOT MEASURED | PageSpeed API unavailable in this environment — run manually at pagespeed.web.dev |

### Local SEO

| Check | Status | Notes |
|-------|--------|-------|
| "Kansas City" in title | PASS | |
| "Kansas City" in description | PASS | |
| Local keywords in H2s | PASS | Each service section targets a GBP category name |
| NAP (Name/Address/Phone) | MISSING | Not visible in footer — add before any local citations |
| Google Business Profile schema | MISSING | No LocalBusiness schema on homepage |

---

## AI Visibility (AEO) Findings

| Check | Status | Notes |
|-------|--------|-------|
| robots.txt AI bot rules | MISSING | No file — unknown if default allows all |
| GPTBot allowed | UNKNOWN | No robots.txt to inspect |
| ClaudeBot allowed | UNKNOWN | No robots.txt to inspect |
| PerplexityBot allowed | UNKNOWN | No robots.txt to inspect |
| llms.txt | MISSING | 307 redirect (no file) — AI crawlers have no structured map |
| FAQPage schema | MISSING | FAQ section exists in HTML but no schema — AI can't reliably cite it |
| Organization schema | MISSING | No entity recognition signal for AI knowledge graphs |
| LocalBusiness schema | MISSING | No structured location/service data for AI citations |
| Answer blocks | PARTIAL | Copy is direct and punchy, but not formatted as Q&A answer blocks |
| SSR (crawlable) | PASS | Content fully in HTML — AI crawlers can read it |

---

## Schema Audit

**Result: NO SCHEMA FOUND**

Zero JSON-LD present on the homepage. This is a significant gap for both Google rich results and AI citation eligibility.

Priority schema to add:
1. `Organization` — entity recognition, Knowledge Panel signals
2. `LocalBusiness` — maps to GBP, enables local AI citations
3. `FAQPage` — maps directly to the existing FAQ section
4. `WebSite` — enables sitelinks search box in Google

---

## llms.txt Status

**Result: MISSING**

No `llms.txt` or `llms-full.txt` at the domain root. AI crawlers (ChatGPT, Perplexity, Claude) use this file to understand site structure. With only a homepage built currently, creating a basic llms.txt now establishes the pattern for all future pages.

---

## Prioritized Action Plan

### Quick Wins (fix before next crawl — these block indexing)

1. **Fix canonical URL** — Add `site: 'https://dominion.digital'` to `astro.config.mjs`. This is the single most important fix. Without it, Google reads every page as localhost.

2. **Add robots.txt** — Create `public/robots.txt` explicitly allowing all AI bots. Default behavior may block them.

3. **Add sitemap** — Install `@astrojs/sitemap`, add to astro.config.mjs. Submit to Google Search Console and Bing Webmaster Tools.

4. **Add Organization + LocalBusiness + FAQPage schema** — Add JSON-LD to the homepage. Unlocks rich results and AI citation eligibility immediately.

5. **Add llms.txt** — Create `public/llms.txt` with site overview and page map.

### Medium Priority (this month)

6. **Add Open Graph tags** — og:title, og:description, og:image in Layout.astro for all pages.

7. **Add NAP to footer** — Full business name, city/state, phone number visible on every page for local SEO signal and citation consistency.

8. **Submit to search consoles** — Google Search Console + Bing Webmaster Tools. Verify domain, submit sitemap.

9. **Title tag keyword order** — Consider flipping to "Kansas City Digital Marketing Agency | Dominion Digital" — primary keyword first gets heavier weight.

### Long-Term (as pages are built)

10. **Add BreadcrumbList schema** to all non-homepage pages as they're built.
11. **Add Article schema** to any blog/guide pages.
12. **Reformat content as answer blocks** — direct Q&A structure at section openings for AI citation eligibility.
13. **Earn first-party citations** — BBB, Chamber of Commerce, KC business directories for local E-E-A-T.
14. **Submit to Bing Webmaster Tools** — ChatGPT and Copilot index via Bing.
15. **Track AI citation rate** — test brand queries monthly in ChatGPT, Perplexity, Gemini, Claude.

---

## AI Visibility Score (Baseline)

| Platform | Score | Notes |
|----------|-------|-------|
| Google AI Overviews | 0/3 | No schema, no sitemap, canonical broken |
| ChatGPT / Copilot | 0/3 | No robots.txt, no llms.txt, no Bing submission |
| Perplexity | 0/3 | New site, no external citations yet |
| Claude | 0/3 | No llms.txt, no structured data |
| **Overall** | **0/12** | Baseline — all infrastructure missing |

**Target in 90 days after fixes:** 6–8/12

---

## Files to Create

- [ ] `astro.config.mjs` — add `site: 'https://dominion.digital'`
- [ ] `public/robots.txt` — allow all bots including AI crawlers
- [ ] `public/llms.txt` — AI-readable site map
- [ ] Schema JSON-LD — add to `src/layouts/Layout.astro` or `src/pages/index.astro`
- [ ] Sitemap — via `@astrojs/sitemap` integration
