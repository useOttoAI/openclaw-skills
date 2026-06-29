---
name: otto-swap
description: Token swaps and portfolio management via Otto AI (Coming Soon)
emoji: 🔄
homepage: https://docs.useotto.xyz
---

# Otto AI Token Swaps

> **Status: Coming Soon to x402**
>
> Token swap execution is currently available via the [Agent Commerce Protocol (ACP)](https://docs.useotto.xyz/acp-swarm/trade-execution-agent) — through `acp-cli` (direct, on-chain USDC-escrow jobs) or the ACP Web GUI. x402 API access is planned for a future release.

## What Will Be Available

When launched, this skill will enable:

- **Multi-chain token swaps** on Base, Ethereum, Polygon, BSC, Arbitrum, Avalanche
- **Best execution routing** via Odos DEX aggregator (dozens of DEXs)
- **Non-custodial trading** through personal Safe smart accounts
- **Cross-chain bridging** via LiFi

---

## Currently Available: Read-Only Resources

While swap execution isn't on x402 yet, you can access these **free resources** to view trading data:

### Portfolio (Free)
**URL:** `GET https://api.useotto.xyz/api/trade-agent/portfolio/{walletAddress}`

View a user's Otto AI portfolio across all chains.

**Returns:** Token balances, USD values, chain breakdown.

### Transaction History (Free)
**URL:** `GET https://api.useotto.xyz/api/trade-agent/history/{walletAddress}`

View complete transaction history.

**Returns:** All swaps, TP/SL fills, manual closes.

### Supported Tokens (Free)
**URL:** `GET https://api.useotto.xyz/api/trade-agent/tokens?search={symbol}&chainId={chainId}`

Search for tokens by symbol on a specific chain.

**Returns:** Matching tokens from CoinGecko + Virtuals registry with contract addresses.

---

## Access Trading Now via ACP

To execute trades today, use Otto AI's Trade Execution Agent via the Agent Commerce Protocol:

1. **Via `acp-cli`:** [`@virtuals-protocol/acp-cli`](https://github.com/Virtual-Protocol/acp-cli) — `acp browse`, then `acp client create-job → fund → complete/reject` (direct, on-chain USDC escrow)
2. **Via ACP Web GUI:** Visit the [Virtuals ACP Interface](https://app.virtuals.io/acp)

**Available services via ACP:**
- `swap` - Same-chain token swaps ($0.01)
- `bridge` - Cross-chain bridging ($0.25)
- `deposit` - Move tokens to Otto AI Safe ($0.25)
- `withdraw` - Withdraw from Safe to wallet ($0.25)
- `earn_yield` - Deposit/withdraw from Aave V3 or Morpho ($0.10)

---

## Coming Soon

When x402 API access launches, you'll be able to:

```
POST https://x402.ottoai.services/swap
{
  "fromSymbol": "USDC",
  "toSymbol": "WETH",
  "amount": 100,
  "chainId": 8453
}
```

`fromSymbol`/`toSymbol` each accept a known **symbol** _or_ a **0x contract address**, resolved on `chainId`. Decimals are derived automatically — do not send them. Ambiguous symbols are rejected with the candidate addresses; pass the contract address to disambiguate (look it up via the tokens search endpoint above).

Stay tuned for updates: [@useOttoAI](https://twitter.com/useOttoAI)

---

## Documentation

- **Trade Execution Agent:** https://docs.useotto.xyz/acp-swarm/trade-execution-agent
- **ACP Overview:** https://docs.useotto.xyz/acp-swarm/overview
