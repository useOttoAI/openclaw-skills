# Otto AI Pricing

Complete pricing guide for all Otto AI x402 endpoints.

## Payment Networks

All prices are in **USDC**. Base is accepted on every route; Solana only where that route's own `accepts[]` lists it:

| Network | Chain ID | Status |
|---------|----------|--------|
| Base | 8453 | Accepted on every route (recommended) |
| Solana | solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp | Only the routes whose 402 lists it — `/video-gen` is Base-only |

---

## Market Intelligence (otto-intel)

| Endpoint | Price | Description |
|----------|-------|-------------|
| `/crypto-news` | $0.001 | Hourly ranked headlines w/ source links + sentiment |
| `/twitter-summary` | $0.001 | Curated crypto Twitter digest |
| `/token-details` | $0.001 | Token price and metrics |
| `/yield-alpha` | $0.002 | DeFi yield opportunities |
| `/suggest-a-trade` | $0.01 | AI trade suggestions |
| `/token-security` | $0.001 | Token contract security audit (GoPlus) |
| `/funding-rates` | $0.001 | Derivatives dashboard (funding, OI, whales) |
| `/defi-analytics` | $0.001 | DeFi protocol analytics (TVL, trends) |
| `/tradfi-data` | $0.003 | TradFi macro intelligence (VIX, DXY, yields) |
| `/filtered-news` | $0.001 | Topic-filtered news |
| `/token-alpha` | $0.005 | Premium token intelligence |
| `/kol-sentiment` | $0.003 | KOL sentiment analysis |
| `/trending-altcoins` | $0.002 | Top trending tokens |
| `/mega-report` | $0.05 | Comprehensive daily briefing |

---

## Creative Tools (otto-creative)

| Endpoint | Price | Description |
|----------|-------|-------------|
| `/generate-meme` | $0.25 | AI image generation (Gemini 3 Pro) |
| `/video-gen` (standard) | $3.00 | 4-second video (Sora 2) |
| `/video-gen` (pro) | $8.50 | 8-second video (Sora 2 Pro) |

---

## Research (otto-research)

| Endpoint | Price | Description |
|----------|-------|-------------|
| `/llm-research` | $0.30 | AI research assistant (Gemini 2.5 Pro) |

---

## Coming Soon (via ACP only)

These services are available via the Agent Commerce Protocol but not yet on x402:

### Swaps & Bridging
| Service | ACP Price | Description |
|---------|-----------|-------------|
| `swap` | $0.10 | Same-chain token swaps |
| `bridge` | $0.10 | Cross-chain bridging |
| `deposit` | $0.25 | Deposit to Otto AI Safe |
| `withdraw` | $0.01 | Withdraw from Safe |

### Perpetual Futures
| Service | ACP Price | Description |
|---------|-----------|-------------|
| `trade_perpetuals` | $0.03 | Open leveraged position |
| `close_position` | $0.01 | Close position |
| `modify_hl_order` | $0.01 | Add/modify TP/SL |
| `update_position_margin` | $0.01 | Adjust margin |
| `hyperliquid_deposit_withdrawal` | $0.10 | HL deposits/withdrawals |

---

## Cost Examples

### Daily Market Research
| Task | Endpoints | Cost |
|------|-----------|------|
| News check | `/crypto-news` | $0.001 |
| KOL signals | `/kol-sentiment` | $0.003 |
| Token deep dive | `/token-alpha` | $0.005 |
| **Total** | | **$0.003** |

### Full Daily Briefing
| Task | Endpoints | Cost |
|------|-----------|------|
| Complete briefing | `/mega-report` | $0.05 |
| **Total** | | **$0.05** |

### Content Creation
| Task | Endpoints | Cost |
|------|-----------|------|
| Meme | `/generate-meme` | $0.25 |
| Short video | `/video-gen` standard | $3.00 |
| **Total** | | **$3.25** |

---

## Free Resources

These read-only endpoints are free (no x402 payment required):

| Endpoint | Description |
|----------|-------------|
| `GET /api/trade-agent/portfolio/{address}` | View Otto AI portfolio |
| `GET /api/trade-agent/history/{address}` | Transaction history |
| `GET /api/trade-agent/tokens?search=&chainId=` | Search tokens |
| `GET /api/trade-agent/hyperliquid/account/{address}` | Hyperliquid account |
| `GET /api/trade-agent/hyperliquid/market` | Market data |
| `GET /.well-known/x402` | Discovery document |
