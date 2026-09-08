# RQ-002 — Tennis Data and Licensing Audit

- Status: Path A selected; no source or subscription approved
- Last updated: 2026-09-07
- Research question: RQ-002

## Required data

The proposed tennis study needs, for each eligible match:

- stable player identifiers and names;
- tournament, season, round, surface, and match format;
- scheduled match date and, if available, start time;
- winner, loser, score, and match status;
- historical rankings or ranking points available before the match;
- pre-match match-winner bookmaker prices;
- a reproducible closing-price observation;
- timestamp, bookmaker identity, missingness, revisions, and licence terms.

The results/rankings source and the bookmaker-price source may be different,
but their match joins must be independently auditable.

## Candidate source matrix

| Source | Potential use | Coverage and timing | Licensing / cost | Preliminary result |
|---|---|---|---|---|
| [Jeff Sackmann ATP data](https://github.com/JeffSackmann/tennis_atp) | ATP results, rankings, player records, and match statistics | Annual tour-level files cover the proposed 2017–2024 period. The repository includes match result fields, player IDs, surfaces, rounds, and ranking-related fields. It does not provide bookmaker odds or closing timestamps. | CC BY-NC-SA 4.0: attribution required, non-commercial use only, and ShareAlike applies to redistribution. | **Strong free results/rankings candidate; not sufficient for market benchmarking.** |
| [The Odds API tennis coverage](https://the-odds-api.com/sports/tennis-odds.html) | Historical bookmaker match-winner odds and timestamped snapshots | Covers selected Grand Slams and ATP tournaments. Historical tennis coverage begins as early as 2020 for some Grand Slams, but many ATP events begin only in 2024–2026. Historical snapshots are paid; the API returns the closest snapshot at or before a requested timestamp. | Paid historical access. Provider terms permit research and model training but prohibit raw-feed resale or redistribution as a competing data service. | **Potential odds candidate only for a much narrower tournament/period sample; not sufficient for ATP-wide 2017–2024 as currently proposed.** |
| [football-data.org API](https://www.football-data.org/about) | General football fixtures and results | Not a tennis bookmaker or tennis historical-odds source. | API terms and registration requirements; irrelevant to the tennis benchmark. | **Out of scope.** |
| Betfair historical data | Exchange prices and market activity | Could represent an exchange market rather than bookmaker consensus; tennis coverage and target-period availability need separate verification. | Betfair terms restrict website/service data, including historical odds, to personal, non-exclusive, non-sublicensable, non-commercial use unless separately licensed. | **Not approved for the current study.** |

## Findings

### 1. Free match data is available, but free closing odds are not established

Jeff Sackmann’s ATP repository is a strong candidate for historical player and
match data. Its repository lists annual ATP match files through recent seasons
and explicitly states the CC BY-NC-SA 4.0 licence. The licence is important:
the data cannot be treated as unrestricted public-domain material or used
commercially without resolving the rights.

The repository does not supply the bookmaker prices needed to answer RQ-002.
Joining it to an odds source would therefore create a two-source provenance and
licensing problem.

### 2. The documented paid odds source does not match the proposed ATP-wide scope

The Odds API documents match-winner tennis markets and timestamped historical
snapshots. Its tournament table shows highly uneven start dates: some Grand
Slams begin around 2020–2021, while many ATP 1000 and ATP 500 events begin in
2024–2026. This means it cannot be assumed to provide a complete 2017–2024 ATP
sample.

The source may support a deliberately narrow tournament study, such as selected
Grand Slams from 2020 onward, but that would be a different research scope and
would require paid-access approval.

### 3. Match status is a material tennis-specific issue

The source audit must verify how retirements, walkovers, withdrawals, and
abandoned matches are represented. A dataset that records only a winner and
loser can hide whether the match was completed normally. This is not a minor
cleaning detail: it can change the population being evaluated and bias a model
comparison.

## Scope decision required

The proposed ATP-wide 2017–2024 study is **not yet data-feasible** under the
reviewed sources. The smallest defensible choices are:

### Path A — Free results-only research

Use Jeff Sackmann’s data to study player-strength forecasting without claiming
that the model adds information beyond bookmaker closing prices. This would no
longer be the full RQ-002 market-baseline question.

**Selected by Victor on 2026-09-08.** The bounded study is documented in
`research/rq-002-free-results-protocol.md`.

### Path B — Paid, narrow market study

Approve a paid historical-odds evaluation and restrict the sample to tournaments
and seasons with verified odds coverage. This could test a real closing-market
question but would not support the original ATP-wide scope.

### Path C — Defer tennis market testing

Keep RQ-002 proposed and wait for a source with complete, licensed ATP match
winner odds and closing snapshots before building a dataset or model.

Path A is selected. No account, purchase, API key, or dataset acquisition has
been made.

## Reproducibility and licensing gates

Before any data acquisition:

- record the exact upstream commit or immutable source version;
- preserve Sackmann attribution and non-commercial licence requirements;
- verify the odds provider’s tournament-by-tournament historical start dates;
- verify bookmaker regions, match-winner market, snapshot interval, and closing
  convention;
- define the join key and conflict-resolution rules;
- define status exclusions before seeing model results;
- record whether raw data may be retained privately and whether derived results
  may be published.

## Conclusion classification

**Further Study Required.** The free results-only path is selected for learning
and player-strength research. It cannot answer whether a model adds information
beyond bookmaker closing prices, because no closing-odds source is included.
No tennis model, provider, subscription, architecture, deployment, or betting
decision is approved.
