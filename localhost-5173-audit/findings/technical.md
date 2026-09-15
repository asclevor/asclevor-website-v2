# Technical SEO — localhost:5173 (Asclevor, SvelteKit)

**Score: 55/100**

## What works
- Full SSR HTML on all 4 routes (`/`, `/pricing`, `/api`, `/contact`) — content is crawlable without JS execution (SvelteKit SSR default). All routes return 200.
- `robots.txt` present and valid (`User-agent: * / Disallow:` — allows all).
- `<html lang="en">` set in `src/app.html`.
- Favicon present (inline SVG data URI).
- Single `Vary: Origin`, no redirect chains within the app.
- No `noindex` tags anywhere (all pages indexable).

## Findings

### 1. No XML sitemap — HIGH
`/sitemap.xml` returns 404. For a 4-page site this is quick to fix and helps discovery + hreflang-free canonical consolidation. Add a static `static/sitemap.xml` or a `src/routes/sitemap.xml/+server.js` endpoint, then reference it from robots.txt.

### 2. robots.txt missing `Sitemap:` directive — MEDIUM
Once the sitemap exists, add `Sitemap: https://www.asclevor.com/sitemap.xml`.

### 3. No canonical tags on any page — HIGH
Zero `<link rel="canonical">` across all 4 pages. Risk: query-string/trailing-slash duplicates and the apex→www redirect (confirmed: `asclevor.com` 308 → `www.asclevor.com`) can split signals. Add a canonical to every page pointing at the `www` production URL.

### 4. Invalid/unknown meta tag — LOW
`<meta name="text-scale" content="scale" />` in `src/app.html` is not a recognized meta and serves no purpose. Remove it.

### 5. Production security headers unverified — MEDIUM (deploy-dependent)
Dev server sends no security headers (expected in dev). Project uses `adapter-auto` with **no `svelte.config.js`** — the deploy target is undetected. Ensure the production host sends: `Strict-Transport-Security`, `X-Content-Type-Options: nosniff`, `Referrer-Policy: strict-origin-when-cross-origin`, and a basic CSP. Also confirm the apex→www 308 is permanent and intentional.

### 6. No prerendering configuration — LOW
All pages are static marketing pages. `export const prerender = true` (or `prerender` entries in `svelte.config.js`) would serve instant CDN-cached HTML → better TTFB/LCP and resilience.

### 7. Soft-404 behavior unverified — INFO
No custom error page found (`+error.svelte` absent). SvelteKit default error page will be served; add a branded `+error.svelte` with a link home.
