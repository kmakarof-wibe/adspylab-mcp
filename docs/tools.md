# Tools

Every tool the AdSpyLab MCP server registers, with the description the server itself sends to a connected client. Free tools never use credits.

## `getting_started` · free

Read this FIRST. A human-readable guide to what AdSpyLab data you can ask for through your assistant, with example questions, how the row limit works, and tips. Free — does not use any quota.

## `suggest_capability` · free

Report a MISSING AdSpyLab capability. Call this when the user asked for ad-intelligence data that no existing tool can answer — a breakdown, metric, filter or time granularity we do not offer. Describe ONLY the missing capability in neutral product terms. Never include the user's identity, their clients, their business plans, or any confidential context. Free — uses no quota.

## `queued_query` · free

Manage a deep query that was offered a place in the queue. action="accept" to confirm the user will wait (ASK THEM FIRST — the wait can be many minutes), "decline" to drop it, "check" to see whether the result is ready. Poll with "check" no more than once a minute. Free — it never uses quota.

## `competitor_report`

One-call competitor report for ONE brand or domain: monthly volume, domains, funnels, pages, languages, landing pages, longest-running copy, PLUS the top-10 live proven creatives, top concept families (per product line when several) and files shared with other brands. Sections with facts, coverage, next_steps and done. Never chain brand_report + shortlist + top yourself — this is that chain, cheaper.

## `category_report`

One-call category report — who leads and what works for each: top brands with volume and trend, their top-5 funnels, per brand the top-10 live proven creatives and strongest concept family, files shared across brands, fastest-growing and new brands. Sections with facts, coverage, next_steps and done. Use instead of a per-brand fan-out. Exact category name (adspylab://categories).

## `funnel_report`

One-call funnel report for a category or one brand/domain: fastest-growing and brand-new funnels, each with its OWNER, landing URL, localised URL variants and monthly series, then the owners' live creatives. Ranked by (brand, funnel) — a funnel name repeats across advertisers. Sections with facts, coverage, next_steps and done.

## `growth_report`

WHO is growing when the user names NO advertiser: the fastest-growing brands, Facebook pages, funnels or domains, market-wide or inside one category, each with what it runs now. window "month" = last two COMPLETE months of volume; "14d"/"7d" = EU reach gained + ads launched in the window. Never ask the user for a brand first.

## `brand_profile`

The dedicated brand page in one call: source-specific monthly activity, growth, top20 plus Others drilldown, nested domain–funnel rankings, top pages and language sets, leading funnel URL and dashboard links. Meta or Google. Saved funnel screens are fetched separately with funnels_library_detail; advertising volume is not spend.

## `market_rankings`

Overview / Monthly Stats ranking using the exact dashboard source and filters. Default six complete months: Total, each month, Last M % and Last 3M %. Sort the entire filtered dataset before pagination. Supports Meta and Google, lists of brands/categories/domains, URL text, Google country/type/legal entity, and a last-complete-month ad minimum.

## `research_filters`

Discover exact filter values and counts for Meta/Google research. Returns only the matching bounded subset; use q to resolve a brand/category instead of guessing spellings. Source must match the subsequent research call. dimension topics / subtopics = place a free phrase in the creative-family topic catalogue (ranked by name, subtopics, definition and, when available, multilingual meaning; counts = labelled families) — the way to find a topic scope for ads_library_top / monthly_stats when you do not know its exact name; no match is reported as such.

## `recent_updates`

New catalog brands, funnels and Facebook pages from the last seven days, as on Overview. Source-scoped; Google returns brands only. These are additions to this database, not proof the businesses or campaigns launched that day.

## `funnels_library_search`

Find saved Funnels Library captures or individual screens. Filter by brand, category, domain, fan page, funnel name, language, URL text, screen kind, text or tracker. Captures are saved walkthroughs, independent of the advertising period. Does not launch a crawl. Requires Funnels Library access.

## `funnels_library_detail`

Read one saved funnel capture: ordered screens, questions, options, CTAs, visible pricing and preview links. Use run_id from search, or an exact landing URL from brand_profile. Supports bounded screen pagination; never starts a new capture. Requires Funnels Library access.

## `ads_library_meaning`

Ads Library Meaning search with the same metadata/date/metric filters applied before semantic candidate retrieval as the UI. Returns family representatives from at most 120 relevance candidates; metric sorts reorder that candidate set, not the entire library. Meta only, requires Ads Library access. Search sources are returned explicitly; never assume spoken transcripts are indexed. The answer carries scope_hint — the topics and brands the matching creatives belong to — so a phrase with no catalogue topic still yields a scope for ads_library_top.

## `ads_library_guide` · free

Read this BEFORE using the ads_library_* tools: what a concept family is, what the Strong candidate score means, and the recipe for finding a competitor's (or a category's) top-performing creatives. Free — no quota used.

## `ads_library_top`

