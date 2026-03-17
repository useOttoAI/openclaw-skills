---
name: otto-intel
description: Crypto market intelligence from Otto AI - news, sentiment, tokens, yields
emoji: 📊
homepage: https://docs.useotto.xyz
---

# Otto Market Intelligence

Access real-time crypto market intelligence via Otto AI's x402 API. Get news, KOL sentiment, token analysis, yield opportunities, trade suggestions, and comprehensive market briefings.

## Payment

All endpoints require x402 payment in **USDC** on:
- **Base** (chain ID: 8453) - recommended
- **Solana** (chain ID: solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp)

Payment is handled automatically via the x402 protocol headers.

---

## Endpoints

### 1. Crypto News ($0.001)

**URL:** `GET https://x402.ottoai.services/crypto-news`

**Use when:** User wants latest crypto market news with sentiment analysis.

**Parameters:** None required.

**Returns:** AI-generated news report with bull/bear sentiment and top 10 headlines ranked by importance.

**Example prompt:** "What's happening in crypto today?"

---

### 2. Twitter Summary ($0.001)

**URL:** `GET https://x402.ottoai.services/twitter-summary`

**Use when:** User wants a quick pulse check from crypto Twitter.

**Parameters:** None required.

**Returns:** Curated Twitter/X digest with trending narratives and sentiment shifts.

**Example prompt:** "What's trending on crypto Twitter?"

---

### 3. Token Details ($0.10)

**URL:** `GET https://x402.ottoai.services/token-details`

**Use when:** User wants basic token information and metrics.

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `symbol` | string | Yes | Token symbol (e.g., "BTC", "ETH", "SOL") |

**Returns:** Token price, market cap, volume, supply, and other metrics.

**Example prompt:** "What's the price of SOL?"

---

### 4. Token Alpha ($0.10)

**URL:** `GET https://x402.ottoai.services/token-alpha`

**Use when:** User wants premium token intelligence with trading insights.

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `token_symbol` | string | Yes | Token symbol to analyze |

**Returns:** AI analysis with metrics, news, Twitter sentiment, derivatives data (funding rates, open interest, liquidations), and one-click trade parameters.

**Example prompt:** "Give me the alpha on ETH" or "Analyze BTC for me"

---

### 5. Filtered News ($0.10)

**URL:** `GET https://x402.ottoai.services/filtered-news`

**Use when:** User wants news filtered by a specific crypto topic (NOT token symbols).

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `topic` | string | Yes | Search term (max 2 words, e.g., "DeFi airdrops", "meme coins") |

**Note:** For token-specific research, use Token Alpha instead.

**Returns:** AI-filtered news and Twitter analysis on the topic.

**Example prompt:** "What's happening with DeFi airdrops?"

---

### 6. KOL Sentiment ($0.10)

**URL:** `GET https://x402.ottoai.services/kol-sentiment`

**Use when:** User wants premium signals from top crypto influencers.

**Parameters:** None required.

**Returns:** Sentiment analysis from top 50 crypto KOLs with trending token picks, alpha signals, and market sentiment.

**Example prompt:** "What are the top crypto influencers saying?"

---

### 7. Yield Alpha ($0.10)

**URL:** `GET https://x402.ottoai.services/yield-alpha`

**Use when:** User wants DeFi yield opportunities.

**Parameters:** None required.

**Returns:** Best DeFi yields across stablecoins, ETH, and BTC with risk ratings and APY comparisons.

**Example prompt:** "Where can I earn yield on my stablecoins?"

---

### 8. Trending Altcoins ($0.10)

**URL:** `GET https://x402.ottoai.services/trending-altcoins`

**Use when:** User wants to discover hot tokens to research.

**Parameters:** None required.

**Returns:** Top 3 trending altcoins based on news and social media analysis with reasons why they're hot.

**Example prompt:** "What altcoins are trending right now?"

---

### 9. Mega Report ($0.25)

**URL:** `GET https://x402.ottoai.services/mega-report`

**Use when:** User wants a comprehensive daily crypto briefing.

**Parameters:** None required.

**Returns:** AI-generated executive summary combining top headlines, Twitter sentiment, KOL alpha, trending altcoins, yield opportunities, and market indicators. Includes link to full HTML report (valid 24h).

**Example prompt:** "Give me today's market briefing" or "Daily crypto report"

