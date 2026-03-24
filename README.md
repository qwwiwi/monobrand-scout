# Monobrand Scout

AI-powered pipeline for discovering viral monobrand products (1-5 SKU, single category).

Works with **Claude Code**, **OpenClaw**, and any AI agent that reads markdown instructions.

## What is a Monobrand?

A brand with 1-5 SKUs in a single category, focused on deep customer understanding and viral potential.

**Examples:** Stanley (tumblers), Ridge Wallet, Crocs (clogs), UNCO (kids underwear), Solo Stove, Truff (hot sauce).

## How It Works

```
Category + Geo → Collect Candidates → Filter (1-5 SKU) → Virality Scoring → Shortlist
```

### Pipeline

1. **Collect** from 3 parallel streams:
   - Marketplaces (Wildberries, Ozon, Amazon)
   - Social media (TikTok, Instagram, YouTube)
   - Trends (Google Trends, Kickstarter, Product Hunt)

2. **Filter** — keep only brands with 1-5 SKU in one category

3. **Score virality** (0-100):
   - TikTok views (30%)
   - Google Trends growth (25%)
   - UGC content count (20%)
   - Engagement rate (15%)
   - Review count (10%)

4. **Output** — shortlist with brand cards

## Installation

### Claude Code

Drop `SKILL.md` into your project or reference it directly:

```bash
# Option 1: Clone into your project
git clone https://github.com/qwwiwi/monobrand-scout.git

# Option 2: Reference as a file
# Just point Claude Code to SKILL.md in conversation:
# "Read monobrand-scout/SKILL.md and find me viral monobrands in cosmetics"
```

Claude Code will read the skill file and follow the pipeline automatically — using web search, APIs, and analysis tools available in its environment.

### OpenClaw

```bash
# Install as AgentSkill
cd ~/.openclaw/workspace/skills/
git clone https://github.com/qwwiwi/monobrand-scout.git
```

The agent picks it up automatically when you ask about monobrands.

### Any AI Agent

The skill is a plain markdown file (`SKILL.md`) with structured instructions. Any AI agent that can:
- Read markdown files
- Execute shell commands (curl, python)
- Search the web

...can follow this pipeline. Just include `SKILL.md` in the agent's context.

## Tools

### Free (11 sources)

| Tool | What it provides |
|------|-----------------|
| TikTok Creative Center | Trending products, hashtags by country |
| Google Trends (pytrends) | Search volume growth, seasonality |
| YouTube Data API v3 | Product review views, channel stats |
| Meta Graph API | Instagram engagement, hashtag posts |
| Pinterest Trends | Visual category trends |
| SocialBlade | YouTube/TikTok/Instagram basic stats |
| Wildberries API | Product catalog, reviews, brands |
| DuckDuckGo Search | Web search for brands |
| Kickstarter | Successful mono-product campaigns |
| Product Hunt | New products, upvotes |
| Reddit / X | Mentions, discussions, sentiment |

### Paid ($139/mo recommended)

| Tool | What it provides | Price |
|------|-----------------|-------|
| Exploding Topics | Early trends BEFORE mass market | $39/mo |
| SerpAPI | Google Trends + Shopping programmatically | $50/mo |
| MPStats | Wildberries/Ozon sales analytics | $50/mo |

### Optional (deep analysis)

| Tool | Price |
|------|-------|
| JungleScout (Amazon) | $49/mo |
| Tokboard (TikTok analytics) | $15-50/mo |
| SimilarWeb (traffic) | $100+/mo |
| BrandWatch (mentions) | $100+/mo |
| SparkToro (audience) | $50/mo |

## Virality Score

| Score | Level | Example |
|-------|-------|---------|
| 80-100 | Viral hit | Stanley, Crocs |
| 60-79 | Strong growth | Ridge Wallet |
| 40-59 | Promising | Early-stage virality |
| 20-39 | Niche | Small but loyal audience |
| 0-19 | No virality | — |

## Quick Start

### Google Trends check
```python
from pytrends.request import TrendReq
pytrends = TrendReq(hl='en', tz=0)
pytrends.build_payload(['brand1', 'brand2'], timeframe='today 3-m')
data = pytrends.interest_over_time()
```

### Wildberries API search
```bash
curl -s "https://search.wb.ru/exactmatch/ru/common/v7/search?query=CATEGORY&resultset=catalog" \
  | jq '.data.products[:20] | .[] | {brand, name, rating, feedbacks}'
```

### YouTube review search
```bash
curl -s "https://www.googleapis.com/youtube/v3/search?part=snippet&q=BRAND+review&type=video&order=viewCount&maxResults=10&key=API_KEY"
```

## Use Cases

- **Ecommerce** — find brands to distribute in your market
- **Content** — generate viral content about trending products
- **Market research** — analyze niches for launching your own monobrand
- **Investment** — early signals on brands with viral potential

## Compatibility

| Platform | How to use |
|----------|-----------|
| **Claude Code** | Clone repo or add SKILL.md to project context |
| **OpenClaw** | Clone into `~/.openclaw/workspace/skills/` |
| **Cursor / Windsurf** | Add SKILL.md as project file |
| **Any LLM agent** | Include SKILL.md in system prompt or context |

The skill is just structured markdown — no runtime dependencies. The agent reads it and follows the pipeline using whatever tools are available in its environment.

## License

MIT
