# Content Quality / E-E-A-T — localhost:5173 (Asclevor)

**Score: 45/100**

**Business type detected: SaaS** (health-tech / clinical data API). Signals: `/pricing`, `/api`, `app.` + `docs.` subdomains, "talk to sales" Enterprise tier.

## Word counts (rendered body text)

| Page | Words | Verdict |
|---|---|---|
| `/` | 134 | Thin for a homepage — below the ~300-word floor for a product's primary ranking page |
| `/api` | 156 | Thin for a developer-facing API page (no endpoints, code samples in HTML, use cases) |
| `/pricing` | 215 | Borderline; FAQ section adds depth |
| `/contact` | 95 | Thin, though contact pages are naturally light |

## Findings

### 1. Wrong-brand copy: homepage & contact are Cursor's — CRITICAL (also trust/E-E-A-T)
- `src/routes/+page.svelte`: `<title>Cursor · The AI Code Editor</title>`, description *"Cursor is your coding agent…"*
- `src/routes/contact/+page.svelte`: `<title>Contact our team · Cursor</title>`, description *"Contact the Cursor team…"*
- `src/lib/components/Hero.svelte` line 40: `alt="Cursor app screenshot"`

This is leftover scaffold copy from cloning cursor.com's structure. It destroys brand clarity for users, search engines, and AI answer engines; it also makes the site look derivative of a competitor. Replace with Asclevor-branded metadata everywhere.

### 2. No proof/authority layer — HIGH
Zero signals of first-hand experience or expertise in the HTML: no customer counts, no named team credentials beyond one testimonial avatar (`leander-guo.png`), no case-study pages, no blog. For a **clinical/medical knowledge** product this matters doubly — health-adjacent YMYL expectations demand visible expertise (who curates the knowledge base, sources, review process). The one testimonial ("Medicine produces an enormous amount of knowledge…") is a good start; expand it.

### 3. No content hub on the main domain — HIGH
Docs (`docs.asclevor.com`) and app (`app.asclevor.com`) are separate subdomains — they don't accumulate ranking authority for `www.asclevor.com`. There is no blog, changelog (component exists but is retired), or use-case pages. Every additional indexed page targeting clinical-data/medical-API queries is a growth lever the site currently doesn't pull.

### 4. Thin product storytelling on `/api` — MEDIUM
H1 "Build on clinical knowledge right from your stack" is good, but the page ships no code sample, endpoint list, response example, or supported-language list in crawlable HTML. Developers (and AI engines citing developer docs) need concrete specifics.

### 5. Readability & tone — OK
Short sentences, consistent voice, scannable. No readability problem; the problem is quantity and proof, not clarity.

## E-E-A-T snapshot
- **Experience**: absent (no usage data, case studies, or outcomes)
- **Expertise**: minimal (one testimonial figure; no named curators/sources)
- **Authoritativeness**: weak (no external links, no about/team page at all — "Contact" is the only human-facing page)
- **Trust**: wrong-brand metadata actively undermines it; contact page + real pricing help
