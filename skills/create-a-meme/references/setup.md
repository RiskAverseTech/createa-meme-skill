# Connecting the Create a Meme MCP

The skill needs the `@createa/meme-mcp` server connected. There's nothing to
install — the client runs it on demand via `npx`.

## 1. Get a free API key
Sign up at <https://dashboard.createa.meme>. Free tier = 20 generations/month.
The key looks like `cam_live_xxxxxxxxxxxxxxxxxxxx`.

## 2. Add the server

**Claude Code** — `~/.claude.json` (or project `.claude/mcp.json`):
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

**Cursor** — `~/.cursor/mcp.json`: same shape.
**Cline / Continue:** same stdio config.

## 3. Restart the client
The `createa_meme_*` tools should now be available. Ask: *"Make me a meme about
Monday standups."*

## Optional env
| Var | Default | Purpose |
|---|---|---|
| `CAM_API_KEY` | — | **Required.** Your createa.meme key. |
| `CAM_BASE_URL` | `https://api.createa.meme` | Self-host / staging override. |