---

### 10. Trade Suggestions ($0.10)

**URL:** `GET https://x402.ottoai.services/suggest-a-trade`

**Use when:** User wants AI-generated trade ideas with risk management.

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `risk_profile` | string | No | "conservative", "moderate", or "aggressive" |
| `focus_symbols` | array | No | Specific tokens to analyze (e.g., ["BTC", "ETH"]) |
| `account_size_usd` | number | No | Account size for position sizing |

**Returns:** Up to 3 trade suggestions (75%+ conviction only) with TA, derivatives data, position sizing, entry/SL/TP levels, and one-click execution params.

**Example prompt:** "Suggest some trades for me" or "What should I buy?"

---

### 11. Token Security Scanner ($0.01)

**URL:** `GET https://x402.ottoai.services/token-security`

**Use when:** User wants to check if a token contract is safe before buying.

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | string | Yes | Token contract address (0x-prefixed) |
| `chain` | string | No | Chain ID (default: 8453). Supported: 1 (ETH), 56 (BSC), 137 (Polygon), 42161 (Arbitrum), 8453 (Base), 43114 (Avalanche), 10 (Optimism) |

**Returns:** Risk score (0-100), security flags (honeypot, hidden mint, rug pull risks), tax analysis, holder concentration, and liquidity info. Powered by GoPlus Security.

**Example prompt:** "Is this token safe?" or "Check contract 0x..."

---

### 12. Funding Rate Dashboard ($0.01)

**URL:** `GET https://x402.ottoai.services/funding-rates`

**Use when:** User wants derivatives market intelligence — funding rates, open interest, whale positions.

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `symbol` | string | No | Token symbol for detailed view (omit for market overview with arb opportunities) |

**Returns:** With symbol: cross-exchange funding rates, OI breakdown, long/short ratios, whale positions. Without symbol: arbitrage opportunities, liquidation summary, fear/greed index, top whale positions.

**Example prompt:** "What are BTC funding rates?" or "Show me derivatives overview"

---

### 13. DeFi Protocol Analytics ($0.01)

**URL:** `GET https://x402.ottoai.services/defi-analytics`

**Use when:** User wants DeFi protocol TVL data, trends, or chain comparisons.

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `protocol` | string | No | Protocol slug for detailed view (e.g., "aave", "lido"). Omit for DeFi overview |

**Returns:** With protocol: TVL, chain breakdown, 7d/30d changes, category. Without protocol: top 20 by TVL, gainers/losers, chain comparison.

**Example prompt:** "How is Aave doing?" or "Show me DeFi TVL rankings"

---

### 14. TradFi Market Data ($0.01)

**URL:** `GET https://x402.ottoai.services/tradfi-data`

**Use when:** User wants traditional finance data for crypto context — indices, VIX, dollar, yields.

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `symbol` | string | No | Ticker symbol for individual quote (e.g., "AAPL", "^GSPC"). Omit for macro dashboard |

**Returns:** With symbol: real-time quote with 50/200 MA context, key stats. Without symbol: S&P 500, Nasdaq, VIX, DXY, treasury yields, gold, oil — with crypto impact analysis.

**Example prompt:** "What's the VIX at?" or "Show me macro dashboard"

---

## Quick Reference

| Endpoint | Price | Use Case |
|----------|-------|----------|
| `/crypto-news` | $0.001 | General market news |
| `/twitter-summary` | $0.001 | Twitter pulse check |
| `/token-details` | $0.10 | Basic token info |
| `/yield-alpha` | $0.10 | DeFi yields |
| `/suggest-a-trade` | $0.10 | AI trade ideas |
| `/token-security` | $0.01 | Contract security audit |
| `/funding-rates` | $0.01 | Derivatives dashboard |
| `/defi-analytics` | $0.01 | DeFi TVL & trends |
| `/tradfi-data` | $0.01 | TradFi macro data |
| `/filtered-news` | $0.10 | Topic-specific news |
| `/token-alpha` | $0.10 | Premium token intel |
| `/kol-sentiment` | $0.10 | KOL signals |
| `/trending-altcoins` | $0.10 | Hot tokens |
| `/mega-report` | $0.25 | Daily briefing |

---

## Documentation

Full API documentation: https://docs.useotto.xyz/acp-swarm/x402
