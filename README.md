# OpenClaw Skills for Otto AI

Install these skills in [OpenClaw](https://openclaw.ai) to give your AI agent access to Otto AI's services via x402 micropayments.

## What is Otto AI?

Otto AI is an autonomous AI agent ecosystem providing 64 pay-per-call x402 services for DeFi, market intelligence, web/domain intelligence, and creative tools — including the **x402 Open Router** (recommend the best service, run a task hands-off with Full Auto, and a money-back guarantee). These skills let any OpenClaw-compatible agent access Otto AI's capabilities through pay-per-use x402 payments.

**Live at:** https://x402.ottoai.services

## Available Skills

| Skill | Description | Endpoints | Price Range |
|-------|-------------|-----------|-------------|
| [otto-intel](skills/otto-intel.skill.md) | Crypto market intelligence | 14 endpoints | $0.01-$0.05 |
| [otto-creative](skills/otto-creative.skill.md) | AI image & video generation | 3 endpoints | $0.25-$8.50 |
| [otto-research](skills/otto-research.skill.md) | AI research assistant | 1 endpoint | $0.30 |
| [otto-blockchain](skills/otto-blockchain.skill.md) | Transaction decoder & explainer (11 EVM chains) | 1 endpoint | $0.01 |
| [otto-swap](skills/otto-swap.skill.md) | Token swaps & portfolio | Coming Soon | - |
| [otto-perps](skills/otto-perps.skill.md) | Perpetual futures trading | Coming Soon | - |
| [x402 Open Router](https://docs.useotto.xyz/acp-swarm/open-router) | Recommend the best service (Meta Intelligence), pay-on-your-behalf hands-off (Full Auto), and a money-back guarantee (Feedback & Refunds) | 3 endpoints | $0.001 |

**Money-back guarantee:** pay a recommended Otto service (or use Full Auto) you don't like, send feedback with a ≥50-word reason, and Otto refunds the fee — capped $0.01 per transaction, up to 10× per wallet per day, to the original payer. Covers Otto's own recommended services + Full Auto, not third-party CDP Bazaar picks.

## Installation

### Option 1: Install via OpenClaw UI

1. Go to your OpenClaw dashboard
2. Navigate to Skills > Add Skill
3. Paste the raw GitHub URL of any skill file:
   ```
   https://raw.githubusercontent.com/useOttoAI/openclaw-skills/main/skills/otto-intel.skill.md
   ```

### Option 2: Manual Installation

Copy the contents of any `.skill.md` file to your OpenClaw skills directory.

## Payment Setup

All Otto AI services require x402 payment in USDC. Networks are PER ROUTE:

| Network | Chain ID | Currency | Coverage |
|---------|----------|----------|----------|
| **Base** | 8453 | USDC | Every route |
| **Solana** | solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp | USDC | Only the routes whose 402 lists it |

Fund your agent's wallet on **Base** and every route is payable. A Solana-only wallet can pay for
calls to 66 of the 89 routes — the ones that offer a Solana accept. Read the route's `accepts[]`
array (returned in both the `PAYMENT-REQUIRED` header and the 402 JSON body), or
`x-payment-info.networks` in `https://x402.ottoai.services/openapi.json`.

## How x402 Works

1. Your agent calls an Otto AI endpoint
2. The server returns a `402 Payment Required` response with payment details
3. Your agent sends USDC payment to the specified address
4. The server returns the response

OpenClaw handles steps 2-3 automatically if your agent has a funded wallet.

## Endpoint Discovery

Otto AI provides a discovery document at:
```
https://x402.ottoai.services/.well-known/x402
```

This lists all available endpoints with pricing.

## Support

- **Documentation:** https://docs.useotto.xyz
- **Twitter:** [@useOttoAI](https://twitter.com/useOttoAI)
- **x402 Explorer:** https://x402scan.com/server/2a58f75f-bd11-4020-a347-0e1c7f4912ef

## License

MIT License - see [LICENSE](LICENSE)
