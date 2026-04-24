# PD.md Protocol

> **A standard for describing products so AI can turn them into playable content.**
> PD.md 协议 — 为 vibecoder 设计的产品说明标准，让 AI 能把你的产品变成可玩、可传播的内容。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
![Version](https://img.shields.io/badge/version-0.1.0-blue)
![Status](https://img.shields.io/badge/status-draft-orange)

---

## Why PD.md exists

In 2026, anyone can build a product with Claude Code, Cursor, Lovable, v0, or Bolt.
But most products die in silence — not because they're bad, but because **no one sees them**.

The bottleneck has shifted from **building** to **being seen**.

PD.md is a structured way to describe your product so that downstream tools (like [Kickoo](https://kickoo.cn)) can automatically generate:

- **Playables** — interactive mini-experiences that preview your product's "wow moment"
- **Launch kits** — platform-specific copy for X, 小红书, LinkedIn, 即刻, TikTok
- **Marketing artifacts** — posters, covers, shareable assets

You write the PD.md once. AI does the rest of the distribution work.

---

## Quick start

### For vibecoders (the 90% case)

1. Open your coding tool (Claude Code / Cursor / Lovable / etc.)
2. Copy the prompt from [`prompt-template.md`](./prompt-template.md)
3. Paste it into your coding tool, pointing at your project
4. The tool generates a `product_details.md` in 3-5 minutes
5. Upload it to [Kickoo](https://kickoo.cn) or any PD.md-compatible tool

### For tool builders

Read [`PROTOCOL.md`](./PROTOCOL.md) for the full spec.
The protocol is intentionally simple — it's a markdown document with expected sections.
Your parser extracts `wow_moment`, `target_user`, `key_features`, `brand_tone`, etc.

---

## Structure

A valid PD.md has 8 parts:

| Part | Section | Purpose |
|------|---------|---------|
| I    | Vision & Origin | One-line positioning, why-now, north-star goal |
| II   | Insights & Assumptions | User insights, product bets |
| III  | Product Shape | User roles, core value prop, wow moment |
| IV   | Feature Inventory | What exists today |
| V    | Technical Architecture | Stack, deploy, data |
| VI   | Go-to-Market Thinking | Target users, channels, positioning |
| VII  | Roadmap | What's shipped, what's next |
| VIII | Appendix | Terms, decision log, known gaps |

The full field specification is in [`PROTOCOL.md`](./PROTOCOL.md).

---

## Versioning

- **v0.1 (current)** — Initial draft. API unstable. Breaking changes expected.
- **v1.0** — Will be frozen once 50+ products have been successfully distributed using the protocol.

---

## Contributing

This protocol is open. If you're a vibecoder, a tool builder, or just someone who wants better ways to distribute products — we want your input.

- Open an issue to propose changes
- Submit PRs with real-world PD.md examples (see `examples/`)
- Join the discussion on X [@kickoo_cn](https://x.com/kickoo_cn)

---

## License

MIT © [Kickoo](https://kickoo.cn)

---

<sub>Made by people tired of shipping products no one sees.</sub>
