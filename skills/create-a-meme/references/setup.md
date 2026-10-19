# Connecting the Create a Meme MCP

The skill needs the `@createa/meme-mcp` server connected. There's nothing to
install — the client runs it on demand via `npx`.

**Installed as the Claude Code plugin?** The server is already bundled; it only
needs your key in the `CAM_API_KEY` environment variable (step 1), then a
restart. If the tools report a missing key — common in desktop apps that don't
read your shell profile — add the server manually (step 2) instead. Don't keep
both: remove a manual `createa` entry once the plugin's server works.

## 1. Get a free API key
Sign up at <https://dashboard.createa.meme>. Free tier = 20 credits/month (a caption is 1 credit, an AI image 3).
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
