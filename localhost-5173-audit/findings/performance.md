# Performance (Core Web Vitals) — localhost:5173 (Asclevor)

**Score: 20/100**

Lab estimates only (local dev server; no CrUX field data exists for an unaudited/launch-stage domain). Dev-server numbers understate production, but asset weights are deployment-independent.

## Estimated page weight

| Asset | Size | Issue |
|---|---|---|
| `case-search.mp4` | **14.0 MB** | `preload="auto"` + autoplay → downloads immediately on `/` |
| `everywhere.mp4` | **6.9 MB** | Same pattern, also on `/` |
| `api-hero.png` | 2.3 MB | LCP candidate on `/api`, unoptimized PNG |
| `hero-app.png` | 1.9 MB | LCP candidate on `/`, unoptimized PNG |
| `leander-guo.png` | 1.1 MB | An avatar. 1.1MB. |
| `cloud-agents.png` | 784 KB | Unoptimized PNG |
| `mission-control.png` | 612 KB | Unoptimized PNG |
| Google Fonts CSS | render-blocking | 2 families × 8 weights, no `font-display` control beyond `display=swap` (present ✓) |

**Homepage ships ~23 MB of media.** LCP will exceed 2.5s even on fast connections; mobile will be far worse.

## Findings

### 1. Autoplay videos with `preload="auto"` and no poster — CRITICAL
`src/lib/components/ImgSlot.svelte` renders `<video autoplay loop muted playsinline preload="auto">` with **no `poster`**. Browsers begin downloading the full MP4 as soon as the element mounts.
**Fix:** `preload="metadata"`, add a compressed `poster` (WebP), `loading="lazy"`-equivalent via `contenteditable`-free intersection-observer gate or Svelte `{#key}`/`IntersectionObserver` so video only loads in-viewport, and re-encode to ≤1080p H.264/VP9 (~1–2 MB target). 21 MB → ~3 MB is realistic.

### 2. Oversized PNGs served as-is — HIGH
No compression pipeline (no `vite-imagetools`, no `@sveltejs/enhanced-img`). Convert to WebP/AVIF (70–90% size cut), add `loading="lazy"` + `decoding="async"` for below-fold, and `width`/`height` attributes (ImgSlot sets none → CLS risk inside `.img-slot` if container aspect isn't fixed).
**Avatar special-case:** `leander-guo.png` at 1.1 MB should be ~15–30 KB WebP at display size.

### 3. Render-blocking Google Fonts — MEDIUM
Two families, 8 weights loaded from `fonts.googleapis.com` in `app.html`. Trim to used weights (audit actual usage), keep `preconnect` (present ✓), and add `font-display: swap` via the CSS2 API (already `display=swap` ✓). Self-hosting via `vite-plugin-fonts`/fontsource would remove a third-party round-trip.

### 4. No width/height on media — MEDIUM (CLS)
`ImgSlot.svelte` `<video>`/`<img>` carry no intrinsic dimensions. If `.img-slot` doesn't reserve aspect-ratio, layout shifts as media loads. Set explicit `aspect-ratio` on `.img-slot` or width/height attributes.

### 5. Images above the fold lack `fetchpriority="high"` — LOW
Hero image is the LCP element on `/` and `/api`; add `fetchpriority="high"` (and skip lazy-loading for it).

### 6. Prerendering — LOW
See technical.md: `prerender = true` → CDN-cached HTML, better TTFB.
