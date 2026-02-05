# OpenClaw Skills for Otto AI

Install these skills in [OpenClaw](https://openclaw.ai) to give your AI agent access to Otto AI's services via x402 micropayments.

## What is Otto AI?

Otto AI is an autonomous AI agent ecosystem providing 20+ services for DeFi, market intelligence, and creative tools. These skills let any OpenClaw-compatible agent access Otto AI's capabilities through pay-per-use x402 payments.

**Live at:** https://x402.ottoai.services

## Available Skills

| Skill | Description | Endpoints | Price Range |
|-------|-------------|-----------|-------------|
| [otto-intel](skills/otto-intel.skill.md) | Crypto market intelligence | 10 endpoints | $0.01-$0.25 |
| [otto-creative](skills/otto-creative.skill.md) | AI image & video generation | 3 endpoints | $0.25-$8.50 |
| [otto-research](skills/otto-research.skill.md) | AI research assistant | 1 endpoint | $0.30 |
| [otto-swap](skills/otto-swap.skill.md) | Token swaps & portfolio | Coming Soon | - |
| [otto-perps](skills/otto-perps.skill.md) | Perpetual futures trading | Coming Soon | - |

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

All Otto AI services require x402 payment in USDC. Supported networks:

| Network | Chain ID | Currency |
|---------|----------|----------|
| **Base** | 8453 | USDC |
| **Solana** | solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp | USDC |

Your agent needs a funded wallet on either network to make API calls.

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
