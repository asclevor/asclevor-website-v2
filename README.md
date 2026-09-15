# Asclevor Website

The marketing website for [Asclevor](https://www.asclevor.com) — a knowledge base for medical
infrastructure: semantic search over 167,000+ real-world patient cases, accessible via a JSON API
and MCP.

Built with **SvelteKit 2 / Svelte 5**, **Tailwind CSS 4**, and **Vite 8**. All pages are
statically prerendered and ship with full SEO: per-page metadata, canonical URLs, Open Graph,
JSON-LD structured data, a sitemap, and `llms.txt`.

## Getting started

```sh
pnpm install
pnpm dev        # dev server at http://localhost:5173
pnpm build      # production build (prerenders all pages)
pnpm preview    # preview the production build
pnpm lint       # prettier check
pnpm format     # prettier write
```

## Pages

| Route         | Purpose                                                      |
| ------------- | ------------------------------------------------------------ |
| `/`           | Homepage — hero, features, product explainer, security strip |
| `/api`        | API overview with a copy-paste request example and Q&A       |
| `/pricing`    | Plans (Free / Developer / Pro / Enterprise) + FAQ            |
| `/leadership` | Team page (avatar grid, values)                              |
| `/changelog`  | Release notes, data-driven — see below                       |
| `/contact`    | Contact form (currently hands off to a `mailto:`)            |
| `/terms`      | Terms of Service                                             |
| `/privacy`    | Privacy Policy                                               |
| `/imprint`    | Legal imprint — **contains placeholders, see below**         |

## Project structure

```
src/
├── app.html                     # Head shell: fonts, apple-touch-icon
├── lib/
│   ├── config/site.js           # Site URL, name, socials, default OG image
│   ├── assets/favicon.svg
│   └── components/
│       ├── Seo.svelte           # Title/description/canonical/OG/Twitter/JSON-LD
│       ├── ImgSlot.svelte       # Lazy images + viewport-gated videos with posters
│       ├── About.svelte         # Homepage "What is Asclevor" section
│       ├── Hero / Features / Navbar / Footer / FinalCta / Avatar / …
│       ├── api/                 # API page sections
│       └── legal/LegalNav.svelte
├── routes/
│   ├── +layout.js               # prerender = true (all pages static)
│   ├── +layout.svelte           # Fonts, favicon, site-wide Organization JSON-LD
│   ├── +error.svelte            # Branded 404 (noindex)
│   └── <route>/+page.svelte     # One folder per page
static/
├── images/                      # Optimized media (WebP images, re-encoded MP4s, posters)
├── robots.txt                   # + Sitemap directive
├── sitemap.xml                  # Keep in sync when adding pages
├── llms.txt                     # Product summary for AI answer engines
├── og-image.jpg                 # 1200×630 social preview
└── apple-touch-icon.png
```

Untracked helper folders (not part of the deploy): `media-originals/` (pre-optimization media
backups) and `design-ref/` (design reference screenshots).

## Common tasks

### Add a changelog entry

Open `src/routes/changelog/+page.svelte` and append an object to the `entries` array
(newest first). There is a how-to comment at the top. Available block types:

```js
{
	date: 'Oct 1, 2026',
	title: 'Your update',
	blocks: [
		{ type: 'p', text: 'Text with **bold** and [links](/pricing).' },
		{ type: 'h2', text: 'Section heading' },
		{ type: 'img', src: '/images/shot.webp', alt: 'Describe the image' }
	];
}
```

Dividers, heading levels (h1 = newest entry), and layout are automatic.

### Add a leadership member

Edit the `leaders` array in `src/routes/leadership/+page.svelte`. Each entry has `name`, `role`,
`bio`, `img` (set `''` to show initials), `initials`, and `bg`. Put portrait photos in
`static/images/` (WebP, ~240×240, a few KB).

### Add a page

1. Create `src/routes/<route>/+page.svelte` with the `<Seo>` component (title, description, path).
2. Add the URL to `static/sitemap.xml`.
3. Add it to the footer columns in `src/lib/components/Footer.svelte` so it's linked sitewide.
4. If it's a legal page, reuse `src/lib/components/legal/LegalNav.svelte` as the sidebar.

### Media conventions

- Images: **WebP**, compressed and resized to display size (`cwebp -q 80 -resize 1600 0 in.png -o out.webp`).
- Videos: H.264, no audio, `+faststart`, ~1600px wide, a few MB max — with a WebP **poster**
  extracted from a frame. `ImgSlot` only loads videos near the viewport.
- Originals of everything shipped are backed up in `media-originals/`.

## SEO notes

- `src/lib/config/site.js` is the single source of truth for the canonical URL, site name, socials,
  and default OG image. The canonical host is `https://www.asclevor.com` (the apex redirects).
- Every page uses the `Seo` component (title, meta description, canonical, Open Graph, Twitter
  cards, optional JSON-LD). The layout emits site-wide `Organization` schema.
- When publishing: replace the bracketed placeholders in `/imprint` (legal entity details) and
  review `/terms` + `/privacy` with legal counsel.
- After deploy: verify security headers (HSTS, `X-Content-Type-Options`, `Referrer-Policy`) at the
  host, submit `sitemap.xml` in Google Search Console, and check the page renders in the
  [Rich Results Test](https://search.google.com/test/rich-results).

## Deployment

Uses `@sveltejs/adapter-auto` — the platform adapter is detected automatically on Vercel, Netlify,
Cloudflare, etc. All routes are prerendered (`src/routes/+layout.js`), so the deploy is fully
static; any host that serves static files works.

## Content & branding

© 2026 Asclevor. All rights reserved. The Asclevor name, logo, and site copy are proprietary;
the code in this repository is public for transparency — please don't reuse the branding or
content without permission.
