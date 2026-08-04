# Create a Meme — agent skill

An agent skill — for **Claude Code, Cursor, Cline, and any MCP client** — that
turns any idea into a finished meme with [Create a Meme](https://createa.meme).
It picks the right format, writes captions that actually land, generates via the
[`@createa/meme-mcp`](https://www.npmjs.com/package/@createa/meme-mcp) tools, and
offers a couple of variations — so you get a *funny* meme, not just "technically
a meme."

> Made a great meme with it? Share it and tag [Create a Meme](https://createa.meme).

## What it does

- **Text-to-meme** — describe a situation, get a captioned meme.
- **Caption a template** — you supply the format + exact lines.
- **AI meme images** — when the joke is in the picture, not the caption.
- **Remix with face-keeping** — put a person or mascot into a new scene while
  preserving their likeness.

It bakes in meme-writing craft (find the *turn*, brevity, one idea per meme) so
the output is sharp, not generic.

## Install

### 1. Connect the Create a Meme MCP (one time)

Grab a free API key at [dashboard.createa.meme](https://dashboard.createa.meme)
(20 generations/month free), then add the server. For **Claude Code**, in
`~/.claude.json`:

```jsonc
{
  "mcpServers": {
    "createa": {
      "command": "npx",
      "args": ["-y", "@createa/meme-mcp"],
      "env": { "CAM_API_KEY": "cam_live_xxxxxxxxxxxxxxxxxxxx" }
    }
  }
}
```

Cursor, Cline, and Continue use the same config shape — full details in
[`skills/create-a-meme/references/setup.md`](skills/create-a-meme/references/setup.md).

### 2. Add the skill guidance

- **Claude Code:** clone this repo and use it as a plugin, or drop
  `skills/create-a-meme/` into your project's `.claude/skills/`.
- **Cursor / Cline / any other agent:** point it at [`AGENTS.md`](AGENTS.md) —
  the same workflow in plain markdown any agent can load.

Both read the same `skills/create-a-meme/references/` files, so the guidance is
identical everywhere.

## Use

Just ask:

- *"Make me a meme about Monday standups."*
- *"Caption the Drake template — top: writing tests, bottom: writing the test that proves the bug exists."*
- *"Generate an AI meme of a cat glaring at a deploy log, top: WORKS ON MY MACHINE."*
- *"Take this photo and turn me into a firefighter — keep my exact face."*

## What's inside

```
AGENTS.md                        general playbook (any agent)
skills/create-a-meme/
  SKILL.md                       Claude Code skill (the flagship)
  references/
    tools.md                     the MCP tools, costs, watermarks
    caption-craft.md             how to write memes that land
    setup.md                     connecting the MCP
```

## Links

- App: [createa.meme](https://createa.meme)
- MCP server: [`@createa/meme-mcp`](https://www.npmjs.com/package/@createa/meme-mcp)

## License

MIT — see [LICENSE](LICENSE). Meme generation is subject to the
[Create a Meme API Terms](https://docs.createa.meme/docs/terms).
