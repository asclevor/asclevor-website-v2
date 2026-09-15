# On-Page SEO — localhost:5173 (Asclevor)

**Score: 50/100**

## Title tags

| Page | Title | Length | Verdict |
|---|---|---|---|
| `/` | `Cursor · The AI Code Editor` | 28 | **CRITICAL — wrong brand** (also duplicates a competitor's title) |
| `/pricing` | `Pricing · Asclevor` | 18 | OK but weak; no keywords beyond "pricing" |
| `/api` | `Asclevor API · Clinical knowledge, programmatically` | 52 | Good |
| `/contact` | `Contact our team · Cursor` | 25 | **CRITICAL — wrong brand** |

## Meta descriptions

| Page | Verdict |
|---|---|
| `/` | **CRITICAL — Cursor's description** |
| `/pricing` | Good (76 chars, clear tiers) |
| `/api` | Good (88 chars) |
| `/contact` | **CRITICAL — Cursor's description** |

## Headings
- Exactly one H1 per page ✓ (home: "Asclevor is your knowledge base for medical infrastructure." — strong, keyword-bearing)
- H2 usage sparse (0–2 per page). Homepage has a single H2 ("Try Asclevor now.") — feature sections in `Features.svelte` don't use H2/H3 headings, costing topical structure. Verify feature card titles use real heading tags, not styled `<div>`s.
- Contact: H1 "Contact us" + H2 "Contact our team" are redundant — differentiate.

## Social / sharing metadata
- **No Open Graph tags** (og:title, og:description, og:image, og:url) — links shared on Slack/X/LinkedIn render bare.
- **No Twitter Card tags.**
- No shareable `og:image` asset exists (hero-app.png is 1.9MB, far over the ~300KB / 1200×630 norm). Create a dedicated OG image.

## Internal linking
- All 4 pages interlinked via navbar + footer ✓ (full mesh at this scale)
- No in-body contextual internal links (e.g., homepage → API page from feature copy)
- No breadcrumbs (acceptable at 4 pages; needed when blog/docs land on main domain)

## Image alt text
- 8/8 `<img>` have alt ✓ — but `alt="Cursor app screenshot"` (Hero.svelte) is **wrong brand**; "Mission Control", "Cloud agents" are feature names, not descriptions — expand to describe what's shown.

## Other
- Canonical: missing everywhere (see technical.md)
- Anchor text: navbar/footer anchors are fine ("Pricing", "API"); no generic "click here" patterns found
