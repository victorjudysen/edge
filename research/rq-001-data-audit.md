# RQ-001 — Data and Licensing Audit

- Status: Path A selected for further review; no source approved for acquisition or final testing
- Last updated: 2026-09-07
- Research question: RQ-001

## Purpose

This audit checks whether candidate public sources can support the registered
RQ-001 design. It is a source and licensing review, not a model result. No
dataset was downloaded, purchased, committed, or made a project dependency.

## Required data

The primary design needs, for the English Premier League, German Bundesliga,
and Italian Serie A across the proposed 2014/15–2023/24 period:

- final match outcome and scheduled kickoff time;
- time-stamped 1X2 bookmaker prices;
- enough bookmaker coverage to construct a reproducible consensus;
- a closing-price observation;
- observations near the declared 72-hour, 24-hour, and 1-hour decision times,
  where available;
- stable identifiers allowing matches to be joined without ambiguous team-name
  matching;
- provenance, revisions, missingness, and licensing information.

The crucial distinction is between a price observed at a known time and a price
described only as “pre-closing.” The latter cannot automatically be used as a
24-hour or 1-hour decision-time price.

## Candidate source matrix

| Source | Potential use | Coverage and timing evidence | Licensing / reuse status | Preliminary result |
|---|---|---|---|---|
| [Football-Data.co.uk historical data](https://www.football-data.co.uk/data) | Match results, match statistics, bookmaker odds, average/max prices, and closing prices | The publisher reports coverage for the three target leagues and historical odds from multiple bookmakers. It reports two odds sets from 2019/20 onward: an opening-period collection at times specified on its fixtures page and a closing collection. Earlier seasons have only pre-closing odds. | The site describes the files as free and provides a disclaimer, but the pages reviewed do not by themselves establish a broad commercial redistribution licence for the underlying third-party odds sources. Attribution, redistribution, and derived-data publication terms require direct confirmation. | **Conditional candidate.** Strongest public starting point for results and closing odds, but it does not yet pass the exact decision-time timestamp gate. |
| [Football-Data fixture notes](https://www.football-data.co.uk/matches/resources/notes.txt) | Interpretation of current/pre-match collection timing | The publisher documents Friday-afternoon collection for weekend fixtures and Tuesday collection for midweek fixtures. This describes the collection schedule, not necessarily historical 72-hour, 24-hour, or 1-hour observations for every match. | Same unresolved licensing question as above. | **Insufficient alone** for time-matched historical decision prices. |
| [StatsBomb Open Data](https://github.com/hudl/open-data) | Event data, lineups, and selected match-level features for supplementary model research | The repository provides JSON match, event, lineup, and selected 360 data for certain competitions and seasons. It does not provide the bookmaker odds needed for the RQ-001 market benchmark. | Public research use is encouraged; published or distributed work must credit StatsBomb and use its logo. The repository’s licence and source-specific conditions must be preserved before reuse. | **Supplementary candidate only.** Not a standalone RQ-001 source and likely incomplete for the full target scope. |
| Understat xG | Possible supplementary expected-goals feature | The seeded literature identifies Understat as an xG source, but this audit did not establish a stable official bulk-data access method, historical snapshot policy, or timestamped availability suitable for leakage-safe reconstruction. | Terms and redistribution rights remain unresolved. | **Not approved.** Do not scrape, download, or depend on it without a licensing and access review. |

## Findings

### 0. Sample inspection status

On 2026-09-07, a permitted 8 KB request was attempted against the public
2023/24 Premier League CSV endpoint to verify the header and a few rows without
retrieving the full file. The host returned a temporary-unavailable HTML page
instead of CSV content. The same endpoint could not be inspected through the
browser fetcher. This means the audit has **not** verified the actual column
names, row shape, or closing-column values from a file sample. No claim about
those details is being made from this failed request.

### 1. Football-Data is useful but does not yet satisfy the full design

Football-Data reports the right broad leagues and period coverage, multiple
bookmaker odds, and closing odds. It also reports that its historical files
contain two odds sets from 2019/20 onward, while earlier seasons contain only
pre-closing odds. This makes it a plausible source for a closing-market
benchmark and a possible pre-closing comparison.

However, the published description does not prove that every historical match
has an observation at 72 hours, 24 hours, and 1 hour before kickoff. The
documented opening-period collection schedule varies by fixture and is not the
same thing as a fixed decision timestamp. Therefore the current RQ-001 plan
cannot claim to test those horizons using this source without further evidence.

The site also warns that Pinnacle data delivery became unreliable after July
2025. That warning is outside the proposed test period, but it reinforces the
need to record source vintages, bookmaker identity, and data-quality checks
rather than treating a provider label as proof of accuracy.

### 2. Closing odds and decision-time odds must remain separate

Football-Data can potentially support a closing benchmark. It may not support a
historically faithful earlier decision process. If no source supplies the
required time-matched observations, the honest choices are:

- narrow the registered question to the timestamps the source actually records;
- obtain a separately licensed historical time-series source with explicit
  timestamps; or
- stop the economic/time-of-decision part of RQ-001 and retain only a closing
  benchmark study.

The project must not label a generic pre-closing column as a 24-hour price.

### 3. Free access does not settle reuse rights

A website saying that files are free to download is not the same as granting
permission to redistribute the raw data, publish a derived dataset, or use it
commercially. The audit therefore treats Football-Data as usable for review
and possible private research only after the relevant terms are confirmed.

StatsBomb is clearer for research attribution, but its open data cannot supply
the market benchmark and should not be treated as permission to redistribute
all derived or joined datasets without checking the licence.

### 4. No candidate currently passes the complete gate

At this stage, no candidate source has demonstrated all of the following at
once:

- complete target-league coverage;
- exact time-matched decision prices;
- closing prices;
- reproducible bookmaker consensus;
- clear reuse terms for the intended analysis and publication.

This is a data-design limitation, not evidence for or against market
efficiency.

## Recommended scope decision

Do not acquire data or begin modelling yet. First choose one of these registered
paths:

### Path A — Closing-market benchmark first

Use Football-Data only for a narrow closing-benchmark study, subject to a
read-only sample inspection and written confirmation of permitted use. Remove
the claim that it evaluates 72-hour, 24-hour, or 1-hour decision prices.

### Path B — Time-matched decision study

Find a licensed historical odds source with explicit timestamps and sufficient
bookmaker coverage. This may require paid access and therefore Victor’s explicit
approval before any account, purchase, or download.

### Path C — Stop RQ-001 temporarily

If neither source path is acceptable, record the data gate as failed and do not
force a model comparison using retrospective or poorly timed odds.

Path A is now the selected low-cost next step, subject to the unresolved source
and licensing checks above. It would answer a narrower question:
whether simple models add information beyond a reproducibly constructed closing
market, not whether they improve an earlier betting decision.

## Practical-threshold proposal for review

No threshold is final until the data path is selected. For the closing-benchmark
study, the following conservative proposal should be reviewed before testing:

- primary comparison: out-of-sample multiclass log loss;
- confirmation metric: multiclass Brier score;
- practical effect: at least 0.005 lower mean log loss and 0.002 lower mean
  Brier score for the combined market-plus-model forecast versus the market
  alone;
- statistical support: a paired 95% uncertainty interval for the primary
  difference that excludes zero;
- stability: the effect must not be driven by one season, and must appear in at
  least two of the three leagues if all three pass the data gate;
- minimum subgroup size: no league or declared condition is interpreted with
  fewer than 500 out-of-sample matches;
- economic metrics: secondary only and not capable of overriding the predictive
  criteria.

These values are decision criteria proposals, not observed results or evidence
that the effects are achievable.

## Reproducibility checklist before acquisition

- Preserve the exact source URLs and access date.
- Record the source’s published notes and terms as evidence, without copying
  unlicensed bulk data into the repository.
- Inspect only a small, permitted sample to confirm column names, league codes,
  date fields, closing columns, and bookmaker coverage.
- Record the file version, retrieval timestamp, and checksum if acquisition is
  approved.
- Define the match-join key and treatment of postponed or rescheduled matches.
- Define the de-vigging method before looking at model results.
- Record every excluded season, league, bookmaker, and match with a reason.

## Conclusion classification

**Further Study Required.** Path A has been selected for further review, but the
source audit has not established a complete, legally reusable, time-matched
dataset for the original RQ-001 design, and the file-level sample inspection
was unavailable because the source endpoint returned a temporary-unavailable
page. No model, provider, architecture, paid subscription, or betting decision
is approved.
