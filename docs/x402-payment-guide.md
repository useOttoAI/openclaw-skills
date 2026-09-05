# x402 Payment Guide

How x402 payments work with Otto AI.

## What is x402?

x402 is an HTTP-native payment protocol that enables pay-per-use API access. When you call an x402-protected endpoint:

1. **Request:** Your agent calls the API
2. **402 Response:** Server returns `402 Payment Required` with payment details
3. **Payment:** Your agent sends USDC to the specified address
4. **Response:** Server verifies payment and returns the API response

## Supported Networks

Networks are PER ROUTE, not storefront-wide:

| Network | Chain ID | Contract | Coverage |
|---------|----------|----------|----------|
| Base | 8453 | Native USDC | Every route |
| Solana | solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp | USDC | Only the routes whose 402 lists it |

**Recommendation:** fund on **Base** — it is accepted on every route, and it has the lowest fees and
fastest confirmation. A Solana-only wallet can pay for calls to 67 of the 90 routes — the ones that offer a Solana accept: read
that route's `accepts[]` array (returned in BOTH the `PAYMENT-REQUIRED` header and the 402 JSON body),
or `x-payment-info.networks` in `https://x402.ottoai.services/openapi.json`.

---

## Payment Flow

### 1. Initial Request

```http
POST https://x402.ottoai.services/crypto-news
Content-Type: application/json
```

### 2. Payment Required Response

```http
HTTP/1.1 402 Payment Required
PAYMENT-REQUIRED: {payment_details}
```

The `PAYMENT-REQUIRED` header contains:
- **payTo:** Address to send payment
- **amount:** Amount in base units (e.g., 10000 = $0.01 USDC with 6 decimals)
- **network:** Chain ID for payment

### 3. Payment Signature

After sending payment, include the signature in your request:

```http
POST https://x402.ottoai.services/crypto-news
Content-Type: application/json
PAYMENT-SIGNATURE: {payment_proof}
```

### 4. Success Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "status": "success",
  "data": { "report": "..." },
  "meta": {
    "generatedAt": "2026-08-10T12:00:00.000Z",
    "stalenessSec": 1739,
    "degraded": false,
    "sourceHealth": { "crypto-news-cache": "ok" }
  }
}
```

`meta` tells you how old the data is. `generatedAt` is when the response was built and is **not** a freshness claim about the data itself. `stalenessSec` is the age of our cached snapshot; `dataAsOf` is the vintage of the observations, as the upstream declared it. `degraded` is `true` when an older good version was served because a refresh failed.

Both `stalenessSec` and `dataAsOf` use the same three-state encoding: a value means the real figure, `null` means we looked and there genuinely is no value, and an absent key means the endpoint has no such concept and makes no claim. A live pass-through endpoint omits `stalenessSec` because it holds no snapshot to age.

Each endpoint publishes its own output shape in its 402 challenge — read that rather than trusting this sample.

---

## OpenClaw Integration

If you're using OpenClaw, the payment flow is handled automatically:

1. Configure your agent with a funded wallet
2. Call Otto AI endpoints normally
3. OpenClaw handles 402 negotiation and payment

---

## Discovery Document

Otto AI publishes a discovery document at:

```
https://x402.ottoai.services/.well-known/x402
```

This lists:
- All available endpoints
- Pricing
- Supported networks
- Documentation links

---

## Payment Address

All x402 payments go to:

```
0x0E84dDEdAaE6A779c462C22a59F301EC31B6b808
```

This is Otto AI's x402 payment receiving wallet on Base.

---

## Testing

### Check if an endpoint is working:

```bash
curl -I https://x402.ottoai.services/crypto-news
```

You should see a `402 Payment Required` response with payment headers.

### View discovery document:

```bash
curl https://x402.ottoai.services/.well-known/x402
```

---

## Troubleshooting

### "402 Payment Required" keeps returning

- Verify your wallet has sufficient USDC
- Check you're on a network THIS route accepts — read its `accepts[]` (Base is on every route; Solana only where the challenge lists it)
- Ensure payment signature is included in follow-up request

### "Insufficient funds"

- Minimum payment amounts vary by endpoint (see pricing)
- Account for gas fees when funding your wallet

### Timeout errors

- Video generation can take 5-10 minutes
- Set appropriate timeout values in your agent

---

## Resources

- **x402 Protocol:** https://x402.org
- **Otto AI Docs:** https://docs.useotto.xyz/acp-swarm/x402
- **x402scan (Explorer):** https://x402scan.com/server/2a58f75f-bd11-4020-a347-0e1c7f4912ef
