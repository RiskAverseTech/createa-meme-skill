# Connecting the Create a Meme MCP

The skill needs the `@createa/meme-mcp` server connected. There's nothing to
install — the client runs it on demand via `npx`.

**Installed as the Claude Code plugin?** The server is already bundled. Claude Code asks for your API key when you enable the plugin and keeps it in secure storage. Skip step 2, and remove any manual `createa` entry you added earlier so the tools don't appear twice.

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
      "args": ["-y", "@createa/meme-mcp@0.5.3"],
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
