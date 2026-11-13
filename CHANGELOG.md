# Changelog

## 1.1.0 — 2026-11-13

List inputs: `research_filters` takes `names` (check up to 20 names in one call, `found` /
`not_found`) and `sources`; `monthly_stats` and `market_rankings` take `per: "brand"` with
`brands` (a table per brand); `ads_library_concept` takes `families`. A list call costs what the
separate calls cost. `research_filters` stays free with a daily allowance of lookups per account;
its `q` needs 3+ characters on name catalogues.

TikTok and companies: `market_rankings`, `monthly_stats`, `brand_profile`, `research_filters` and
`recent_updates` take `source: "tiktok"` — the TikTok Commercial Content Library (ads shown in the
EEA, UK and Switzerland), with `page_name` being the advertiser; counts are not comparable across
sources. On every source `entity_type: "company"` ranks the companies behind the landing domains,
`companies` filters by them, and `research_filters {dimension: "companies"}` lists the exact names.

## 1.0.0 — 2026-11-09

First public entry: `server.json` for the official MCP registry, the connection README,
`docs/tools.md` generated from the live tool registry, the Claude Skill, a Claude Code plugin
manifest and `llms.txt`.
