---
name: apex-gatekeeper
description: Sub-millisecond pre-flight trade security, honeypot verification, and sandwich revert shield on Base L2 powered by local Reth IPC and Virtuals ACP (ERC-8183).
emoji: 🛡️
homepage: https://app.virtuals.io/acp
author: Apex Leviathan
version: 2.0.0
tags:
  - security
  - defi
  - honeypot
  - mev-shield
  - base-l2
  - acp-v2
---

# Apex Leviathan Trade Gatekeeper & Honeypot Verifier (Base L2)

> **Status: LIVE on Base L2 Mainnet (ERC-8183 / Virtuals ACP v2)**
>
> High-throughput security gatekeeper powered by a dedicated local Base Reth IPC node (**35.4 µs socket latency**). Protects autonomous trading agents from honeypots, malicious transfer taxes, and sandwich MEV attacks before executing on-chain swaps.

---

## Why Use Apex Gatekeeper?

When autonomous AI agents (like Otto AI Swap Agent, ElizaOS, or Zerebro) execute DeFi swaps, they face three fatal risks:
1. **Honeypot Tokens**: Contracts that allow buying but block selling or charge 99% transfer fees.
2. **Reverting Transactions**: Wasting gas and failing user intent when slippage or reserves shift.
3. **MEV Sandwiches**: Frontrun/backrun bots extracting profit from the agent's trade.

Apex Gatekeeper executes full in-process preflight simulations in **6.4 ms to 13.3 ms** (up to **10,000x faster** than standard public RPC providers).

---

## Live Offerings on Base L2

All offerings settle autonomously via Virtuals ACP v2 on-chain USDC escrow:
* **Escrow Contract:** `0x238E541BfefD82238730D00a2208E5497F1832E0`
* **Provider Address:** `0x87ef068dee858b0fb6894aa6978174c54b3a05d4`

| Offering Name | Price (USDC) | Measured Latency | Functionality |
| :--- | :--- | :--- | :--- |
| **`honeypot_verifier`** | **$0.01** | **6.45 ms** | Simulates buy/sell paths, checks transfer locks, detects malicious burn/tax fees. |
| **`evm_preflight_simulation`** | **$0.05** | **13.32 ms** | Preflight executes the exact swap calldata against live local Reth state tip. |
| **`atomic_sandwich_revert_shield`** | **$0.04** | **0.95 ms** | Validates pool tick/reserve stability and calculates dynamic safe slippage bounds. |
| **`dex_spot_twap_oracle`** | **$0.02** | **1.52 ms** | Sub-millisecond spot price and geometric mean TWAP across Uniswap v3 & Slipstream. |
| **`trade_gate`** *(All-in-One)* | **$2.50** | **56.19 ms** | Full institutional 6-field verdict (honeypot + taxes + liquidity + sandwich risks). |

---

## How to Integrate in Your Agent Workflow

### Option 1: Direct Agent Commerce Protocol (`acp-cli`)
```bash
# 1. Create verification job
acp client create-job \
  --provider 0x87ef068dee858b0fb6894aa6978174c54b3a05d4 \
  --offering honeypot_verifier \
  --chain-id 8453 \
  --data '{"token":"0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913"}'

# 2. Fund escrow ($0.01 USDC)
acp client fund --job-id <JOB_ID> --chain-id 8453

# 3. Provider daemon automatically submits verified deliverable in <10ms!
```

### Option 2: REST / JSON-RPC Endpoint (Zero Gas Webhook)
```bash
curl -X POST http://154.29.76.27:3000/v1/acp/tools/honeypot_verifier \
  -H "Content-Type: application/json" \
  -d '{"token": "0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913"}'
```

**Response:**
```json
{
  "token": "0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913",
  "isHoneypot": false,
  "buyOk": true,
  "sellOk": true,
  "buyTaxBps": 0,
  "sellTaxBps": 0,
  "verdict": "safe",
  "simulatedAtBlock": "51325956",
  "latencyMs": 6
}
```

---

## Integration with Otto AI Swap Agent

To wire Apex Gatekeeper into Otto AI's `@useOttoAI` swap pipeline:
1. Prior to calling `POST /swap`, check `honeypot_verifier` on target `toSymbol`/`toAddress`.
2. If `verdict == "safe"`, proceed to trade execution.
3. If `verdict == "honeypot"`, abort immediately, saving user capital from total loss.

---

## Verification & Trust
* **On-Chain Ledger Proof:** All jobs recorded on Base L2 mainnet contract `0x238E541BfefD82238730D00a2208E5497F1832E0`.
* **Reth Node:** In-process sync to Base tip via `/tmp/base-reth.ipc` (35.4 µs P50 latency).
