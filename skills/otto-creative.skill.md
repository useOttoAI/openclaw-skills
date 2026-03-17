---
name: otto-creative
description: AI image and video generation from Otto AI - Gemini 3 Pro & Sora 2
emoji: 🎨
homepage: https://docs.useotto.xyz
---

# Otto AI Creative Tools

Generate professional images and videos using cutting-edge AI models via Otto AI's x402 API.

**Models:**
- **Image Generation:** Google Gemini 3 Pro Image Preview (Nano Banana Pro)
- **Video Generation:** OpenAI Sora 2 / Sora 2 Pro

## Payment

All endpoints require x402 payment in **USDC** on:
- **Base** (chain ID: 8453) - recommended
- **Solana** (chain ID: solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp)

Payment is handled automatically via the x402 protocol headers.

---

## Endpoints

### 1. Image Generation ($0.50)

**URL:** `GET https://x402.ottoai.services/generate-meme`

**Use when:** User wants to generate images, memes, logos, illustrations, or edit existing images.

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `prompt` | string | Yes | Detailed description (100+ characters recommended for best results) |
| `image_url` | string | No | Public URL to an image for editing/composition (PNG, JPEG, WEBP, GIF) |
| `aspect_ratio` | string | No | Output ratio: "1:1" (default), "16:9", "9:16", "4:3", "3:4", etc. |

**Returns:** PNG image URL.

**Capabilities:**
- Text-to-image generation
- Image editing via URL input
- High-fidelity text rendering (great for memes)
- Real-time Google Search grounding for topical content

**Safety:** Prompts must meet Gemini Safety Policies (no violence, NSFW, etc.)

**Example prompts:**
- "Create a meme about Bitcoin going to the moon with an astronaut otter"
- "Generate a professional logo for a DeFi protocol called 'YieldMax'"
- "A photorealistic image of a robot trading on multiple screens"

---

### 2. Video Generation ($1.00–$7.50, dynamic)

**URL:** `GET https://x402.ottoai.services/video-gen`

**Use when:** User wants AI-generated video clips.

**Dynamic Pricing:** Price depends on model and duration.
| Model | Rate | 4s | 8s | 12s |
|-------|------|-----|-----|------|
| `sora-2-2025-12-08` (Standard) | $0.25/sec | $1.00 | $2.00 | $3.00 |
| `sora-2-pro` (Pro) | $0.625/sec | $2.50 | $5.00 | $7.50 |

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `prompt` | string | Yes | Descriptive prompt (20-500 chars). Be specific about motion and camera movement. |
| `model` | string | Yes | "sora-2-2025-12-08" (Standard) or "sora-2-pro" (Pro) |
| `seconds` | string | Yes | Video duration: "4", "8", or "12" |
| `orientation` | string | No | "portrait" (720x1280, default) or "landscape" (1280x720) |
| `image_url` | string | No | Public URL to an image for image-to-video generation (PNG, JPEG, WEBP, GIF) |

**Returns:** MP4 video URL with synced audio (valid for 7 days).

**Safety:** Prompts must meet OpenAI content policy.

**Example prompts:**
- "A crypto trader celebrating as charts go green, cinematic lighting"
- "Abstract visualization of blockchain transactions flowing through a network"

---

## Quick Reference

| Endpoint | Price | Output | Model |
|----------|-------|--------|-------|
| `/generate-meme` | $0.50 | PNG image | Gemini 3 Pro |
| `/video-gen` (standard, 4s) | $1.00 | 4s MP4 | Sora 2 |
| `/video-gen` (standard, 8s) | $2.00 | 8s MP4 | Sora 2 |
| `/video-gen` (standard, 12s) | $3.00 | 12s MP4 | Sora 2 |
| `/video-gen` (pro, 4s) | $2.50 | 4s MP4 | Sora 2 Pro |
| `/video-gen` (pro, 8s) | $5.00 | 8s MP4 | Sora 2 Pro |
| `/video-gen` (pro, 12s) | $7.50 | 12s MP4 | Sora 2 Pro |

---

## Best Practices

### Image Generation
- **Longer prompts = better results.** Aim for 100+ characters.
- Describe style, mood, lighting, and composition.
- For memes, describe text placement and style.

### Video Generation
- Describe the **motion** you want (camera pan, zoom, subject movement).
- Include **scene details** (lighting, atmosphere, style).
- Keep prompts focused on a single scene or action.

---

## Generation Time

- **Images:** ~10-30 seconds
- **Video Standard:** ~2-3 minutes
- **Video Pro:** ~5-10 minutes

---

## Documentation

Full API documentation: https://docs.useotto.xyz/acp-swarm/x402

Interactive endpoint explorer: https://x402scan.com/server/2a58f75f-bd11-4020-a347-0e1c7f4912ef
