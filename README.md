# PowerPoint Engine — MCP Server

Generate and edit real PowerPoint (`.pptx`) files from an AI agent, over the
[Model Context Protocol](https://modelcontextprotocol.io). Backed by the hosted
**[PowerPoint Engine API](https://powerpointengine.io)** — no local PowerPoint,
Office, or GPU required.

- **Endpoint:** `https://powerpointengine.io/api/mcp/mcp` (Streamable HTTP)
- **Auth:** OAuth 2.1 (browser authorize, PKCE, dynamic client registration)
- **Website:** https://powerpointengine.io · **Docs:** https://powerpointengine.io/docs

## Install

### Claude Code

```bash
claude mcp add --transport http powerpoint-engine https://powerpointengine.io/api/mcp/mcp
```

Then run `/mcp` and authorize in the browser (one click).

### Other MCP clients

Point your client at the Streamable HTTP endpoint above. On first use it will
open the browser OAuth flow; discovery is at
`https://powerpointengine.io/.well-known/oauth-protected-resource`.

## Tools

| Tool | Purpose |
|------|---------|
| `generate_presentation` | Build a deck from simple markup (`markup`, `theme?`) → download URL |
| `generate_from_template` | Build a deck from a structured `template` (title + slides, incl. native charts) |
| `get_account_status` | Plan, remaining credits, recent generations, and recent errors |

## Markup rules

- A single `# Title` line sets the deck title.
- Each `## Heading` starts a new slide.
- `### Heading`+ are sub-headings; `-`/`*` are bullets.
- Fenced code blocks, links, `**bold**`, and inline code are cleaned up.

Themes: `corporate`, `modern`, `minimal`, `vibrant`.

## What makes it different

- **Structure-preserving edits:** send your own `.pptx` template and replace
  text/numbers while keeping the exact layout, fonts, and branding — the thing
  most generators break.
- **Native editable charts** from data (column/bar), not images.
- **Zero setup:** one hosted endpoint, OAuth, credit-based pricing (1 credit =
  up to 10 slides). Free tier returns watermarked files; Pro removes the mark.

See [`SKILL.md`](./SKILL.md) for an installable agent-skill version and
[`server.json`](./server.json) for the MCP registry manifest.

## License

MIT — see [`LICENSE`](./LICENSE). This repository contains the MCP manifest and
documentation for the hosted service; the generation engine itself is operated
at [powerpointengine.io](https://powerpointengine.io).
