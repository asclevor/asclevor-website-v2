# Schema / Structured Data — localhost:5173 (Asclevor)

**Score: 15/100**

## Current state
**Zero JSON-LD blocks across all 4 pages.** No microdata, no RDFa. This is the site's lowest-scoring category relative to effort required — it's all additive.

## Recommended implementation (priority order)

### 1. `Organization` — site-wide (High)
```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Asclevor",
  "url": "https://www.asclevor.com",
  "logo": "https://www.asclevor.com/logo.svg",
  "sameAs": ["https://x.com/asclevor", "https://www.linkedin.com/company/asclevor"]
}
```
Grounds the brand entity; `sameAs` ties the existing social profiles to it. Put in `+layout.svelte` head.

### 2. `WebSite` — homepage (Medium)
Standard `WebSite` with `name` + `url`. (Skip `SearchAction` unless/until a site search exists.)

### 3. `SoftwareApplication` with `offers` — homepage + pricing (High)
```json
{
  "@context": "https://schema.org",
  "@type": "SoftwareApplication",
  "name": "Asclevor",
  "applicationCategory": "BusinessApplication",
  "operatingSystem": "Web",
  "offers": {
    "@type": "Offer",
    "price": "0",
    "priceCurrency": "USD",
    "description": "Free tier; Team and Enterprise plans available"
  }
}
```
Extend per-plan if desired. This is the core product-entity markup for a SaaS.

### 4. `ContactPage` — /contact (Medium)
`ContactPage` referencing the `Organization` via `about`.

### 5. `FAQPage` — /pricing Q&A section (Info)
The pricing page has a genuine Q&A section, so FAQPage markup would be *valid*. Caveat per current guidance: Google retired FAQ rich results for all sites (May 2026), so **do not add it expecting a SERP feature** — value is limited to entity/answer-engine clarity. Optional, Info-level only.
- Do NOT add `HowTo` schema (deprecated).

### Notes
- SvelteKit: emit via `<svelte:head><script type="application/ld+json">{JSON.stringify(...)}</script></svelte:head>` or a small `JsonLd.svelte` helper.
- Validate after deploy with Google Rich Results Test + Schema.org validator.
