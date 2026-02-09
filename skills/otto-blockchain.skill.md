---
name: otto-blockchain
description: Blockchain transaction decoder & explainer from Otto AI - powered by Gemini 3 Flash
emoji: ⛓️
homepage: https://docs.useotto.xyz
---

# Otto AI Blockchain Tools

Decode and explain any EVM blockchain transaction in plain English. Supports 11 chains. Powered by on-chain data + Gemini 3 Flash AI.

## Payment

All endpoints require x402 payment in **USDC** on:
- **Base** (chain ID: 8453) - recommended
- **Solana** (chain ID: solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp)

Payment is handled automatically via the x402 protocol headers.

---

## Endpoint

### Transaction Explainer ($0.01)

**URL:** `GET https://x402.ottoai.services/tx-explainer`

Also supports `POST` with JSON body.

**Use when:** User wants to understand what a transaction did, decode a swap, transfer, approval, DeFi interaction, NFT operation, or any on-chain activity.

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `txHash` | string | Yes | Transaction hash (0x-prefixed, 64 hex characters) |
| `chain` | string | No | Blockchain network (default: `base`). See supported chains below. |
| `outputLevel` | string | No | `summary` (default, one-liner) or `detailed` (full breakdown with events) |

**Returns:** Human-readable explanation of what happened in the transaction.

---

## Supported Chains

| Chain | Value | Provider |
|-------|-------|----------|
| Base | `base` | Tenderly |
| Ethereum | `ethereum` | Tenderly |
| Arbitrum | `arbitrum` | Tenderly |
| OP Mainnet | `optimism` | Tenderly |
| Avalanche | `avalanche` | Tenderly |
| Polygon | `polygon` | Tenderly |
| Mantle | `mantle` | Tenderly |
| Monad | `monad` | Tenderly |
| Plasma | `plasma` | Tenderly |
| BSC | `bsc` | Alchemy |
| Hyperliquid L1 | `hyperliquid` | Alchemy |

---

## Output Levels

### Summary (default)
A concise one-liner explaining the transaction:
> "Swapped 1,000 USDC for 0.42 ETH on Uniswap V3"

### Detailed
Full breakdown including:
- Transaction overview (from, to, value, gas cost)
- Decoded function call (if verified contract)
- All decoded event logs (transfers, approvals, swaps)
- AI interpretation of the full transaction flow

---

## Use Cases

### Understand a Swap
```
txHash: "0xabc123..."
chain: "base"
outputLevel: "summary"
```

### Debug a Failed Transaction
```
txHash: "0xdef456..."
chain: "ethereum"
outputLevel: "detailed"
```

### Analyze Cross-Chain Activity
```
txHash: "0x789abc..."
chain: "arbitrum"
outputLevel: "detailed"
```

### Explain DeFi Interactions
- Lending/borrowing on Aave, Morpho, Compound
- Liquidity provision on Uniswap, Curve, Balancer
- Yield farming, staking, restaking
- NFT mints, transfers, marketplace sales

---

## Example Requests

**GET request:**
```
GET https://x402.ottoai.services/tx-explainer?txHash=0x1234...&chain=base&outputLevel=summary
```

**POST request:**
```json
{
  "txHash": "0x1234...",
  "chain": "ethereum",
  "outputLevel": "detailed"
}
```

---

## Documentation

Full API documentation: https://docs.useotto.xyz/acp-swarm/x402
