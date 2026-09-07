# RQ-002 — Tennis Market Baseline Scope and Test Plan

- Status: Proposed scope for review
- Conclusion: Further Study Required
- Last updated: 2026-09-07

## Question

Across a pre-specified set of ATP Tour-level men's singles matches, seasons,
surfaces, prediction timestamps, and pre-match match-winner markets, do
statistical or probabilistic tennis models provide statistically and practically
meaningful incremental out-of-sample predictive information beyond margin-free
consensus bookmaker probabilities, using closing prices as the primary market
benchmark under leakage-free walk-forward evaluation?

This is a forecasting and market-information question. It is not a claim that
Edge can make money or that any future match should be bet.

## What changes from the football work

The football research remains preserved as RQ-001. This tennis question is a
separate study because tennis outcomes, data fields, markets, and failure modes
are different.

- Football 1X2 becomes tennis match winner: player A or player B.
- Team ratings become player-strength and matchup features.
- Home advantage becomes surface, tournament, court, travel, and scheduling
  context where data are available.
- Draw handling disappears, but retirements, walkovers, withdrawals, and
  abandoned matches require explicit rules.
- Match format must be recorded; a best-of-five match cannot be silently mixed
  with best-of-three evidence.

## Primary scope proposal

The first study will propose:

- ATP Tour-level men's singles;
- completed seasons 2017 through 2024;
- regular ATP Tour tournaments and ATP Finals;
- best-of-three matches only;
- hard, clay, and grass surfaces recorded separately;
- pre-match match-winner market only;
- no doubles, Challenger, ITF, Davis Cup, junior, exhibition, or qualifying
  matches in the primary sample.

This is a proposal pending data and licensing verification. The final scope
must be fixed before final test results are inspected. If the source cannot
reliably identify tournament tier, surface, match format, and match status, the
affected observations will be excluded and recorded rather than silently
relabelled.

## Match-status rules

The primary outcome sample will include matches completed with a valid winner
and loser. The primary sample will exclude:

- walkovers before play;
- withdrawals before play;
- retirements during play;
- abandoned or suspended matches without a final competitive result;
- duplicate or conflicting records.

Retirements and other excluded statuses may be analysed separately as a
diagnostic because excluding them can create a different selection problem. They
must not be folded into ordinary wins or losses without a pre-specified rule.

## Prediction timestamps and benchmark

The primary benchmark is the margin-free closing match-winner market. A future
time-matched decision study may use 72-hour, 24-hour, and 1-hour snapshots, but
those timestamps are not part of this first protocol until a source proves that
the historical observations exist.

Closing prices are a later benchmark. They cannot be used as inputs to an
earlier prediction. If an early-price study is later approved, it must be kept
separate from the closing comparison.

## Competing hypotheses

- **H0 — Market sufficiency:** No tested model provides a repeatable,
  practically meaningful improvement over the closing market, and no tested
  model adds useful information when combined with it.
- **H1 — General incremental information:** At least one pre-specified model
  improves on the closing market by the registered thresholds and remains
  stable across the primary scope.
- **H2 — Conditional incremental information:** A model meets the thresholds only
  within a condition declared before final testing, such as surface or
  tournament tier, without meeting the generalization requirement for H1.

H1 and H2 are classification outcomes, not mutually exclusive mathematical
null hypotheses. A positive unregistered subgroup is exploratory and cannot
support H1 or H2.

## Candidate model families

The first model set should remain small and understandable:

1. Uniform 50%–50% forecast.
2. Historical player-win-rate forecast fitted only on past matches.
3. Elo-style player ratings with surface-specific and overall variants fixed
   before final testing.
4. A Bradley–Terry-style paired-comparison model, if player and match data can
   support it without future leakage.
5. A logistic model using pre-specified player, surface, rest, and ranking
   features available at the declared prediction timestamp.

These are candidate families, not implementation approval. Neural networks,
large language models, and complex ensembles are out of scope for the first
study.

## Market construction

The market benchmark will be built from bookmaker match-winner prices after
removing bookmaker margin. The protocol must define:

- bookmaker panel and regional coverage;
- closing timestamp and tolerance;
- treatment of missing prices;
- minimum number of complete bookmaker prices;
- primary and sensitivity de-vigging methods;
- consensus aggregation and normalization;
- handling of odds revisions or duplicate snapshots.

No construction method may be selected because it gives the best model result.

## Evaluation

The primary metrics are binary log loss and Brier score. Log loss heavily
penalizes confident wrong predictions. Brier score measures the squared distance
between predicted probability and the outcome that occurred.

Secondary diagnostics are calibration, sharpness, accuracy, discrimination,
paired uncertainty intervals, and stability by season, surface, tournament
tier, and player-ranking band.

The primary incremental test will combine each model with the market forecast in
a pre-specified logarithmic forecast pool. Combination weights must be fitted
using training data only, then evaluated on the next walk-forward period.

## Practical thresholds for review

Before final testing, the project must approve numerical thresholds. Initial
proposals are:

- at least 0.005 lower mean log loss for the combined forecast versus the market
  alone;
- at least 0.002 lower mean Brier score as confirmation;
- a paired 95% uncertainty interval for the primary difference excluding zero;
- the effect must not be driven by one season or one tournament tier;
- at least 2,000 eligible out-of-sample matches for the pooled primary result;
- no declared subgroup interpreted with fewer than 500 eligible matches;
- ROI and closing-line value, if later analysed, remain secondary evidence.

## Leakage controls

- Player ratings, rolling form, surface records, rest, rankings, and calibration
  use only information available before the prediction timestamp.
- Rankings must be captured as historical values, not current rankings applied
  retrospectively.
- Future match results, later tournament rounds, later injuries, and later
  withdrawals are prohibited from earlier features.
- Match-status exclusions are determined using an auditable result record, not
  an outcome-based convenience rule.
- Model selection, feature choices, de-vigging, and forecast-combination
  weights are fixed before the final test or selected inside training windows.

## Data and licensing gate

Before acquisition, candidate sources must be audited for:

- match outcomes and statuses;
- player identities and stable identifiers;
- tournament, season, surface, and match format;
- historical rankings and player-level features;
- bookmaker match-winner prices and closing timestamps;
- missingness, revisions, and coverage;
- owner, licence, attribution, commercial-use, and redistribution terms.

No paid account or data purchase is approved by this document.

## Completion boundary

RQ-002 is complete only when the scope, data source, models, metrics,
thresholds, leakage checks, sensitivity analyses, and uncertainty reporting are
fixed before final evaluation and one permitted conclusion is assigned.

A positive result would show only that a tested model added information to the
closing market under this tennis design. It would not prove persistent
profitability or justify real-money betting.

A negative result would show only that the tested models did not add information
under this design. It would not prove that tennis markets can never be improved
upon.

This protocol does not approve a data provider, architecture, implementation,
deployment, paid subscription, or betting decision.

