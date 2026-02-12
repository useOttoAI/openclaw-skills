# Otto AI Pricing

Complete pricing guide for all Otto AI x402 endpoints.

## Payment Networks

All prices are in **USDC**. Supported networks:

| Network | Chain ID | Status |
|---------|----------|--------|
| Base | 8453 | Recommended |
| Solana | solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp | Supported |

---

## Market Intelligence (otto-intel)

| Endpoint | Price | Description |
|----------|-------|-------------|
| `/crypto-news` | $0.01 | Real-time crypto news with sentiment |
| `/twitter-summary` | $0.01 | Curated crypto Twitter digest |
| `/token-details` | $0.01 | Token price and metrics |
| `/yield-alpha` | $0.01 | DeFi yield opportunities |
| `/suggest-a-trade` | $0.01 | AI trade suggestions |
| `/token-security` | $0.01 | Token contract security audit (GoPlus) |
| `/funding-rates` | $0.01 | Derivatives dashboard (funding, OI, whales) |
| `/defi-analytics` | $0.01 | DeFi protocol analytics (TVL, trends) |
| `/tradfi-data` | $0.01 | TradFi macro intelligence (VIX, DXY, yields) |
| `/filtered-news` | $0.05 | Topic-filtered news |
| `/token-alpha` | $0.05 | Premium token intelligence |
| `/kol-sentiment` | $0.05 | KOL sentiment analysis |
| `/trending-altcoins` | $0.05 | Top trending tokens |
| `/mega-report` | $0.25 | Comprehensive daily briefing |

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
| News check | `/crypto-news` | $0.01 |
| KOL signals | `/kol-sentiment` | $0.05 |
| Token deep dive | `/token-alpha` | $0.05 |
| **Total** | | **$0.11** |

### Full Daily Briefing
| Task | Endpoints | Cost |
|------|-----------|------|
| Complete briefing | `/mega-report` | $0.25 |
| **Total** | | **$0.25** |

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
