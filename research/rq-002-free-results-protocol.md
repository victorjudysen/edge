# RQ-002 — Free Results-Only Tennis Study Protocol

- Status: Selected bounded study; no market-edge claim
- Last updated: 2026-09-08
- Parent question: RQ-002
- Data candidate: Jeff Sackmann’s ATP results and rankings, subject to its
  CC BY-NC-SA 4.0 terms

## Purpose

This is the first practical tennis study for Edge. It has two goals:

1. help Victor understand how tennis performance and uncertainty behave; and
2. test whether simple player-strength forecasts are calibrated against actual
   match outcomes.

It does **not** test whether a model beats bookmaker prices. No bookmaker odds,
closing market, bet selection, stake, or real-money decision is part of this
study.

## Scope

- ATP Tour-level men’s singles;
- seasons 2017–2024, subject to verified file coverage;
- best-of-three matches only;
- regular ATP Tour events and ATP Finals;
- hard, clay, and grass surfaces recorded separately;
- no doubles, Challenger, ITF, Davis Cup, junior, exhibition, or qualifying
  matches in the primary sample;
- completed matches with a valid winner and loser;
- walkovers, pre-match withdrawals, retirements, abandoned matches, duplicates,
  and conflicting records excluded from the primary sample.

The final inclusion table must record every excluded category and count.

## Bounded research question

Across the verified ATP sample, can simple player-strength models produce
well-calibrated out-of-sample probabilities for the winner of a completed tennis
match, and are those probabilities stable across seasons and surfaces?

This is narrower than RQ-002. A result here cannot be described as evidence of
market inefficiency or betting profitability.

## Forecasts to compare

1. **Uniform baseline:** 50% for each player.
2. **Historical player rate:** each player’s past eligible match-win rate,
   calculated using only matches before the forecast date.
3. **Overall Elo-style rating:** a simple sequential rating updated only after a
   match is completed.
4. **Surface-specific Elo-style rating:** a separate or partially pooled rating
   for hard, clay, and grass.
5. **Bradley–Terry-style model:** optional, only if player identifiers and
   fitting procedure remain auditable and leakage-safe.

Model 5 is not required for the first run. The first useful comparison is often
between a transparent rating model and the uniform baseline.

## Walk-forward evaluation

The historical calendar is travelled in order, like watching seasons unfold
without opening tomorrow’s newspaper:

- build the forecast using only earlier eligible matches;
- record the forecast before the next match outcome is used;
- update the rating or training data after the match;
- move forward to the next match.

Current rankings must not be copied backward into older matches. The study must
record whether a ranking field is genuinely available before the match or merely
attached retrospectively to a historical row.

## Evaluation

Primary metrics:

- binary log loss, which heavily penalizes confident wrong predictions;
- Brier score, which measures the squared distance between a probability and the
  result that occurred.

Secondary reporting:

- calibration by probability bin;
- sharpness, meaning whether forecasts vary informatively rather than clustering
  near 50%;
- accuracy as a descriptive metric only;
- stability by season, surface, tournament tier, and player-ranking band;
- uncertainty intervals for pooled and subgroup results.

No result will be called a betting edge because there are no prices in this
study.

## Tennis-specific checks

The study must separately report:

- surface distribution;
- match format and tournament tier;
- retirements and walkovers excluded from the primary sample;
- player debut or sparse-history cases;
- duplicated or changed player names and identifier joins;
- matches where ranking or player information is missing;
- whether COVID-era scheduling or unusual tournament conditions alter coverage.

## Data and licence rules

Jeff Sackmann’s data requires attribution and is licensed for non-commercial use
with ShareAlike obligations. The raw dataset must not be committed to this
repository unless the exact permitted handling is confirmed. Any published
analysis must preserve attribution and the applicable licence terms.

The source commit, retrieval date, file list, transformations, exclusions, and
software versions must be recorded before results are interpreted.

## Learning output

Each study period should produce a short plain-language review:

- what the model believed;
- where it was confidently wrong;
- whether calibration improved or worsened;
- how surface and player history changed the forecast;
- what the data could not tell us;
- why this does or does not justify later market research.

The output should teach the sport and the uncertainty, not advertise a winning
strategy.

## Boundary

This protocol does not approve bookmaker accounts, paid data, market forecasts,
real-money bets, staking, or a production model. A later market study would need
its own licensed odds source, research question, audit, and approval gate.

