# Report template (competitor or category)

Use when the user asks for a report, a page or a document. Use the matching report or research tool. Avoid repeating its data with extra
calls; fetch another surface only when the requested report needs it. A Google
report uses brand_profile / market_rankings, not Meta-only creative reports.
If a section is unavailable or access-restricted, identify that boundary.

## Structure

1. **Title and scope line** - brand or category, window (months), data as of
   the newest date in the answer, the actual source returned (Meta or Google), and the exact period. Saved funnel
   captures have their own date, separate from the advertising period.
2. **Verdict** - 2-3 sentences: what is happening and what to do about it.
3. **Sections in the tool's order**, each as: the `facts` lines first (they are
   the computed backbone - quote the numbers as given), then a compact table
   from `data`, then that section's `caveats` in one line.
   - Competitor: Volume -> Domains and funnels -> Pages and languages ->
     Landing pages -> Longest-running copy -> Live and proven creatives
     (shortlist) -> Top concept families -> Shared creative files.
   - Category: Category overview -> one block per brand (volume and trend,
     `top_funnels`, live creatives, strongest concept) -> Shared creative
     files across the category.
4. **Coverage** - from `coverage`: how many brands of the category were
   profiled, how many creatives were considered vs shown, which months.
5. **Caveats** - EU-only reach (null = not visible), the running month is
   partial, page ranks are per page, shared files are not proof of copying,
   preview links expire in about an hour.
6. **Links** - every creative: `dashboard_url` + `ad_library_url`; every
   family: `dashboard_url`. Never invent links.

## Visual blocks (the agent tab only)

Inside AdSpyLab's own agent tab a report can show a chart and the creatives
themselves. You do NOT draw them: you put a reference on its own line and the
page renders it from the same answer you are writing from.

    [[chart: Testora]]                      - ads per month for that advertiser
    [[chart: Testora - testora_fl_iq_tp1]]  - ads per month for that funnel
    [[creatives: Testora]]                  - that advertiser's live creatives
    [[creatives: Testora - testora_fl_iq_tp1]]  - that funnel's live creatives

Rules:

- The label must name an advertiser (or "advertiser - funnel") that the answer
  actually carries. A label nothing matches renders nothing and is reported as
  an error, exactly like an invented number.
- One chart per section at most, right after that section's facts; one
  creative strip per section, after its table. A page of pictures is not a
  report.
- The block does not replace the table or the numbers - it is read alongside
  them. Say in the prose what the reader should notice in it.
- When the tool answer carries no monthly series or no creatives for a label,
  do not reference one. In a funnel report the monthly series belong to the
  FUNNELS, so `[[chart: <advertiser>]]` usually has nothing behind it — chart
  the funnel, not the advertiser.
- Landing pages with no funnel name are a bucket, not a funnel: they have no
  label and cannot be charted or shown.

Use the special chart/creative block tokens above only inside the AdSpyLab report
renderer. In ordinary chat or documents, use standard tables and image links.

## Tables

- Live creatives: asset, family, ads launched in window, EU reach gained,
  days since alive, ownership, reason, links.
- Concept families: family, kind, strong candidate, potential winners /
  tested (win rate), alive creatives / share, newest alive cohort, link.
- Funnels: funnel name, landing URL, ads.

## Tone

- Numbers from the answer, not recomputed; percentages only when the tool
  gave them or the base is stated.
- "Observation, not explanation": a change in volume is reported as a change;
  causes are named only as possibilities.
- No accusations of copying; name the four explanations for shared files.

## Brand profiles and saved funnels

For brand_profile, report summary, activity, nested domain–funnel placements,
pages and language sets when present. Keep the pair (domain, funnel_name);
Others is an aggregate tail, not a real advertiser. Include dashboard_url.
For Funnels Library, report the capture date and run_id, ordered steps and
visible offer/pricing. Use returned preview URLs and stable dashboard links.
Do not claim a saved offer is currently live or that ad volume proves conversion.
