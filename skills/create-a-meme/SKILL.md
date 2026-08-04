---
name: create-a-meme
description: >-
  Turn any topic, screenshot, headline, or idea into a finished meme with Create
  a Meme. Use whenever the user wants a meme, a reaction image, a captioned
  template, an AI-generated meme image, or wants to put someone into a scene
  while keeping their face. Picks the right format, writes captions that actually
  land, generates via the Create a Meme MCP tools, and offers a couple of
  variations. Requires the `@createa/meme-mcp` server to be connected.
---

# Create a Meme

Make memes that are actually funny — not just technically "a meme." This skill
turns an idea into a finished image using the Create a Meme MCP tools.

## Before you start

This skill drives the **`@createa/meme-mcp`** server. If the `createa_meme_*`
tools aren't available, the server isn't connected — point the user to
`references/setup.md` (one `npx` line + a free API key) and stop.

## The tools (pick by where the humor lives)

| Tool | Use it when | Cost |
|---|---|---|
| `createa_template_search` | You need to find a template/format first | free |
| `createa_meme_generate` | Text-to-meme — let the AI pick a template and write captions from a topic | 2 |
| `createa_meme_caption` | You already know the exact template and the exact caption text | 1 |
| `createa_meme_ai_image` | The joke is in the *image* — generate original AI art (± captions) | 3 |
| `createa_meme_remix` | Put a real person/mascot into a new scene while keeping their face | 5 |

Full parameters, watermarks, and cost detail: `references/tools.md`.

## Workflow

1. **Find the joke.** State it in one line — the *turn*, the unexpected beat. If
   you can't, ask one clarifying question. A sharp idea beats a pretty render.
2. **Choose the format by where the humor lives:**
   - Humor in the **words** over a familiar image → `createa_meme_generate`
     (topic in, AI picks template + captions) or `createa_meme_caption` (you
     supply template + exact lines).
   - Humor in the **image itself** → `createa_meme_ai_image`.
   - Putting a **specific person/mascot** into a bit → `createa_meme_remix`.
   - Unsure which template → `createa_template_search` first.
3. **Write the caption.** Short, high-contrast, one idea. Top = setup,
   bottom = punchline. Two lines max per panel. See `references/caption-craft.md`.
4. **Generate**, then **offer 1–2 variations** (a different template or a sharper
   caption) so the user can pick. Don't silently settle on the first output.

## Rules that keep memes good

- **Funny > pretty.** If it doesn't land, fix the *words* before regenerating.
- **Brevity.** No walls of text. If a caption needs a comma splice, cut it.
- **One idea per meme.** Two jokes = zero jokes.
- **Results vary** — regenerate rather than over-explaining. Never apologize for
  the model; just offer another take.

## The remix identity trick

`createa_meme_remix` holds a face across a scene change *if you describe what to
**preserve**, not just what to change*. Identity anchors like "keep his exact
face, wavy blond hair, and proud expression" are the whole game. Always name the
preserved features explicitly. Great for mascots, "put me in X," and character bits.

## Async

Generations can take a few seconds. If a tool returns a pending/job response,
poll for the result before reporting done — never claim an image exists until the
tool returns its URL.
