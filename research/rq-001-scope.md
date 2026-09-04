# RQ-001 — Scope and Test Plan

- Status: Proposed scope for review
- Conclusion: Further Study Required
- Last updated: 2026-09-04

## Question

Across a pre-specified set of football leagues, seasons, prediction timestamps,
and 1X2 matches, do statistical or probabilistic football models provide
statistically and practically meaningful incremental out-of-sample predictive
information beyond margin-free consensus bookmaker probabilities, using closing
prices as the primary market benchmark, under leakage-free walk-forward
evaluation?

This is a forecasting and information question. It is not, by itself, a claim
that any strategy is profitable or suitable for real-money betting.

## Why this matters

The closing market is a strong public forecast because it combines many models,
opinions, and pieces of information. A model that cannot improve on it may still
be useful for explanation or calibration, but it has not demonstrated an
independent forecasting edge.

## Scope and prediction timestamp

### Primary scope proposal

The primary analysis will cover the English Premier League, German Bundesliga,
and Italian Serie A, for the ten completed seasons from 2014/15 through
2023/24. The unit of analysis is one scheduled match and its mutually exclusive
home-win, draw, and away-win outcomes.

This scope is a proposal, not a claim that suitable data already exist. A league
or season may be excluded only under the pre-specified data-quality or licensing
gates below. Any exclusion will be recorded before final testing.

### Prediction timestamps

Two distinct information sets will be evaluated:

1. **Decision-time forecast:** the latest price and information available at a
   declared capture time before the match. The default proposal is 24 hours
   before scheduled kickoff, with a sensitivity analysis at 72 hours and 1 hour
   where coverage permits.
2. **Closing benchmark:** the final observable market snapshot before kickoff,
   using a documented time window. Closing prices are a later benchmark, not
   information available to the earlier decision-time forecast.

No model or calibration procedure may use match results, future matches,
future-season information, later team ratings, later news, later lineups, or
closing prices when producing a decision-time forecast.

### Market and bookmaker definition

The market is the pre-match 1X2 market. The bookmaker panel, odds fields,
timestamp tolerance, handling of missing values, and definition of “closing”
must be fixed in the data audit before final testing.

The primary consensus will be the equal-weight mean of the available
margin-free bookmaker probabilities after applying the approved de-vigging
method. The analysis will also report bookmaker-count coverage and sensitivity
to alternative consensus rules. No bookmaker will be included solely because it
improves a result.

### Data and licensing gates

Before analysis, every candidate source must have a recorded owner, access and
reuse terms, commercial-use status, redistribution restrictions, attribution
requirements, coverage, missingness, revision behaviour, and collection method.
Data will not be downloaded, purchased, redistributed, or made a project
dependency until its terms are reviewed and Victor approves any paid access.

The primary scope requires adequate coverage for match outcomes, time-stamped
1X2 odds, and the fields needed to reproduce the market consensus. If those
requirements cannot be met, the affected scope is not silently substituted with
a different league, period, or benchmark.

## Competing hypotheses and decision rule

The hypotheses are deliberately classified rather than treated as three
mutually exclusive mathematical null hypotheses:

- **H0 — Market sufficiency:** no tested model provides a repeatable,
  practically meaningful improvement over the closing market, and no tested
  model contributes useful incremental information when combined with it.
- **H1 — General incremental information:** at least one pre-specified model
  improves on the closing market by the required statistical and practical
  thresholds, with evidence that survives the primary stability checks across
  the full scope.
- **H2 — Conditional incremental information:** a model meets the same thresholds
  only within a condition declared before final testing, such as a particular
  league, season block, liquidity proxy, or prediction horizon, without meeting
  the generalization requirement for H1.

The final classification will be one of:

- **Accepted:** H1 or H2 is supported under the registered thresholds and
  sensitivity checks.
- **Rejected:** the registered evidence supports H0 for the tested scope.
- **Inconclusive:** estimates are too uncertain, unstable, or incomplete to
  distinguish the hypotheses.
- **Further Study Required:** the question cannot yet be completed because a
  pre-specified data, licensing, reproducibility, or methodological gate failed.

An apparent positive result that occurs only in an unregistered subgroup,
unregistered model variant, or post-hoc threshold search is exploratory and
cannot support H1 or H2.

## Models and baselines

The primary model set is intentionally small and understandable:

1. A time-updated Elo-style rating model with a fixed, pre-specified update
   rule.
2. A time-updated Poisson score model with home advantage.
3. A Dixon–Coles-style score model, if its implementation and fitting details
   can be reproduced without using future information.
4. A pre-specified logistic regression using only features available at the
   prediction timestamp.

