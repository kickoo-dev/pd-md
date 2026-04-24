# PD.md Protocol Specification

**Version:** 0.1.0 (draft)
**Status:** Unstable — expect breaking changes before v1.0
**Maintainer:** [Kickoo](https://kickoo.cn)

---

## 1. What this is

PD.md is a **markdown-based product description protocol**. It defines the structure and fields a product document must contain for downstream AI tools to automatically generate distribution content (playables, launch kits, social posts).

The protocol is intentionally human-first — any vibecoder can read and edit a PD.md without tooling. But it's also machine-parseable: well-defined sections, consistent headings, and optional YAML frontmatter for structured data.

## 2. File format

- **Filename**: `product_details.md` (canonical) or `PD.md` (short)
- **Encoding**: UTF-8
- **Line endings**: LF
- **Max size**: No hard limit, but recommend under 50KB for AI processing
- **Frontmatter**: Optional YAML block at top

### 2.1 Frontmatter (recommended)

```yaml
---
name: TAAI
slug: taai
tagline: AI-powered digital business cards for professionals
url: https://jiling.chat
version: "0.1"
pd_md_version: "0.1.0"
primary_language: zh-CN
secondary_language: en
tags: [ai, saas, professional-services, china]
---
```

## 3. Required sections

A valid PD.md **must** contain these 8 parts with `## Part` level-2 headings:

```markdown
## Part I · Vision & Origin
## Part II · Insights & Assumptions
## Part III · Product Shape
## Part IV · Feature Inventory
## Part V · Technical Architecture
## Part VI · Go-to-Market Thinking
## Part VII · Roadmap
## Part VIII · Appendix
```

Section ordering matters. Parsers use section headings to extract structured fields.

## 4. Field-by-field specification

### Part I · Vision & Origin

**Required subsections:**
- `One-line positioning` — a single sentence describing what the product is
- `Why now` — why this product is viable at this moment (tech maturity, market shift, etc.)
- `North-star goal` — what success looks like in 6 / 12 / 24 months

### Part II · Insights & Assumptions

**Required subsections:**
- `Key insights` — 3–5 user or market insights the product is built on
- `Key assumptions` — 3–5 bets that, if wrong, would invalidate the product

Each insight/assumption should include a confidence tag: `(H)` high, `(M)` medium, `(L)` speculative.

### Part III · Product Shape

**Required subsections:**
- `User roles` — who uses this, in what mode
- `Core value proposition` — the "I paid for this because ___" sentence
- **`Wow moment`** ⭐ — the single most impressive 30-second experience. This is the most important field for Kickoo-class tools.

### Part IV · Feature Inventory

A structured list of what exists today. Use tables or bullet lists. Downstream tools extract feature names, descriptions, and completion status.

### Part V · Technical Architecture

Stack, deployment, data model. Used by distribution tools to understand the product's technical positioning (e.g., "this is a Next.js SaaS" vs "this is a hardware device").

### Part VI · Go-to-Market Thinking

**Required subsections:**
- `Target users` — who you want to acquire
- `Channels` — where your target users hang out
- `Current GTM status` — what's been tried, what worked/failed
- `Monetization assumptions` — pricing hypotheses

### Part VII · Roadmap

Three time buckets:
- `Shipped` — what's live
- `Next up (Q+1)` — the next quarter
- `Long-term vision` — 12-month+ direction

### Part VIII · Appendix

- `Terms` — project-specific glossary
- `Decision log` — key decisions with dates (helps AI understand product history)
- `Known gaps` — what's incomplete, for honesty

## 5. Style conventions

- Use 雙語混寫 (bilingual) where natural — Chinese for emotional/narrative content, English for technical terms
- Include confidence markers: `(H)` `(M)` `(L)` for disputable claims
- Mark AI-generated sections with `[speculation · review needed]` blocks
- Date major decisions in the format `YYYY-MM-DD`

## 6. Compatibility

Tools claiming "PD.md v0.1 compatible" must:
1. Parse all 8 parts without error
2. Extract the `Wow moment` field from Part III
3. Surface missing required subsections to the user
4. Preserve original content when round-tripping

## 7. What PD.md is not

- **Not a PRD** — PRDs are for engineering; PD.md is for distribution
- **Not marketing copy** — it's the source material, not the output
- **Not user-facing** — vibecoders write it, AI reads it

## 8. Examples

See the `examples/` directory for real PD.md files from products that have used the protocol.

Contributed examples welcome via PR.

## 9. Change log

### v0.1.0 (2026-04)
- Initial draft
- 8-part structure proposed
- Frontmatter format defined

---

**Questions?** Open an issue or reach out at [kickoo.cn](https://kickoo.cn).
