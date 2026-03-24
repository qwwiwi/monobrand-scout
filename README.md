# Monobrand Scout

AI-powered pipeline for discovering viral monobrand products (1-5 SKU, single category) and finding brand-donors for localization.

Works with **Claude Code**, **OpenClaw**, **Cursor**, **Windsurf**, and any AI agent that reads markdown.

## What is a Monobrand?

A brand with 1-5 SKUs in a single category, focused on deep customer understanding and viral potential.

**Examples:** UNCO (underwear, 3 SKU), Stanley (tumblers), Ridge Wallet, Crocs (clogs), Solo Stove, Truff (hot sauce).

**Monobrand vs Arbitrage:** Arbitrage = 20-30 unrelated products, low margins, no LTV. Monobrand = 1-5 SKU, deep product focus, virality, repeat purchases.

## Strategy: Copy & Localize

The core strategy is NOT inventing from scratch, but finding a proven brand-donor in another market (US, Europe) and localizing it to your market.

## How It Works

```
Category + Geo → Collect from 4 streams → 12 Criteria Filter → Virality Scoring → Brand Cards → Launch Steps
```

### 6-Stage Pipeline

1. **Collect candidates** from 4 parallel streams:
   - Amazon (Best Sellers, New Releases, Movers & Shakers)
   - Shopify D2C stores (Internet Search Unit analytics)
   - Local marketplaces (Wildberries, Ozon — availability check)
   - Social + Trends (TikTok, Instagram, Google Trends)

2. **12 criteria filter** — financial viability (>$1M/yr), SKU count, virality potential, margins, manufacturability, logistics, LTV...

3. **Virality scoring** (0-100) — TikTok views (25%), Google Trends growth (20%), financials (20%), UGC (15%), engagement (10%), reviews (10%)

4. **Brand cards** — detailed profile of each candidate with all metrics

5. **Launch roadmap** — factory → logistics → test batch → marketplace test → scale

6. **Output** — ranked shortlist of 5-10 brand-donors with verdicts

## Tools

### Free (12 sources)

| Tool | What it provides |
|------|-----------------|
| Amazon Best Sellers / New Releases / Movers & Shakers | Top products by category, fast growers |
| TikTok Creative Center | Trending products, hashtags by country |
| Google Trends (pytrends) | Search volume growth, seasonality |
| YouTube Data API v3 | Product review views, channel stats |
| Meta Graph API | Instagram engagement, hashtag posts |
| Pinterest Trends | Visual category trends |
| SocialBlade | YouTube/TikTok/Instagram basic stats |
| Wildberries API | Product catalog, reviews, brands |
| DuckDuckGo Search | Web search for brands |
| Product Hunt | New products, upvotes |
| Reddit / X | Mentions, discussions, sentiment |

### Paid (recommended ~$200/mo)

| Tool | What it provides | Price | Priority |
|------|-----------------|-------|----------|
| Internet Search Unit | Shopify store analytics: revenue, sales, filters | ~$100/mo | CRITICAL |
| Exploding Topics | Early trends before mass market | $39/mo | HIGH |
| MPStats | Wildberries/Ozon sales analytics | $50/mo | HIGH |
| SerpAPI | Google Trends programmatically | $50/mo | HIGH |
| JungleScout | Amazon sales, niches, BSR | $49/mo | MEDIUM |
| Hom10 | Additional Shopify analytics | ~$30-50/mo | MEDIUM |
| Tokboard | TikTok analytics | $15-50/mo | MEDIUM |
| SimilarWeb | Website traffic | $100+/mo | LOW |

## Virality Score

| Score | Level | Action |
|-------|-------|--------|
| 80-100 | Viral hit | Ideal donor — start immediately |
| 60-79 | Strong growth | Excellent candidate — deep dive |
| 40-59 | Promising | Worth studying more |
| 20-39 | Niche | Only if you strongly believe |
| 0-19 | Skip | Move on |

## 12 Donor Criteria

| # | Criterion | Must-have |
|---|-----------|-----------|
| 0 | Revenue >$1M/yr | YES |
| 1 | 1-5 SKU | YES |
| 2 | Single vertical | YES |
| 3 | Viral potential (Reels/TikTok) | YES |
| 4 | Active social media | Preferred |
| 5 | Margins >40% | YES |
| 6 | Not yet on target market | Preferred |
| 7 | Manufacturable | YES |
| 8 | Easy logistics | Preferred |
| 9 | Repeat purchase (LTV) | Preferred |
| 10 | Value proposition | YES |
| 11 | Team can focus | YES |
| 12 | Testable (small batch) | Preferred |

## Installation

### Claude Code
```bash
git clone https://github.com/qwwiwi/monobrand-scout.git
# Then: "Read monobrand-scout/SKILL.md and find me brand-donors in [category]"
```

### OpenClaw
```bash
cd ~/.openclaw/workspace/skills/
git clone https://github.com/qwwiwi/monobrand-scout.git
```

### Any AI Agent
Include `SKILL.md` in the agent's context. It's plain markdown — no dependencies.

## Compatibility

| Platform | How to use |
|----------|-----------|
| **Claude Code** | Clone repo or add SKILL.md to project |
| **OpenClaw** | Clone into skills/ directory |
| **Cursor / Windsurf** | Add SKILL.md as project file |
| **Any LLM agent** | Include SKILL.md in context |

## Methodology

Based on the "Brand Launch" course by Expansio, covering monobrand definition, donor search (Amazon + Shopify), 12 selection criteria, practical examples, and launch operations.

## License

MIT