Top concept families (hook x body video pairs / static design families) for ONE brand or category — or WHOLE-MARKET with a growth sort (eu7, eu14, ads7, momentum) and no scope: "which templates grew this week" = {sort: "eu7"} or {sort: "ads7"}, never ask for a brand first. Default sort strong_candidate (calibrated 0-100); any dashboard sort; filters kind, lang, first-seen dates, q, min_ads, funnel_name / page_name / url_contains, topic / subtopic / format (a topic alone is a scope: "top concepts in tai chi" = {topic: "Tai chi"}; names in adspylab://topics; topics label families with 20+ ads as of 2026-09-30 — NEW concepts have none yet, catch them by category / brands + sort newest), lists; thresholds min_<key> / max_pos; offset. Returns per-family metrics, the family name / description / topic / subtopic / format, + the top creative. Row-level: costs per row.

## `ads_library_concept`

One concept family in depth: metrics, the creatives inside (most-advertised first; sortable, thresholds, offset), the brands running it and the destination domains. family_id (+ family_hook_id) from ads_library_top / ads_library_search. Row-level: costs per row.

## `ads_library_search`

The creative library: text search (words AND, "quoted" phrase, over ad texts + brands + domains) and/or filters (brand, category, lang, kind, first-seen dates, min_ads, funnel_name / page_name / url_contains, lists), every dashboard sort, thresholds min_<key> / max_pos, offset. Lookup by identifier: asset_ids (creative ids) or ad_archive_ids (Meta Ad Library ids) — each a scope on its own; never put an id into q. Needs q or brand/category or ids — except a growth sort (eu7, eu14, ads7, momentum), which runs WHOLE-MARKET with no filter. Returns creatives with family_id (drill via ads_library_concept). Row-level: costs per row.

## `creative_shortlist`

"What to copy today": server-side gates over the FULL scoped set — alive, spending, owned, proven — ranked by EU reach gained in the window, with a reason per row and considered/passed/rejected_by counters. Scope: brand and/or category, or one funnel_name / page_name ("what works on THIS funnel"). Row-level media: expensive per row.

## `monthly_stats`

Month-by-month pivot — the dashboard's Monthly Stats table: rows are brand | domain | category | funnel_name | page_name | language | url, each with per-month ads + visuals, window totals, 3-month growth and MoM; sort by total, last3m, mom, name or one month. Drill into a row by pinning it as a filter (brand="X" with entity_type="domain"; a language row via language_cell). url rows need brand, domain or funnel_name. source fb/google, exact dates or list filters; six complete months by default. TOPICS: entity_type topic | subtopic | format = what the market / a brand advertises by creative theme (e.g. tai chi, wall pilates, anxious attachment) or production format (UGC talking head, text hook over footage…); pin topic / subtopic / format to unfold it (entity_type="brand", topic="Tai chi" = who buys tai chi). Names from adspylab://topics.

## `watchlist_snapshot`

Monthly ad volume for a fixed watchlist of brands and/or domains. Returns per entity per month: total ads, distinct visuals (unique creative media) and distinct funnel count. At least one brand or domain is required (max 20 entries total).

## `category_top_brands`

DEPRECATED — use monthly_stats (entity_type="brand", category=...): the same top plus the monthly series and column sorting. Still works, will be removed later. Top brands by ad volume within one category over the last N complete months plus the running month so far. Category is required; use exact category names from the dashboard (e.g. "Astrology & Spirituality", "AI Tools & Productivity", "Health").

## `brand_deep_dive`

Deep dive on one brand or one domain: monthly series (ads + distinct visuals) plus top domains and top funnels. Provide either brand or domain.

## `niche_search`

Find brands/funnels whose funnel URL, funnel name or FB page name matches a keyword (e.g. "meditation", "language learning"). Min 3 characters.

## `trending_entities`

DEPRECATED — use monthly_stats (sort_by="mom" or "last3m", with min_monthly_ads): the same ranking plus the full monthly series. Still works, will be removed later. Fastest-growing entities: compares the last complete month with the one before it — deliberately NOT the running month, whose month-to-date count would read as a collapse against a full one. entity_type is one of brand | domain | category | funnel_name | page_name.

## `market_overview`

Market scan of a category (or the whole market) over N complete months plus the running month: top brands by volume, fastest-growing (last two COMPLETE months), brand-new this month, top funnels.

## `competitor_watch`

Weekly-style watch of up to 10 competitors (brands and/or domains): for each, last complete month vs the month before — ad volume, change, distinct visuals, and how many funnels are active. Use for the recurring "what changed for my competitors" check.

## `funnel_map`

Reconstruct one advertiser's funnel: their landing pages grouped by destination, with ad volume and how many distinct ad texts point at each. Provide exactly one brand or one domain. Row-level data — costs more per row than aggregate tools.

## `creative_teardown`

Top ad creatives for one advertiser: the actual ad copy/hook, CTA, landing page and running duration, longest-running first (a long run = a market-validated winner). Provide exactly one brand or one domain. Row-level data — costs more per row.

## `creative_visuals`

The ad files themselves: signed still/video URLs (they expire — use promptly), for exactly ONE of brand, domain, category or asset_ids (exact creative ids, any age). Sorts: longest_running (default), most_ads, newest, momentum, eu/eu7/eu14, pos/dpos7/dpos14, active/act7/act14, alive/lastseen, brands; offset. Row-level media: the most expensive rows.

## `shared_creatives`

Byte-identical creative files run by MORE THAN ONE brand — white-label operations, shared production houses, brand families. Scope: a brand (who shares with them) or a category. Returns no images: use creative_visuals to see one.

## `brand_report`

One-call picture of one brand or domain: monthly ad + creative volume, the domains, funnels and Facebook pages it runs (Ad Library links), language mix, top landing pages, longest-running creatives with copy. Replaces brand_deep_dive + funnel_map + creative_teardown, cheaper than the three.

