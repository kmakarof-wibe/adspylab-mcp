# Changelog

## Unreleased — 2026-11-16

Plan the spend: `account_balance` (free) returns the credits left, the renewal date, today's free
allowances and the typical cost of each tool — median and 90th percentile credits and the
approximate answer size in tokens, from real calls of the last 30 days. Every paid tool takes
`max_credits`, a ceiling for that one call: an answer above it is withheld, nothing is charged and
the exact price is returned (`status: "over_budget"`); `max_credits: 0` is an estimate only.
Withheld answers are limited per account per day.

A reminder when a list would do: after three calls in a row to `monthly_stats`, `market_rankings`,
`ads_library_concept` or `research_filters` with only the brand, family or `q` changing, the answer
carries `list_hint` — the single list call covering the values already sent. Same answer, same cost.

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
