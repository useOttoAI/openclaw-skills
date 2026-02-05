# Content Creation Workflow

Example workflow using Otto AI's creative tools.

## Scenario: Creating Social Media Content

Your AI agent can generate professional content for crypto projects.

### Example 1: Meme Generation

**Prompt:** "Create a meme about Ethereum gas fees being low with a happy penguin celebrating"

**Endpoint called:** `/generate-meme` ($0.25)

**Response:** PNG image URL with the generated meme.

**Tips for better results:**
- Be descriptive (100+ characters)
- Mention style, mood, and composition
- Describe text placement for memes

---

### Example 2: Project Logo

**Prompt:** "Generate a minimalist logo for a DeFi lending protocol called LendFlow. Use blue and white colors, clean geometric shapes, representing liquidity flow. Modern fintech aesthetic."

**Endpoint called:** `/generate-meme` ($0.25)

**Response:** PNG image URL with the generated logo.

---

### Example 3: Marketing Video

**Prompt:** "A 3D animated crypto coin spinning in space with aurora borealis in the background. Camera slowly zooms in as particles emit from the coin. Cinematic, professional quality."

**Endpoint called:** `/video-gen` with `tier: "standard"` ($3.00)

**Response:** MP4 video URL (4 seconds, valid for 24 hours).

---

### Example 4: Promotional Video (Extended)

**Prompt:** "Dramatic reveal of a trading dashboard showing green charts. Camera starts from behind a silhouetted trader, slowly panning around to show their face illuminated by multiple screens. Professional, corporate feel."

**Endpoint called:** `/video-gen` with `tier: "pro"` ($8.50)

**Response:** MP4 video URL (8 seconds, valid for 24 hours).

---

## Image Editing

You can also edit existing images:

**Prompt:** "Add a 'HODL' text banner at the top of this crypto meme in bold white letters"

**Parameters:**
```json
{
  "prompt": "Add 'HODL' text banner at top in bold white letters with black outline",
  "image_url": "https://example.com/original-meme.png"
}
```

**Endpoint called:** `/generate-meme` ($0.25)

**Response:** Edited image with the text added.

---

## Sample Agent Code

```python
# Pseudo-code for an OpenClaw agent

async def create_social_content(topic: str):
    # Generate a meme about the topic
    meme = await call_x402(
        "https://x402.ottoai.services/generate-meme",
        {
            "prompt": f"Create a funny crypto meme about {topic}. Include bold text at top and bottom. Viral meme style, high contrast colors.",
            "aspect_ratio": "1:1"
        }
    )

    # If high-impact announcement, create a video too
    if topic.importance == "high":
        video = await call_x402(
            "https://x402.ottoai.services/video-gen",
            {
                "prompt": f"Dramatic announcement video about {topic}. Professional, cinematic lighting, slow motion effects.",
                "orientation": "portrait",
                "tier": "standard"
            }
        )

    return {
        "meme_url": meme.image_url,
        "video_url": video.video_url if video else None
    }
```

---

## Cost Summary

| Content Type | Endpoint | Cost |
|--------------|----------|------|
| Meme/Image | `/generate-meme` | $0.25 |
| Short Video (4s) | `/video-gen` standard | $3.00 |
| Long Video (8s) | `/video-gen` pro | $8.50 |
| Image Edit | `/generate-meme` | $0.25 |
