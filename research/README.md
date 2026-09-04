# Edge Research

## Charter

Edge research exists to determine whether football data, probabilistic models, market information, and decision methods can produce a reproducible informational or decision advantage after bookmaker margin, uncertainty, and operational constraints. It does not exist to prove that Edge can beat a bookmaker.

## Principles

- **Falsifiability first:** Every research question must state testable competing hypotheses and conditions that could reject the proposed advantage.
- **Balanced evidence:** Seek and report evidence against Edge's core hypothesis with the same care as supporting evidence.
- **Source quality:** Prefer original data, primary research, and peer-reviewed sources. Preprints and secondary sources may be used only when identified and assessed accordingly.
- **Separate claim types:** Label observations as **Evidence**, **Interpretation**, **Hypothesis**, or **Decision**. One does not automatically imply another.
- **Temporal integrity:** A historical prediction may use only information available at its declared prediction timestamp. Future results, later ratings, unavailable lineups, and later odds are prohibited unless they are explicitly the benchmark being evaluated.
- **Reproducibility:** Record data provenance, extraction dates, transformations, code/configuration versions, random seeds where relevant, evaluation periods, and enough procedure detail for an independent rerun.
- **Explicit uncertainty:** Record sampling uncertainty, model uncertainty, missing data, assumptions, sensitivity, external-validity limits, and unresolved contradictions.
- **Valid conclusions:** A completed question must conclude **Accepted**, **Rejected**, **Inconclusive**, or **Further Study Required**, relative to its stated hypotheses and evidence threshold.
- **Architecture boundary:** Research may discuss or recommend an architecture, model, provider, or tool; none becomes approved until it passes the separate Whiteboard and backlog approval process.

## Research flow

1. Register a falsifiable question in `questions.md`.
2. Agree its scope, hypotheses, evidence plan, and completion criteria before investigation.
3. Register and assess sources in `sources.md`.
4. Conduct leakage-safe analysis and preserve a reproducible record.
5. Synthesize supporting, challenging, and unresolved evidence separately.
6. Review collaboratively and assign one permitted conclusion.
7. Route any proposed decision through the Whiteboard and backlog process.

## Minimal research-note format

```markdown
# RQ-XXX — Title

- Status:
- Conclusion: Accepted | Rejected | Inconclusive | Further Study Required
- Last updated: YYYY-MM-DD

## Question
## Scope and prediction timestamp
## Competing hypotheses
## Method and evidence plan
## Evidence
<!-- Cite Source IDs; distinguish supporting, challenging, and unresolved evidence. -->
## Interpretation
## Uncertainty and limitations
## Conclusion
## Decision implications
<!-- Proposals only; this section does not approve architecture. -->
## Reproduction record
<!-- Data provenance, versions, configuration, seeds, periods, and commands/procedure. -->
```
