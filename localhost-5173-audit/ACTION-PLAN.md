# Action Plan — Asclevor SEO (41/100)

Dependency order matters: decide canonical URLs (P2-1) before sitemap (P2-2); fix metadata (P1-1) before OG tags (P2-4) since both live in the same head component.

## Phase 1 — Critical Fixes · Week 1 (~2 hrs)

| # | Item | Files | Effort |
|---|---|---|---|
| 1.1 | Replace Cursor title/description on `/` — e.g. `Asclevor — Clinical Knowledge Infrastructure` + accurate description | `src/routes/+page.svelte` | 10 min |
| 1.2 | Replace Cursor title/description on `/contact` | `src/routes/contact/+page.svelte` | 5 min |
| 1.3 | Fix `alt="Cursor app screenshot"` → Asclevor-accurate alt | `src/lib/components/Hero.svelte` | 2 min |
| 1.4 | Videos: `preload="metadata"`, add compressed poster, load only in viewport; re-encode both MP4s (~21 MB → ~2.5 MB) | `src/lib/components/ImgSlot.svelte`, `static/images/*.mp4` | 60 min |
| 1.5 | Convert 5 PNGs → WebP (esp. 1.1 MB avatar → ~25 KB) | `static/images/` | 45 min |

**Falsifiability check:** after deploy, PageSpeed LCP should drop below 2.5s on `/`. If not, bottleneck is fonts/JS — proceed to 3.5.

## Phase 2 — High-Impact Improvements · Weeks 2–3 (~1 day)

| # | Item | Notes |
|---|---|---|
| 2.1 | Canonical URLs | `<link rel="canonical">` on every page; standardize on `https://www.asclevor.com/...` |
| 2.2 | Sitemap | `static/sitemap.xml` with all 4 URLs + `Sitemap:` line in robots.txt |
| 2.3 | JSON-LD: `Organization` (+`sameAs` socials) site-wide; `SoftwareApplication`+`offers` on `/` and `/pricing` | see findings/schema.md for copy-paste blocks |
| 2.4 | OG + Twitter tags via shared `<Meta>` component; create one 1200×630 OG image (<300 KB) | unblocks decent Slack/X/LinkedIn previews |
| 2.5 | `/api` depth: add one curl example, endpoint list, auth note in HTML | biggest SXO gap for technical buyers |
| 2.6 | Compliance strip (SOC 2 / HIPAA-eligibility / data sourcing) on `/` and `/api` | #1 objection for clinical buyers + E-E-A-T signal |
| 2.7 | Image loading: `loading="lazy"` + `width`/`height` in ImgSlot; `fetchpriority="high"` on heroes | CLS + LCP |

## Phase 3 — Content & Authority · Month 2

- Expand homepage to 300+ words with concrete outcomes (coverage stats, data sources, customer proof)
- Expand the pricing FAQ pattern to `/api` (genuine Q&A → also the only citable-passage format on site today)
- Add `llms.txt`; add `WebSite` + `ContactPage` schema
- Decide content-hub strategy: blog/changelog/use-case pages on `www.asclevor.com` (subdomains don't build main-domain authority)
- Optionally self-host fonts / trim to used weights

## Phase 4 — Monitoring & Iteration · Ongoing

- Deploy → verify SSR output + headers in production (HSTS, nosniff, Referrer-Policy; apex→www 308)
- Google Search Console: submit sitemap; track impressions for "asclevor" (4-week check)
- PageSpeed Insights monthly on all 4 routes
- Ask ChatGPT/Perplexity "What is Asclevor?" monthly — watch entity accuracy improve after metadata + schema fixes
- Re-run `/seo audit` after production deploy (this audit's field-data gaps: CWV, indexation, backlinks)
