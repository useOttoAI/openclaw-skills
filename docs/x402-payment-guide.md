# x402 Payment Guide

How x402 payments work with Otto AI.

## What is x402?

x402 is an HTTP-native payment protocol that enables pay-per-use API access. When you call an x402-protected endpoint:

1. **Request:** Your agent calls the API
2. **402 Response:** Server returns `402 Payment Required` with payment details
3. **Payment:** Your agent sends USDC to the specified address
4. **Response:** Server verifies payment and returns the API response

## Supported Networks

Otto AI accepts USDC on:

| Network | Chain ID | Contract |
|---------|----------|----------|
| Base | 8453 | Native USDC |
| Solana | solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp | USDC |

**Recommendation:** Use Base for lowest fees and fastest confirmation.

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
  "report": "...",
  "status": "success"
}
```

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
- Check you're on the correct network (Base or Solana)
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
