---
name: otto-creative
description: AI image and video generation from Otto AI - GPT Image 2, Nano Banana Pro, Seedance 2.0, Sora 2, Veo 3.1
emoji: 🎨
homepage: https://docs.useotto.xyz
---

# Otto AI Creative Tools

Generate professional images and videos using cutting-edge AI models via Otto AI's x402 API (multi-model, powered by fal.ai).

**Models:**
- **Image Generation:** OpenAI GPT Image 2 (default — strongest typography + photorealism), Google Nano Banana Pro (memes, stylized compositions)
- **Video Generation:** ByteDance Seedance 2.0 (default — cinematic, native synced audio), OpenAI Sora 2, Google Veo 3.1

## Payment

All endpoints require x402 payment in **USDC** on:
- **Base** (chain ID: 8453) - recommended
- **Polygon** (chain ID: 137)
- **Solana** (solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp)

Payment is handled automatically via the x402 protocol headers.

---

## Endpoints

### 1. Image Generation ($0.15 flat)

**URL:** `POST https://x402.ottoai.services/generate-meme`

**Use when:** User wants to generate images, memes, logos, illustrations, or edit existing images.

**Parameters** (send as a JSON request body):
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `prompt` | string | Yes | Detailed description (100+ characters recommended for best results) |
| `model` | string | No | `"gpt-image-2"` (default) or `"nano-banana-pro"` |
| `image_url` | string | No | Public URL to an image for editing/remixing (PNG, JPEG, WEBP, GIF) |
| `aspect_ratio` | string | No | `"1:1"` (default), `"16:9"`, `"9:16"` |

**Returns:** PNG image URL (valid for 24h).

**Capabilities:**
- Text-to-image generation
- Image editing via URL input
- High-fidelity text rendering (great for memes)

**Safety:** Prompts must meet the selected model's safety policy. A paid call that trips the provider's safety filter cannot be refunded on x402 — keep prompts clean.

**Example prompts:**
- "Create a meme about Bitcoin going to the moon with an astronaut otter"
- "Generate a professional logo for a DeFi protocol called 'YieldMax'"
- "A photorealistic image of a robot trading on multiple screens"

---

### 2. Video Generation (dynamic, ~$0.46–$4.60)

**URL:** `POST https://x402.ottoai.services/video-gen`

**Use when:** User wants AI-generated video clips.

**Dynamic Pricing:** at-cost fal.ai rate + 15% margin, $0.05 floor. The exact quote is computed per request (model × duration) and returned in the 402; the advertised price is the Seedance 5s reference quote (~$1.75).
| Model | Approx. rate | 5s | 8s |
|-------|------|-----|-----|
| `seedance-2.0` (default) | ~$0.35/s | ~$1.75 | ~$2.79 |
| `sora-2` | ~$0.12/s | ~$0.58 | ~$0.92 |
| `sora-2-pro` | ~$0.58/s | ~$2.88 | ~$4.60 |
| `veo-3.1` | ~$0.46/s | ~$2.30 | ~$3.68 |

**Parameters** (JSON request body):
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `prompt` | string | Yes | Descriptive prompt (20-1000 chars). Be specific about motion and camera movement. |
| `duration` | integer | Yes | Duration in seconds, 4-10 (per-model caps enforced) |
| `model` | string | No | `"seedance-2.0"` (default), `"sora-2"`, `"sora-2-pro"`, or `"veo-3.1"` |
| `aspect_ratio` | string | No | `"16:9"` (default), `"9:16"`, `"1:1"` |
| `image_url` | string | No | Public URL to an image for image-to-video (auto-routes to the model's i2v variant) |

**Returns:** 720p MP4 video URL with synced audio (valid for 24h).

**Safety:** Prompts must meet the selected model's content policy.

**Example prompts:**
- "A crypto trader celebrating as charts go green, cinematic lighting, slow dolly-in"
- "Abstract visualization of blockchain transactions flowing through a network"

---

## Quick Reference

| Endpoint | Price | Output | Models |
|----------|-------|--------|--------|
| `/generate-meme` | $0.15 flat | PNG image (24h URL) | GPT Image 2 / Nano Banana Pro |
| `/video-gen` | dynamic ~$0.46–$4.60 | MP4 + audio (24h URL) | Seedance 2.0 / Sora 2 / Veo 3.1 |

---

## Best Practices

### Image Generation
- **Longer prompts = better results.** Aim for 100+ characters.
- Describe style, mood, lighting, and composition.
- For memes, describe text placement and style.

### Video Generation
- Describe motion and camera movement explicitly.
- Generation takes ~30s–3 min depending on model and duration — don't time out early.
