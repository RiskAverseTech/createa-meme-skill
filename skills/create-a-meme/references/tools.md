# Create a Meme — tool reference

All tools come from the `@createa/meme-mcp` server. Credit costs are per
successful generation.

## `createa_template_search` (free)
Find templates by keyword or category. Use before `caption`/`generate` when the
user names a format ("the Drake one", "distracted boyfriend") or a vibe
("something for shipping a release").

## `createa_meme_generate` (2 credits)
Text-to-meme. Give it a topic/idea; the AI picks a fitting template and writes
the captions. Best default when the user describes a *situation* rather than an
exact template + lines.

## `createa_meme_caption` (1 credit)
Caption a **known** template with **exact** text you supply. Cheapest path when
you already know both the template and the top/bottom lines. Prefer this over
`generate` once the format and wording are decided.

## `createa_meme_ai_image` (3 credits)
Generate original AI imagery, with optional baked-in captions. Use when the joke
is visual (an absurd scene, a "X as a Y" transformation) rather than a caption
over a known template.

## `createa_meme_remix` (5 credits)
Edit an existing image while preserving a subject's identity — pass a reference
photo + a prompt. Describe what to **preserve** ("keep his exact face, hair, and
expression") as strongly as what to change. Best for "put this person in X",
mascot edits, and stylized portraits.

## Watermarks (Starter+ plans)
Every generation tool accepts an optional `watermark` — provide **either** `text`
**or** `logo_url`:

```jsonc
"watermark": { "text": "Green Frog Labs", "position": "bottom-right", "opacity": 0.65 }
"watermark": { "logo_url": "https://yoursite.com/logo.png", "scale": 0.15 }
```

Optional keys: `position` (4 corners + `bottom-center`), `opacity` (0–1),
`color` / `outline_color` (text hex), `scale` (logo width fraction). Free-tier
keys requesting a watermark get a 402 — it's a Starter+ feature, no per-call
upcharge.

## Notes
- Costs draw from the account's credit balance (free tier: 20 generations/month).
- Generation may be async; wait for the returned image URL before reporting done.
