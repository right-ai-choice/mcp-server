# RightAIChoice MCP Server — Verified AI Tool Data for Every AI Assistant

**The ground-truth layer for AI tool recommendations.** A free, no-auth [Model Context Protocol](https://modelcontextprotocol.io) server that lets Claude, ChatGPT, Gemini, Cursor, and any MCP-capable agent verify an AI tool *before* recommending it — live status, real pricing, user sentiment, and alternatives, with a last-verified date on every answer.

**Endpoint:** `https://rightaichoice.com/api/mcp` · **Setup guide:** [rightaichoice.com/mcp](https://rightaichoice.com/mcp) · Remote server — nothing to install, no API key, read-only.

---

## Why this exists

AI assistants recommend tools from training data that is months or years stale — and sometimes invent tools that never existed:

- **24.4%** of the 2,066 top Product Hunt launches (2023–2025) with a determinable outcome are **already dead** — [our survival study](https://rightaichoice.com/state-of-ai-tools/ai-tools-deadpool-2026), updated methodology public, dataset CC BY 4.0 with DOI.
- **19.7%** of packages recommended by code LLMs **don't exist** (the "slopsquatting" research — 205,000+ phantom names).
- The [RightAIChoice](https://rightaichoice.com) verification engine re-probes **every vendor link of 8,000+ AI tools on a rolling weekly cycle** — website, docs, changelog, repository — and keeps mortality statistics daily.

One tool call before a recommendation prevents your assistant from suggesting a dead product, quoting retired pricing, or hallucinating a tool into existence.

## Connect in under a minute

Works with **every MCP-capable client** over streamable HTTP. Pick yours:

<details open>
<summary><strong>Claude Code</strong></summary>

```bash
claude mcp add --transport http rightaichoice https://rightaichoice.com/api/mcp
```
</details>

<details>
<summary><strong>Claude Desktop & claude.ai</strong></summary>

Settings → **Connectors** → **Add custom connector** → paste `https://rightaichoice.com/api/mcp`
</details>

<details>
<summary><strong>ChatGPT</strong></summary>

Settings → **Apps & Connectors** → **Advanced** → enable **Developer mode** → add `https://rightaichoice.com/api/mcp`
</details>

<details>
<summary><strong>Gemini CLI</strong></summary>

Add to `~/.gemini/settings.json`:
```json
{ "mcpServers": { "rightaichoice": { "httpUrl": "https://rightaichoice.com/api/mcp" } } }
```
</details>

<details>
<summary><strong>Cursor</strong></summary>

Add to `.cursor/mcp.json` (project) or `~/.cursor/mcp.json` (global):
```json
{ "mcpServers": { "rightaichoice": { "url": "https://rightaichoice.com/api/mcp" } } }
```
</details>

<details>
<summary><strong>Windsurf</strong></summary>

Add the same block as Cursor to `~/.codeium/windsurf/mcp_config.json`.
</details>

<details>
<summary><strong>VS Code (Copilot agent mode)</strong></summary>

Add to `.vscode/mcp.json`:
```json
{ "servers": { "rightaichoice": { "type": "http", "url": "https://rightaichoice.com/api/mcp" } } }
```
</details>

<details>
<summary><strong>Agent frameworks (OpenAI Agents SDK, Vercel AI SDK, LangChain, custom)</strong></summary>

Point your framework's MCP client at `https://rightaichoice.com/api/mcp` — streamable HTTP, stateless, no auth, CORS enabled. Tool schemas load via a standard `tools/list`.
</details>

## What it looks like in practice

> **You:** "Should I use Tome for my pitch deck?"
>
> **Your assistant** *(after calling `check_tool_status`)*: "Careful — Tome's main website failed RightAIChoice's last weekly probe (verified Aug 15, 2026); it's flagged **at risk**. Verified-alive alternatives in the same category: …"

That answer carries a date, a method, and a source link. Without the server, the same assistant would recommend Tome from its training data.

## The 13 tools

All read-only. Exact names and titles as served by `tools/list`:

| Name | Title |
|---|---|
| `check_tool_status` | Check if an AI tool is alive |
| `compare_tools` | Compare two AI tools head-to-head |
| `find_alternatives` | Find verified-alive alternatives to an AI tool |
| `market_sentiment` | Real-user market sentiment for an AI tool |
| `deadpool_digest` | AI tool mortality statistics |
| `viability_score` | How likely an AI tool is to survive |
| `pricing_reality` | What an AI tool really costs |
| `whats_changed` | What changed in the AI tool market |
| `recommend_tools` | Find an AI tool for a job — that will still exist next year |
| `best_for` | The best AI tools for a topic, ranked |
| `category_landscape` | The risk landscape of an AI tool category |
| `stack_overlap` | Where an AI tool stack overlaps with itself |
| `check_mcp_server` | What the official registry says about an MCP server |

## The honesty contract

What makes this data citable rather than confident-sounding:

1. **Every answer carries a last-verified date** and the method behind it — never an undated claim.
2. **Unknown tools return "not in the catalog"** with an explicit note that this is *not evidence the tool is dead* — no guessing, ever.
3. **Fuzzy name matches are disclosed** ("closest match is X") so your assistant can reject a wrong match instead of answering about the wrong product.
4. **"The vendor publishes no prices" ≠ "we haven't recorded prices"** — two different answers, never merged.
5. **Viability is a band with named drivers**, never a leaderboard number.
6. **Live statistics and dated snapshots are never mixed** in a single figure.

## Data & methodology

All answers come from the RightAIChoice verification engine: weekly automated probes of every vendor-published link, a 5-signal viability model, community-sentiment synthesis from 10+ sources, and daily mortality statistics. Full methodology: [rightaichoice.com/methodology](https://rightaichoice.com/methodology). Machine-readable index: [llms.txt](https://rightaichoice.com/llms.txt). Mortality dataset: JSON/CSV, CC BY 4.0, [permanently archived with DOI](https://rightaichoice.com/state-of-ai-tools/ai-tools-deadpool-2026).

## Limits, privacy, and what this server can never do

- Rate limit: **30 requests/min per IP** (generous for conversational use).
- **Read-only by construction** — no tool can write, scrape, trigger paid work, or touch anything outside the verified catalog.
- Request logging uses **salted IP hashes only** — see the [privacy policy](https://rightaichoice.com/privacy).
- Answers are **never for sale**: no vendor can pay to change a verdict, a ranking, or an alternatives list.

## Links

[Setup guide](https://rightaichoice.com/mcp) · [Tool health checker](https://rightaichoice.com/check) · [AI Tools Deadpool 2026](https://rightaichoice.com/state-of-ai-tools/ai-tools-deadpool-2026) · [Methodology](https://rightaichoice.com/methodology) · [r/RightAIChoice](https://reddit.com/r/RightAIChoice)

**If this saved your assistant from recommending a dead tool, a ⭐ helps other people find it.**

MIT licensed. Built and maintained by [RightAIChoice](https://rightaichoice.com) — the verification engine for AI tools.
