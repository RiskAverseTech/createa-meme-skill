# Create a Meme — agent playbook

Guidance for any agent (Cursor, Cline, Continue, or any MCP client) to make good
memes with the Create a Meme tools. Claude Code users get the same thing as a
native skill in [`skills/create-a-meme/SKILL.md`](skills/create-a-meme/SKILL.md).

## Prerequisite

The [`@createa/meme-mcp`](https://www.npmjs.com/package/@createa/meme-mcp) server
must be connected (see [`skills/create-a-meme/references/setup.md`](skills/create-a-meme/references/setup.md)).
If the `createa_meme_*` tools aren't available, it isn't connected — point the
user to setup and stop.

## Tools (pick by where the humor lives)

| Tool | Use it when | Cost |
|---|---|---|
| `createa_template_search` | You need to find a template/format first | free |
| `createa_meme_generate` | Text-to-meme — AI picks a template and writes captions from a topic | 2 |
| `createa_meme_caption` | You already know the exact template and the exact lines | 1 |
| `createa_meme_ai_image` | The joke is in the *image* — generate original AI art (± captions) | 3 |
| `createa_meme_remix` | Put a person/mascot into a new scene while keeping their face | 5 |

Full parameters, watermarks, costs: [`references/tools.md`](skills/create-a-meme/references/tools.md).

## Workflow

1. **Find the joke** — state the *turn* (the unexpected beat) in one line. If you
   can't, ask one question. A sharp idea beats a pretty render.
2. **Choose the format** by where the humor lives:
   - Words over a familiar image → `createa_meme_generate` or `createa_meme_caption`
   - The image itself → `createa_meme_ai_image`
   - A specific person/mascot → `createa_meme_remix`
   - Unsure which template → `createa_template_search` first
3. **Write the caption** — short, high-contrast, one idea. Top = setup, bottom =
   punchline. Two lines max per panel. See [`references/caption-craft.md`](skills/create-a-meme/references/caption-craft.md).
4. **Generate**, then **offer 1–2 variations** so the user can pick. Don't settle
   silently on the first output.

## Rules

- **Funny > pretty.** If it doesn't land, fix the *words* before regenerating.
- **One idea per meme.** Two jokes = zero jokes.
- **Results vary** — regenerate rather than over-explaining. Don't apologize for
  the model; offer another take.
- **Remix identity trick** — describe what to **preserve** ("keep his exact face,
  hair, and expression"), not just what to change. Identity anchors are the whole game.
- **Async** — if a tool returns a pending job, wait for the image URL before
  reporting done. Never claim an image exists until the tool returns it.
