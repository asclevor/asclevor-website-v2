# Full SEO Audit — Asclevor (localhost:5173 / www.asclevor.com)

**Date:** 2026-09-15 · **Scope:** 4 routes (`/`, `/pricing`, `/api`, `/contact`) · **Business type:** SaaS (health-tech / clinical knowledge API)

---

# SEO Health Score: 41 / 100 🔴

| Category | Weight | Score | Weighted |
|---|---|---|---|
| Technical SEO | 22% | 55 | 12.1 |
| Content Quality | 23% | 45 | 10.4 |
| On-Page SEO | 20% | 50 | 10.0 |
| Schema / Structured Data | 10% | 15 | 1.5 |
| Performance (CWV) | 10% | 20 | 2.0 |
| AI Search Readiness | 10% | 35 | 3.5 |
| Images | 5% | 40 | 2.0 |

*Scores are conservative because the site is pre-launch on a dev server; production header/CDN behavior is unverified.*

## Executive summary

Asclevor is a well-designed 4-page SaaS marketing site with clean SSR HTML — and it currently sabotages itself in three compounding ways:

1. **Two of four pages carry a competitor's brand.** The homepage and contact page ship Cursor's title tags and meta descriptions (plus a wrong-brand image alt). This is the single most damaging issue on the site — for search, for AI answer engines, and for any human who notices.
2. **~37.6 MB of uncompressed media** (14 MB and 6.9 MB autoplaying videos with `preload="auto"`, multi-MB PNGs) guarantees failing Core Web Vitals.
3. **The site is nearly invisible to machines**: no sitemap, no canonicals, no Open Graph, zero structured data, no llms.txt, and 95–215 words of content per page — nothing for a search engine or LLM to cite.

The good news: the design, information architecture, and SSR foundation are solid, and every Critical/High fix is less than a day of work combined.

## Top 5 critical issues
1. Homepage `<title>` + meta description are Cursor's (`src/routes/+page.svelte:11-12`)
2. Contact page `<title>` + meta description are Cursor's (`src/routes/contact/+page.svelte:44-48`)
3. 21 MB of autoplay video downloaded on page load (`ImgSlot.svelte`: `preload="auto"`, no poster)
4. No sitemap.xml (404) and no canonical tags anywhere
5. Hero image alt text says "Cursor app screenshot"

## Top 5 quick wins (all under 2 hours combined)
1. Rewrite the two wrong-brand titles/descriptions (10 min)
2. Fix the hero alt text (1 min)
3. Add `static/sitemap.xml` + `Sitemap:` line in robots.txt (15 min)
4. Create one 1200×630 OG image and add OG/Twitter tags + canonicals via a shared head component (45 min)
5. Convert the 5 PNGs to WebP and re-encode both MP4s (~60 MB → ~3 MB total) (45 min)

## Category reports
Detailed findings per category in `findings/`:
`technical.md` · `content.md` · `on-page.md` · `schema.md` · `performance.md` · `geo.md` · `sxo.md` · `images.md`

## Synthesis (10-principle framework)

**PERCEIVE** — The site is externally polished but internally inconsistent: rendered HTML is excellent (SSR, semantic, alt-texted) while machine-facing layers (metadata, schema, sitemap) are absent, and two pages still speak in another product's voice.

**ANALYZE** — THINK: a page's strongest entity signal is its title/description; those currently assert "Cursor," so every downstream system (Google, LLMs, humans) receives a contradictory first fact. CONNECT-system: the metadata fix unblocks GEO scoring, brand queries, and CTR together; the media fix unblocks CWV *and* image SEO; sitemap depends only on canonical URLs being decided first.

**VALIDATE** — FEEL: for a *clinical* product, trust is the conversion bottleneck — wrong-brand copy and zero compliance signals fail the gut check of the exact buyer persona. ACCEPT (falsifiability checks): if after the metadata fix brand-query impressions don't appear in GSC within 4 weeks of deploy, the issue is indexing, not metadata. If LCP lab scores stay >2.5s after media re-encoding, the bottleneck is fonts/JS, not media.

**ACT** — CREATE: the missing assets are enumerated in the action plan (sitemap, OG image, schema, llms.txt). GROW (leading indicators to watch without re-auditing): GSC impressions for "asclevor", LCP from PageSpeed API after deploy, and AI-engine answers for "what is Asclevor".

## Priority buckets

### 🔴 Critical — fix immediately (blocks brand/indexing)
- Replace Cursor titles + descriptions on `/` and `/contact`
- Fix wrong-brand hero alt text
- Fix video preload (`preload="metadata"` + posters) and compress media

### 🟠 High — within 1 week
- Canonical tags on all pages
- sitemap.xml + robots.txt `Sitemap:` directive
- Organization + SoftwareApplication JSON-LD
- OG/Twitter card tags + 1200×630 OG image
- Convert PNGs → WebP/AVIF, add lazy loading + dimensions
- Begin depth work: code sample + endpoint list on `/api`; compliance strip on `/` and `/api`

### 🟡 Medium — within 1 month
- WebSite, ContactPage JSON-LD
- llms.txt
- Prerender static routes (`prerender = true`)
- Security headers at the production host; confirm apex→www 308
- Expand homepage copy past ~300 words with outcomes/proof; add in-body internal links
- Trim font weights; consider self-hosting

### 🟢 Low — backlog
- Remove invalid `<meta name="text-scale">`
- Custom `+error.svelte` 404 page
- Optional FAQPage schema (no SERP feature since May 2026 — entity value only)
- apple-touch-icon; move stray PNGs out of project root
- Plan a content hub (blog/changelog/use cases) on the main domain

## Method note
- `claude-seo` Python runtime not installed → analysis ran inline (curl renders + source inspection); screenshot/visual capture skipped; no Google API or backlink credentials configured, so no field CWV/indexation/backlink data. Re-run after deploy for production-accurate numbers.
