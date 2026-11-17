# Build Test Lab — raw run data

Every published run of [buildtestlab.com](https://buildtestlab.com): 47 runs,
22 tools, 8 briefs, 381 criteria passed. Updated 2026-11-17.

These are not opinions about builders. Each run is one prompt, one brief, one published page, scored
against a fixed list of binary criteria on a free plan. When a criterion could not be checked, it is
`null` — never guessed, never filled in afterwards.

## Files

| File | What it is |
|---|---|
| `runs.json` | Every run as one JSON array: criteria, reasons for failures, timings, prices, metrics |
| `runs.csv` | The same flattened, one column per metric, `criteria` as `A1=1 A2=0 A3=na` |
| `runs/<run-id>.json` | The original file per run, exactly as it is committed in the site repository |
| `tools/<slug>.json` | Pricing, capabilities and limits per tool, with the date each was checked |

## Fields

- `score`: `passed` / `measured` / `total`. `total` is every criterion on the brief; `measured` is what
  the run could actually check. The score is always `passed` of `measured` — an unmeasurable criterion
  never counts as a pass.
- `criteria`: `pass`, `fail` or `unmeasured` per criterion key.
- `reasons`: why a criterion failed, in the words of the run.
- `minutes_to_deploy`: wall-clock from the first prompt to a public URL.
- `cost_usd`: money spent. Always 0 — no run was made on a paid plan.
- `pricing`: the vendor's own page, with the date it was read.
- `metrics`: Lighthouse and axe numbers where they were taken; `null` where they were not.

## Briefs

`booking-app-v1`, `landing-page-v1`, `portfolio-v1`, `artist-site-v1`, `musician-site-v1`,
`nonprofit-site-v1`, `restaurant-site-v1`, `dashboard-v1`. Criteria per brief are documented at
<https://buildtestlab.com/methodology>.

## Licence

CC BY 4.0 — https://creativecommons.org/licenses/by/4.0/

Use it, chart it, quote it, teach with it. Name the source and the date.

## Citation

> Build Test Lab (2026). *AI website builders tested on free plans.*
> https://buildtestlab.com/data — retrieved 2026-11-17.

## What this data does not show

Paid plans, support quality, long-term reliability, or the business behind each vendor. We test a free
plan and a published page, nothing else. Attempts that died at a signup, a captcha or a paywall are not
rows — they are named with their reason at <https://buildtestlab.com/state-2026>.
