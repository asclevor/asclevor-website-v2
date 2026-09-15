# Image & Media SEO — localhost:5173 (Asclevor)

**Score: 40/100**

## Alt text: 8/8 present ✓
Quality issues:
- `Hero.svelte`: `alt="Cursor app screenshot"` — **wrong brand**, and doesn't describe content ("Asclevor clinical knowledge base interface" would be accurate + keyword-bearing)
- `Features.svelte`: "Mission Control", "Cloud agents" — feature names only; expand to describe what's shown
- Video elements: no alt equivalent needed, but no `poster` (see performance.md)

## File optimization
| File | Size | Target | Saving |
|---|---|---|---|
| api-hero.png | 2.3 MB | WebP ~150 KB | −93% |
| hero-app.png | 1.9 MB | WebP ~130 KB | −93% |
| leander-guo.png | 1.1 MB | WebP ~25 KB | −98% |
| cloud-agents.png | 784 KB | WebP ~60 KB | −92% |
| mission-control.png | 612 KB | WebP ~50 KB | −92% |
| case-search.mp4 | 14 MB | H.264/VP9 ~1.5 MB | −89% |
| everywhere.mp4 | 6.9 MB | H.264/VP9 ~1 MB | −86% |

Total media: ~37.6 MB → **~3 MB achievable**.

## Missing attributes & features
- No `loading="lazy"` on any image/video
- No `width`/`height` (CLS risk)
- No `fetchpriority="high"` on hero LCP images
- No WebP/AVIF pipeline (`@sveltejs/enhanced-img` or `vite-imagetools` would automate this)
- No dedicated OG image asset (1200×630, <300 KB) for social/AI previews
- No apple-touch-icon (favicon is data-URI SVG only)

## Housekeeping
Two ~1MB screenshots ("Pasted 2026-09-15…png") sit in the project root — move out of the deployable directory.
