# Market Analysis Workflow

Example workflow using Otto AI's market intelligence skills.

## Scenario: Daily Market Check

Your AI agent can perform a comprehensive market analysis using these Otto AI endpoints:

### Step 1: Get the Daily Pulse

**Prompt:** "What's happening in crypto today?"

**Endpoint called:** `/crypto-news` ($0.01)

**Response:** AI-generated news report with bull/bear sentiment and top headlines.

---

### Step 2: Check Social Sentiment

**Prompt:** "What are crypto influencers talking about?"

**Endpoint called:** `/kol-sentiment` ($0.05)

**Response:** Sentiment analysis from top 50 KOLs with trending tokens and alpha signals.

---

### Step 3: Deep Dive on Interesting Token

**Prompt:** "Give me the alpha on SOL"

**Endpoint called:** `/token-alpha` ($0.05)

**Response:** Premium token intelligence including:
- Price metrics and technicals
- News and Twitter sentiment
- Derivatives data (funding, OI, liquidations)
- One-click trade suggestions

---

### Step 4: Find Yield Opportunities

**Prompt:** "Where can I earn yield on my USDC?"

**Endpoint called:** `/yield-alpha` ($0.01)

**Response:** Best DeFi yields with risk ratings and APY comparisons.

---

## Total Cost: $0.12

For a comprehensive market overview, you've spent just $0.12 in x402 payments.

---

## Alternative: Full Daily Briefing

**Prompt:** "Give me today's market briefing"

**Endpoint called:** `/mega-report` ($0.25)

**Response:** Everything above combined into one comprehensive report:
- Top headlines
- Twitter sentiment
- KOL alpha
- Trending altcoins
- Yield opportunities
- Market indicators

**Total Cost:** $0.25 for the complete package.

---

## Sample Agent Code

```python
# Pseudo-code for an OpenClaw agent

async def daily_market_check():
    # Quick pulse check
    news = await call_x402("https://x402.ottoai.services/crypto-news")

    # Check if any tokens mentioned are interesting
    if "SOL" in news.content:
        sol_alpha = await call_x402(
            "https://x402.ottoai.services/token-alpha",
            {"token_symbol": "SOL"}
        )

        # If bullish signals, check for trade ideas
        if sol_alpha.sentiment == "bullish":
            trades = await call_x402(
                "https://x402.ottoai.services/suggest-a-trade",
                {"focus_symbols": ["SOL"]}
            )

    return compile_report(news, sol_alpha, trades)
```
