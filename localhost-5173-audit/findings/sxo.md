# Search Experience Optimization (SXO) — localhost:5173 (Asclevor)

**Page-type analysis & persona fit.**

## Page-type vs. SERP-intent match

| Page | Intended type | Verdict |
|---|---|---|
| `/` | SaaS product landing | Structure matches (hero → features → CTA). Missing the proof band (logos/metrics) that Google-rewarded landing pages for this niche show. |
| `/pricing` | Pricing page | Good: tiers + FAQ + CTA. Matches intent well. |
| `/api` | Developer docs-adjacent landing | Partial mismatch: reads as marketing but the searcher intent ("asclevor api", "clinical data api") expects code, endpoints, auth. Even a single curl example in HTML would close most of the gap. |
| `/contact` | Contact page | Type match; thin execution. |

## User stories

1. *"As a hospital-data engineer searching for clinical knowledge APIs, I need to see what data you cover and a request example before I'll book a demo."* — `/api` currently fails the second half.
2. *"As a founder evaluating tools, I need to trust you're real."* — Cursor-branded titles and a 134-word homepage actively break this.
3. *"As a returning visitor, I navigated here to sign up."* — CTAs are clear ✓.

## Persona scoring (0–5)
- **Technical buyer**: 2/5 — no code, no endpoint list, no security/compliance signal (HIPAA/SOC2 nowhere in HTML — for a *clinical* product this is the #1 objection)
- **Executive/evaluator**: 3/5 — clear value prop, but no outcomes/metrics/customers
- **AI answer engine**: 1/5 — contradictory entity signals, no schema, thin passages

## Top SXO move
Add a compliance/security strip (SOC 2, HIPAA-eligibility, data sourcing) to `/` and `/api` — for this vertical it doubles as E-E-A-T, conversion copy, and citable passages.
