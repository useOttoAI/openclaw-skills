---
name: otto-perps
description: Hyperliquid perpetual futures trading via Otto AI (Coming Soon)
emoji: 📈
homepage: https://docs.useotto.xyz
---

# Otto AI Perpetual Futures

> **Status: Coming Soon to x402**
>
> Perpetual futures trading is currently available via the [Agent Commerce Protocol (ACP)](https://docs.useotto.xyz/acp-swarm/trade-execution-agent) through Virtuals Butler. x402 API access is planned for a future release.

## What Will Be Available

When launched, this skill will enable:

- **Leveraged long/short positions** on 220+ crypto assets
- **Stock perpetuals** (TSLA, AAPL, NVDA, etc.) via xyz DEX
- **Native TP/SL orders** executed by Hyperliquid
- **Position management** (add/remove margin, modify orders)
- **Cross and isolated margin** modes

---

## Currently Available: Read-Only Resources

While trade execution isn't on x402 yet, you can access these **free resources** to view Hyperliquid data:

### Hyperliquid Account (Free)
**URL:** `GET https://api.useotto.xyz/api/trade-agent/hyperliquid/account/{walletAddress}`

View complete Hyperliquid account snapshot.

**Returns:** Account balance, open positions, pending orders, margin usage, risk metrics.

### Hyperliquid Market (Free)
**URL:** `GET https://api.useotto.xyz/api/trade-agent/hyperliquid/market?asset={symbol}`

Get live market data for any asset.

**Parameters:**
- `asset` - Symbol (e.g., "BTC", "ETH", "TSLA"). Omit for top 20 markets.

**Returns:** Current price, 24h change, funding rate, open interest, max leverage.

### Trade History (Free)
**URL:** `GET https://api.useotto.xyz/api/trade-agent/hyperliquid/history/{walletAddress}?limit=20`

View recent trade history.

**Returns:** Trades with timestamps, prices, and realized PnL.

---

## Access Perps Trading Now via ACP

To trade perpetuals today, use Otto AI's Trade Execution Agent via the Agent Commerce Protocol:

1. **Via Butler:** Talk to [@Butler_Agent](https://twitter.com/Butler_Agent) on Twitter/X
2. **Via ACP Web GUI:** Visit the [Virtuals ACP Interface](https://app.virtuals.io/acp)

**Available services via ACP:**
- `trade_perpetuals` - Open leveraged positions ($0.01)
- `close_position` - Close open positions ($0.01)
- `modify_hl_order` - Add/modify TP/SL orders ($0.01)
- `update_position_margin` - Adjust leverage/margin ($0.01)
- `hyperliquid_deposit_withdrawal` - Deposit/withdraw USDC (ACP-only, not listed in ACP Web GUI — may be deprecated)

**Key specs:**
- Min position: $10 notional
- Max leverage: BTC 40x, ETH 25x, SOL 20x, stocks 20x
- Margin modes: Cross (default), Isolated

---

## Coming Soon

When x402 API access launches, you'll be able to:

```
POST https://x402.ottoai.services/trade-perpetuals
{
  "asset": "BTC",
  "side": "long",
  "size": 1000,
  "leverage": 10,
  "takeProfit": { "percentage": 5 },
  "stopLoss": { "percentage": 2 }
}
```

Stay tuned for updates: [@useOttoAI](https://twitter.com/useOttoAI)

---

## Documentation

- **Trade Execution Agent:** https://docs.useotto.xyz/acp-swarm/trade-execution-agent
- **Hyperliquid Integration:** https://docs.useotto.xyz/acp-swarm/hyperliquid
