# Marketing — Cowork plugin

Exported by Agent Collaboration Platform.

- Marketplace: `marketing-marketplace`
- Plugin: `marketing` v1.0.0
- 2 agents · 9 custom skills · 2 commands · 2 MCP connectors · 1 knowledge base

## Install

Two surfaces, same artifact: install via slash commands in Claude Code /
Cowork, or via the GUI in Claude Desktop. Both pull from this repo.

### Claude Code / Cowork (CLI)

From this repo:

```
/plugin marketplace add <you>/<repo>
/plugin install marketing@marketing-marketplace
```

Or locally (point at this folder on disk):

```
/plugin marketplace add /absolute/path/to/this/folder
/plugin install marketing@marketing-marketplace
```

### Claude Desktop (GUI)

**Option 1 — from this repo:** Customize → **+** Personal plugins →
Create plugin → **Add marketplace** → paste `<you>/<repo>`.

**Option 2 — from a downloaded zip:** on the platform's Distribution
page, grab the **Plugin zip (for Desktop Upload)** — *not* the
Marketplace zip. Desktop's Upload flow expects a plugin shape (skills
/ .mcp.json at the zip root), not a marketplace wrapper. Then
Customize → **+** Personal plugins → Create plugin → **Upload plugin**
→ pick the `.zip`. No GitHub needed.

_Caveat: Desktop installs the **Skills** and **Connectors** (MCP) from
this bundle. Agents and slash commands run in Claude Code / Cowork; in
Desktop they're inert. Knowledge bases are inlined into agent prompts at
publish time, so they ride along with whichever surface the agent runs on._

Third-party marketplaces in Desktop have auto-update disabled by default —
toggle it on per-marketplace from the plugin UI to get future pushes
automatically, otherwise re-add the marketplace to pull fresh.

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
