# Marketing — Cowork plugin

Exported by Agent Collaboration Platform.

- Marketplace: `marketing-marketplace`
- Plugin: `marketing` v0.1.0-20260516
- 2 agents · 8 custom skills · 2 commands · 2 MCP connectors · 1 knowledge base

## Install

Push this repo to GitHub, then in Claude Cowork / Claude Code:

```
/plugin marketplace add <you>/<repo>
/plugin install marketing@marketing-marketplace
```

Or test locally:

```
/plugin marketplace add /absolute/path/to/this/folder
/plugin install marketing@marketing-marketplace
```

## Required environment variables

The MCP connectors in `.mcp.json` reference bearer tokens via env vars.
Set these in your shell (or your Claude Code env) before installing —
the actual tokens live in your Anthropic vault on the platform and are
not exported.

```bash
export ACP_MCP_GITHUB_TOKEN=...
```

## Knowledge bases

The `knowledge/` directory mirrors every knowledge base in the
workspace, one markdown file per KB. These files are for human
inspection and for re-import — Claude Code itself doesn't load them.
The agents that use a KB already inline its entries into their system
prompt, so installed agents work without consumer Claude opening these
files.
