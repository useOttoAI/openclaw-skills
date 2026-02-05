# Research Workflow

Example workflow using Otto AI's research assistant.

## Scenario: Due Diligence on a DeFi Protocol

Your AI agent can research crypto projects and protocols.

### Example 1: Quick Concept Explanation

**Prompt:** "Explain how Hyperliquid's HIP-1 works"

**Endpoint called:** `/llm-research` ($0.30)

**Response:** Detailed explanation of the Hyperliquid Improvement Proposal covering:
- What HIP-1 enables
- Technical implementation
- Benefits for traders

---

### Example 2: Comparative Analysis

**Prompt:** "Compare Aave vs Morpho for lending"

**Endpoint called:** `/llm-research` ($0.30)

**Response:** Side-by-side comparison covering:
- Interest rate models
- Risk parameters
- Supported assets
- Fee structures

---

### Example 3: Image Analysis (Chart Reading)

**Prompt:** "Analyze this BTC chart and identify patterns"

**Parameters:**
```json
{
  "prompt": "Analyze this BTC chart and identify patterns",
  "url": "https://example.com/btc-chart.png"
}
```

**Endpoint called:** `/llm-research` ($0.30)

**Response:** Technical analysis identifying:
- Chart patterns (head & shoulders, triangles, etc.)
- Support/resistance levels
- Trend direction

---

### Example 4: Article Summarization

**Prompt:** "Summarize the key points of this article"

**Parameters:**
```json
{
  "prompt": "Summarize the key points of this article",
  "url": "https://example.com/defi-research-paper"
}
```

**Endpoint called:** `/llm-research` ($0.30)

**Response:** Condensed summary with key takeaways.

---

## Prompt Writing Tips

Remember the **180 character limit**. Keep prompts concise:

**Good:**
- "What is account abstraction?" (28 chars)
- "Explain perpetual futures funding" (34 chars)
- "How do zkRollups work?" (22 chars)

**Too long - needs shortening:**
- "Can you explain in detail how account abstraction works in Ethereum, including ERC-4337, bundlers, paymasters, and the user operation flow?" (139 chars - close to limit)

**Shortened version:**
- "Explain ERC-4337 account abstraction" (36 chars)

---

## Combining with Market Intelligence

Research works well combined with other Otto AI skills:

```python
# Pseudo-code workflow

async def deep_dive_token(symbol: str):
    # Get market data first
    alpha = await call_x402(
        "https://x402.ottoai.services/token-alpha",
        {"token_symbol": symbol}
    )

    # If it's a new protocol, research it
    if alpha.project_age < "6 months":
        research = await call_x402(
            "https://x402.ottoai.services/llm-research",
            {"prompt": f"What are the risks of {symbol} protocol?"}
        )

    return combine_analysis(alpha, research)
```

---

## Cost Summary

| Task | Cost |
|------|------|
| Single question | $0.30 |
| Image analysis | $0.30 |
| Webpage summary | $0.30 |

The research endpoint is best for:
- Explaining complex concepts
- Analyzing images/charts
- Summarizing long articles
- Answering specific technical questions
