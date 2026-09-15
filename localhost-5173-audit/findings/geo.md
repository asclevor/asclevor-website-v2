# AI Search Readiness (GEO) — localhost:5173 (Asclevor)

**Score: 35/100**

## What works
- Full SSR HTML — AI crawlers (GPTBot, ClaudeBot, PerplexityBot) that don't execute JS still see all content
- Clear, declarative H1s stating what the product is
- Plain-semantic markup, no intrusive interstitials
- robots.txt allows all crawlers (no AI-bot blocks detected)

## Findings

### 1. No `llms.txt` — MEDIUM
`/llms.txt` → 404. Cheap win: a short file listing the product definition, pricing tiers, API base URL, and links to docs. Helps LLMs represent Asclevor accurately.

### 2. Wrong-brand metadata poisons entity understanding — CRITICAL
AI engines reading `/` and `/contact` see "Cursor · The AI Code Editor" in the title/description — the strongest entity signals on the page contradict the brand. Any retrieval-based answer about Asclevor is currently more likely to conflate or skip it. Fixing metadata (see content.md #1) is simultaneously the top GEO fix.

### 3. Thin content = low citability — HIGH
Passage-level citability needs self-contained, factual, quotable chunks: definitions, numbers, concrete capabilities. At 95–215 words/page with feature names but few specifics (no endpoint examples, no data-source list, no coverage stats), there is little for an answer engine to cite. The pricing FAQ is the best citable block on the site — keep expanding that pattern.

### 4. No structured data for entity grounding — HIGH
Zero JSON-LD (see schema.md). `Organization` + `SoftwareApplication` markup is how machines confirm "Asclevor = this product, this category, these socials."

### 5. Brand-mention footprint lives off-domain — INFO
Docs and app are subdomains; content depth that would earn citations (changelog, guides, use cases) doesn't exist yet anywhere. When it does, keep marketing-domain content canonical on `www`.

## Citability snapshot
- Definitions: partial (H1s carry the definition)
- Statistics/numbers: absent
- Quotable specifics: FAQ only
- Author/source signals: absent
