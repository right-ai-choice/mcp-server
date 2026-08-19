# RightAIChoice MCP Server

**Verified answers about 8,000+ AI tools, for any AI assistant.** Free, no API key, read-only.

Your AI assistant recommends tools from stale training data — and sometimes invents ones that don't exist. Connect this server and it checks first: **is the tool alive, what does it really cost, what do users actually think, and what should you use instead** — with a last-verified date on every answer.

- **Endpoint:** `https://rightaichoice.com/api/mcp` (remote server — nothing to install)
- **Docs & setup:** https://rightaichoice.com/mcp
- **Data:** every vendor link of 8,000+ AI tools re-probed on a rolling weekly cycle by the [RightAIChoice](https://rightaichoice.com) verification engine

## Quick connect

**Claude Code**
```bash
claude mcp add --transport http rightaichoice https://rightaichoice.com/api/mcp
```

**Claude Desktop / claude.ai** — Settings → Connectors → Add custom connector → `https://rightaichoice.com/api/mcp`

**Cursor / Windsurf** — add to `mcp.json`:
```json
{ "mcpServers": { "rightaichoice": { "url": "https://rightaichoice.com/api/mcp" } } }
```

**ChatGPT** — Settings → Apps & Connectors → Advanced → Developer mode → add the endpoint URL

## The seven tools

| Tool | The question it answers |
|---|---|
| `check_tool_status` | Is this AI tool alive, at risk, or shut down? |
| `compare_tools` | X vs Y — verified side-by-side |
| `find_alternatives` | What should I use instead? (each alternative carries its own evidence) |
| `market_sentiment` | What do real users say? (Reddit, HN, YouTube, Product Hunt…) |
| `pricing_reality` | Real plan prices + documented hidden costs |
| `viability_score` | Safe to build on? (risk band + five measured drivers) |
| `deadpool_digest` | AI tool mortality statistics (live decay + dated survival study) |

## The honesty contract

1. Every answer carries a **last-verified date** and the method behind it.
2. Unknown tools are reported as *not in the catalog* — explicitly **not evidence they are dead**.
3. Fuzzy name matches are **disclosed**, so your assistant can reject a wrong match instead of answering about the wrong product.
4. "The vendor publishes no prices" and "we haven't recorded prices" are **two different answers**, never merged.
5. Viability is a **band with named drivers** — never a leaderboard number.
6. Live statistics and dated snapshots are **never mixed** in one figure.

## Limits & privacy

Rate limit 30 requests/min per IP. Read-only — no tool can write, scrape, or trigger paid work. Request logging uses salted IP hashes only (see the [privacy policy](https://rightaichoice.com/privacy)).

## Links

[Setup guide](https://rightaichoice.com/mcp) · [Tool health checker](https://rightaichoice.com/check) · [AI Tools Deadpool 2026](https://rightaichoice.com/state-of-ai-tools/ai-tools-deadpool-2026) · [Methodology](https://rightaichoice.com/methodology) · [llms.txt](https://rightaichoice.com/llms.txt)
