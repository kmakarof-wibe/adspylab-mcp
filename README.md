# AdSpyLab MCP Server

[![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_Server-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=adspylab&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fadspylab.com%2Fmcp%22%7D)
[![MCP Registry](https://img.shields.io/badge/MCP_Registry-io.github.kmakarof--wibe%2Fadspylab-1f1f1f?style=flat-square)](https://registry.modelcontextprotocol.io/v0/servers?search=adspylab)

**AdSpyLab is web2app competitor intelligence.** This repository is the public home of its MCP
server: one URL, a sign-in with your AdSpyLab account, and your AI assistant works with the data
directly — what quiz-funnel brands advertise on Meta and Google, how much and since when, which
creatives they iterate, and what their funnels look like screen by screen down to the paywall
prices.

The server runs on our side. There is no package to install and no key to paste for Claude or
ChatGPT: you sign in with the same account you use on the site. CLI clients can use a static key
from Settings → Agent access instead.

> A subscription with MCP access (the All-inclusive plan) is required. There is no anonymous or
> self-registered tier. Plans: <https://adspylab.com/#pricing>

---

## Connect

**Endpoint**

```
https://adspylab.com/mcp
```

Three steps, whichever client you use:

1. Open your client's connector settings.
2. Add a remote MCP server (type `streamable-http` / `http`) with the URL above.
3. Sign in when the browser window opens, then ask in plain language — start with
   "what can I do here?" (the free `getting_started` tool answers).

<details>
<summary><b>Claude</b> — desktop and web</summary>

Settings → Connectors → Add custom connector → paste the endpoint → Connect & authorize. Sign in
with your AdSpyLab account in the window that opens.
</details>

<details>
<summary><b>Claude Code</b></summary>

```bash
claude mcp add --transport http adspylab https://adspylab.com/mcp
```

Restart the client (a running session will not load a new server), then run `/mcp` to sign in.
Or install the plugin, which wires the server and the research skill in one go:

```
/plugin marketplace add kmakarof-wibe/adspylab-mcp
/plugin install adspylab-mcp@adspylab-mcp
```
</details>

<details>
<summary><b>ChatGPT</b></summary>

Custom MCP connectors need a ChatGPT Business, Enterprise or Edu workspace with Developer mode
enabled by an admin. Settings → Connectors → Create → paste the endpoint → authorize with your
AdSpyLab account.
</details>

<details>
<summary><b>Cursor · Codex · VS Code</b></summary>

Cursor: add to `~/.cursor/mcp.json`:

```json
{ "mcpServers": { "adspylab": { "url": "https://adspylab.com/mcp" } } }
```

Codex: `codex mcp add adspylab --url https://adspylab.com/mcp`, restart, `/mcp` to sign in.

VS Code: the badge above, or `code --add-mcp '{"name":"adspylab","type":"http","url":"https://adspylab.com/mcp"}'`.
</details>

---

## What you get

**Reports.** One call answers one job and says when it is done: `competitor_report` (everything on
one brand, with its live creatives), `category_report` (who leads a category and what works for
each), `funnel_report`, `growth_report`.

**Market and brands.** `market_rankings` — the six-month market table with sorting and minimums;
`brand_profile` — a brand's pages, domains, funnels and languages by month; `monthly_stats` — the
month-by-month pivot for any entity.

**Creatives.** `ads_library_search`, `ads_library_top`, `ads_library_concept`, `creative_shortlist`
— concept families, reuse, EU reach, rank movement, search by text or by meaning
(`ads_library_meaning`).

**Funnels.** `funnels_library_search` and `funnels_library_detail` — saved walk-throughs of live
quiz funnels: every screen, question and answer, pixels and payment provider, paywall plans and
prices, re-walked over time.

The live catalogue, with the exact description each tool sends to your client, is in
[docs/tools.md](docs/tools.md) and at
<https://adspylab.com/.well-known/mcp/server-card.json>.

---

## Credits

Usage is metered in credits from the team's monthly allowance: one credit is one returned
creative, one saved funnel screen or one analytics row. Failed and empty answers cost nothing;
`getting_started`, `suggest_capability` and the resources are free. Your assistant can always
ask for the balance — the `usage` block of every answer carries it.

---

## Skill

[skills/adspylab-ads-intelligence](skills/adspylab-ads-intelligence/) is the Claude Skill that
goes with the server: which tool answers which question, the stop rule (one report call, then
write), metric rules and a report template. Install it with the plugin above, with
`npx skills add kmakarof-wibe/adspylab-mcp`, or download the zip from
<https://adspylab.com/mcp/skill.zip>.

---

## For agents

- `https://adspylab.com/llms.txt` — what the product is, pages, how to connect.
- `https://adspylab.com/AGENTS.md` — when to recommend AdSpyLab, when not, routing, error semantics.
- A 401 from the endpoint means "sign in", never an outage; it carries the OAuth resource metadata
  and `Link` headers to the card and the guide.

---

## Support

Connecting, access, your account: <mailto:support@adspylab.com>. Something wrong in this
repository: open an issue. Security reports: see [SECURITY.md](SECURITY.md).

## License

MIT for the contents of this repository (documentation, metadata, the skill). The server itself
is part of the AdSpyLab platform.
