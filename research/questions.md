# Research Question Registry

This registry tracks questions before, during, and after investigation. A proposed question is not approval to implement a model or architecture.

## RQ-001 — Market Efficiency / Bookmaker Baseline

**Status:** Proposed

### Question

Across a pre-specified set of football leagues, seasons, prediction timestamps, and 1X2 matches, do statistical or probabilistic football models provide statistically and practically meaningful incremental out-of-sample predictive information beyond margin-free consensus bookmaker probabilities, using closing prices as the primary market benchmark, under leakage-free walk-forward evaluation?

### Why it matters

Closing prices aggregate models, information, and market participation into a strong observable forecast. Before Edge investigates whether prices can be beaten, it must establish the difficulty of this baseline and whether independent models add information that the market has not already absorbed. Evidence that the market dominates is as valuable as evidence of model advantage.

### Competing hypotheses

- **H0 — Market sufficiency:** No tested model provides a repeatable, practically meaningful improvement over closing market probabilities, and no tested model contributes useful incremental information when combined with them.
- **H1 — General incremental model information:** At least one pre-specified model delivers a repeatable, statistically and practically meaningful out-of-sample improvement over closing market probabilities, with stability across the full primary scope.
- **H2 — Conditional incremental information:** Incremental information meets the same thresholds only within a condition declared before final testing and does not generalize across the full primary scope.

H1 and H2 are classification outcomes rather than mutually exclusive null
hypotheses: H2 is the conditional result when the registered effect does not
meet H1's generalization requirement. The scope, numerical thresholds, primary
tests, subgroup rules, and decision mapping are recorded in
`research/rq-001-scope.md` before final testing.

### Evidence required

- A pre-registered scope: competitions, seasons, 1X2 market, prediction timestamps, bookmakers, consensus method, closing-price definition, models, metrics, and material-effect thresholds.
- Time-stamped match, feature, and odds data with documented provenance, coverage, missingness, and licensing.
- Margin-free probabilities derived using multiple defensible de-vigging methods, with sensitivity analysis.
- Strong, independently generated baselines, including simple dynamic rating and score-based structural models, evaluated on the same matches as the market.
- Strict walk-forward or otherwise temporal out-of-sample evaluation with auditable leakage checks.
- Proper scoring rules, calibration and sharpness analysis, paired uncertainty intervals or tests, and stability checks by season and competition.
- A direct incremental-information test, such as a pre-specified forecast-combination or encompassing analysis, rather than accuracy alone.
- A declared primary model set, primary metric, practical-effect threshold,
  multiple-comparison policy, and rule distinguishing general from conditional
  evidence.
- Economic evaluation only as secondary evidence, using attainable time-matched prices, margin, realistic availability, and pre-specified selection rules; ROI alone is insufficient.
- Evidence from both peer-reviewed literature and reproducible modern studies that support, challenge, or qualify each hypothesis.

### Decision(s) it informs

- Whether Edge should treat a margin-free closing market as the minimum forecasting benchmark.
- Whether independent statistical modelling is justified as a source of incremental predictive information, a calibration tool, a diagnostic tool, or not justified for the tested scope.
- Whether later research should focus on broad forecasting, narrower leagues/markets/timestamps, market movement, contextual information, or a non-betting decision-support use.
- What evidence threshold future model research must meet before implementation is proposed.

### Completion criteria

RQ-001 is complete when:

1. Its scope, models, evaluation metrics, and practical-effect thresholds were fixed before final testing.
2. Comparable model and margin-free market forecasts were evaluated on the same leakage-free out-of-sample observations.
3. Predictive performance, calibration, incremental information, uncertainty, temporal/competition stability, and key sensitivity analyses were reported.
4. Supporting and challenging literature was assessed without excluding adverse findings.
5. Data limitations, licensing constraints, and reproducibility status were recorded.
6. The evidence supports one permitted conclusion—Accepted, Rejected, Inconclusive, or Further Study Required—without implying automatic architecture approval.
