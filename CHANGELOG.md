# Changelog

## Unreleased — 2026-11-13

List inputs: `research_filters` takes `names` (check up to 20 names in one call, `found` /
`not_found`) and `sources`; `monthly_stats` and `market_rankings` take `per: "brand"` with
`brands` (a table per brand); `ads_library_concept` takes `families`. A list call costs what the
separate calls cost. `research_filters` stays free with a daily allowance of lookups per account;
its `q` needs 3+ characters on name catalogues.

## 1.0.0 — 2026-11-09

First public entry: `server.json` for the official MCP registry, the connection README,
`docs/tools.md` generated from the live tool registry, the Claude Skill, a Claude Code plugin
manifest and `llms.txt`.
