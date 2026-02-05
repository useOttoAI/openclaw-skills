---
name: otto-research
description: AI research assistant from Otto AI - powered by Gemini 2.5 Pro
emoji: 🔬
homepage: https://docs.useotto.xyz
---

# Otto AI Research Assistant

Ask anything and get instant, AI-powered answers with live web search. Powered by Google's Gemini 2.5 Pro.

## Payment

All endpoints require x402 payment in **USDC** on:
- **Base** (chain ID: 8453) - recommended
- **Solana** (chain ID: solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp)

Payment is handled automatically via the x402 protocol headers.

---

## Endpoint

### AI Research ($0.30)

**URL:** `POST https://x402.ottoai.services/llm-research`

**Use when:** User has a question that requires research, analysis, or explanation.

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `prompt` | string | Yes | Your question (max 180 characters) |
| `url` | string | No | Public URL for analysis (image or webpage) |

**Returns:** AI-generated text response answering the prompt.

**Capabilities:**
- Live web search for up-to-date information
- Image analysis (JPEG, PNG, WEBP, HEIC, HEIF)
- Webpage summarization
- Any topic: crypto, science, technology, history, etc.

---

## Important: 180 Character Limit

The prompt must not exceed **180 characters**. Keep questions concise and focused.

**Good examples:**
- "Explain how Hyperliquid's HIP-1 works" (39 chars)
- "What are the risks of liquid restaking?" (40 chars)
- "Compare Aave vs Morpho for lending" (35 chars)

**Too long:**
- "Can you explain in detail how the Hyperliquid perpetuals exchange works, including their margin system, funding rates, and liquidation mechanism?" (145 chars - getting close to limit)

---

## Use Cases

### General Knowledge
- "What is account abstraction (ERC-4337)?"
- "Explain perpetual futures funding rates"
- "How do cross-chain bridges work?"

### Image Analysis
Provide an image URL to analyze:
- Screenshots of charts
- Social media posts
- Diagrams or infographics

### Webpage Summarization
Provide a webpage URL to summarize:
- Blog posts
- Documentation
- Research papers

---

## Example Requests

**Simple question:**
```
prompt: "What is the difference between L2 and L3 blockchains?"
```

**With image analysis:**
```
prompt: "Analyze this chart and explain the pattern"
url: "https://example.com/chart.png"
```

**With webpage summary:**
```
prompt: "Summarize the key points of this article"
url: "https://example.com/article"
```

---

## Documentation

Full API documentation: https://docs.useotto.xyz/acp-swarm/x402