Baselines will include the uniform 1/3–1/3–1/3 forecast, a historical
   outcome-rate forecast fitted only on the training period, and the
   margin-free bookmaker consensus. Model variants and hyperparameters will be
   fixed before final test evaluation or selected inside each training window.

## Margin removal and market construction

At least two defensible de-vigging methods will be specified before final
testing. The primary method will be selected based on an ex ante methodological
rule, not on which method produces the best model result. Sensitivity results
will report how conclusions change under the alternative method.

The exact formulas, treatment of overround, impossible or missing prices,
rounding, bookmaker weights, and consensus aggregation will be recorded in the
reproduction record.

## Evaluation

### Predictive performance

Primary metrics are multiclass log loss and Brier score. In plain language,
log loss strongly penalizes confident wrong forecasts, while Brier score
measures the squared distance between predicted probabilities and what actually
happened.

Secondary diagnostics are calibration, sharpness, accuracy, and ranked
probability score. Calibration asks whether events predicted at, for example,
70% occur about 70% of the time. Sharpness asks whether predictions are
informative rather than all being close to one-third.

All model and market forecasts must be evaluated on identical matches. Results
will include paired differences, uncertainty intervals, calibration plots, and
season- and competition-level stability summaries.

### Incremental-information test

The primary incremental test will be a pre-specified logarithmic forecast pool
combining the market forecast with each model forecast. The model’s weight will
be fitted using training data only and evaluated on the next walk-forward period.
The key question is whether the combined forecast improves the market forecast
out of sample, not whether the model beats a uniform baseline.

A supplementary encompassing or forecast-regression test may be used if its
assumptions, fitting window, uncertainty calculation, and interpretation are
specified before final evaluation.

### Practical thresholds

Before final testing, the project must fix numerical thresholds for:

- minimum improvement in primary scoring metrics;
- uncertainty interval requirements;
- minimum number of test matches per subgroup;
- minimum number of seasons or competitions showing the effect;
- maximum tolerated degradation in other primary subgroups.

Until these thresholds are approved, no result may be described as practically
meaningful.

### Economic evidence

ROI, drawdown, attainable price, and closing-line value may be reported only as
secondary evidence. Economic tests must use time-matched prices, a fixed
selection rule, realistic price availability, stake constraints, and documented
market limits. They cannot override weak predictive or incremental-information
evidence.

## Walk-forward and leakage controls

Testing proceeds through historical time in order. Each forecast is generated
from information available at its timestamp, the result is recorded, and only
then does the calendar move forward. This is like travelling through the
historical calendar without opening tomorrow’s newspaper.

Required controls include:

- fitting ratings, models, calibration, de-vig parameters, and combination
  weights using past data only;
- preventing future matches from entering rolling features or team states;
- separating decision-time forecasts from closing-market benchmarks;
- recording the exact data version or retrieval date used for each forecast;
- preserving failed, missing, and excluded observations rather than silently
  dropping them;
- running an auditable leakage check before interpreting results.

## Multiple comparisons and exploratory work

The primary model set, primary metric, benchmark, scope, and stability rules
must be frozen before final test results are inspected. Additional leagues,
markets, thresholds, model variants, and subgroups are secondary or exploratory
unless explicitly registered beforehand. The report will disclose the number of
comparisons and distinguish confirmation from discovery.

## Evidence plan

The literature review will include evidence supporting, challenging, and
qualifying the hypotheses. Historical evidence that a model was profitable
against published odds does not by itself demonstrate incremental information
beyond a comparable modern closing market.

Seed sources will be fully appraised before their claims are used. Publisher
records, original papers, institutional copies, original datasets, and code
repositories will be preferred. Peer review will be recorded as a quality
factor, not treated as proof.

## Limitations

The proposed scope may not generalize to other leagues, sports, markets,
bookmakers, currencies, prediction horizons, or future market regimes. Closing
prices may be unavailable, revised, rounded, or assembled from sources with
different timestamps. A negative result would mean that no tested model showed
incremental information under this design; it would not prove that no possible
model or information source could ever add value.

## Reproduction record

To be completed before analysis:

- data owners, URLs, terms, and access dates;
- raw-file checksums or immutable data identifiers where permitted;
- extraction method and timestamp conventions;
- transformations and de-vig formulas;
- model equations and configuration;
- training and test periods;
- software and dependency versions;
- random seeds where relevant;
- commands or procedure for an independent rerun;
- leakage-check results and exclusions.

## Decision implications

The result may inform whether later Edge research should use the closing market
as a minimum benchmark, focus on narrower conditions, or treat independent
models primarily as calibration or diagnostic tools.

This document does not approve a model, architecture, provider, database,
dashboard, deployment, paid subscription, or real-money betting decision.
