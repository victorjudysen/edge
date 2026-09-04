# Source and Quality Registry

Sources are registered before their claims are relied upon. Inclusion records relevance; it does not endorse a paper's methods or conclusions.

## Required fields

- **Source ID**
- **Title**
- **Authors**
- **Year**
- **Publication / Publisher**
- **Source Type**
- **DOI**
- **URL**
- **Accessed**
- **Research Question(s)**
- **Evidence Direction:** Supports, Challenges, Mixed, Contextual, or Not Yet Assessed
- **Relevance**
- **Quality / Limitations**
- **Data / Licensing Notes**

For RQ-001, **Supports** means evidence favouring incremental model information (H1 or H2), while **Challenges** means evidence favouring market sufficiency (H0). **Mixed** records material evidence in both directions, **Contextual** informs the method without directly testing the hypotheses, and **Not Yet Assessed** means no direction has been assigned. Direction is provisional until the source has been fully appraised in a research note.

## Seeded sources

### SRC-001

- **Title:** Modelling Association Football Scores and Inefficiencies in the Football Betting Market
- **Authors:** Mark J. Dixon; Stuart G. Coles
- **Year:** 1997
- **Publication / Publisher:** *Journal of the Royal Statistical Society: Series C (Applied Statistics)*, 46(2), 265–280; Royal Statistical Society
- **Source Type:** Peer-reviewed journal article
- **DOI:** [10.1111/1467-9876.00065](https://doi.org/10.1111/1467-9876.00065)
- **URL:** https://academic.oup.com/jrsssc/article-abstract/46/2/265/6990546
- **Accessed:** 2026-08-27
- **Verification note:** Bibliographic record verified against Oxford Academic on 2026-09-04. The platform displays the 1997 issue and a separate article-history publication date; these should not be conflated.
- **Research Question(s):** RQ-001
- **Evidence Direction:** Contextual
- **Relevance:** Establishes the dynamic Poisson-based Dixon–Coles score model and reports a betting-market application, making it a foundational structural-model baseline and historical efficiency claim.
- **Quality / Limitations:** Peer-reviewed and foundational, but based on English match data from the 1990s and bookmaker odds from 1995–96. Its reported returns do not establish persistence in modern, faster, more competitive markets.
- **Data / Licensing Notes:** Publisher access and copyright restrictions apply. Underlying match and odds data licensing and present availability require separate verification before reproduction.

### SRC-002

- **Title:** pi-football: A Bayesian Network Model for Forecasting Association Football Match Outcomes
- **Authors:** Anthony C. Constantinou; Norman E. Fenton; Martin Neil
- **Year:** 2012
- **Publication / Publisher:** *Knowledge-Based Systems*, 36, 322–339; Elsevier
- **Source Type:** Peer-reviewed journal article
- **DOI:** [10.1016/j.knosys.2012.07.008](https://doi.org/10.1016/j.knosys.2012.07.008)
- **URL:** https://www.sciencedirect.com/science/article/pii/S0950705112001967
- **Accessed:** 2026-08-27
- **Verification note:** Bibliographic record verified against ScienceDirect on 2026-09-04.
- **Research Question(s):** RQ-001
- **Evidence Direction:** Contextual
- **Relevance:** Provides a Bayesian-network approach that combines objective and subjective variables and evaluates English Premier League outcome forecasts; it is relevant as a candidate model family, not proof of incremental information beyond closing prices.
- **Quality / Limitations:** Peer-reviewed, but the study concerns one league and an older period. A full appraisal must check forecast timing, market benchmark construction, evaluation design, and reproducibility before using its results in RQ-001.
- **Data / Licensing Notes:** Publisher copyright applies. An accepted manuscript is available through Queen Mary University of London; underlying data rights and reuse conditions require verification.

### SRC-003

- **Title:** Determining the Level of Ability of Football Teams by Dynamic Ratings Based on the Relative Discrepancies in Scores Between Adversaries
- **Authors:** Anthony C. Constantinou; Norman E. Fenton
- **Year:** 2013
- **Publication / Publisher:** *Journal of Quantitative Analysis in Sports*, 9(1), 37–50; De Gruyter
- **Source Type:** Peer-reviewed journal article
- **DOI:** [10.1515/jqas-2012-0036](https://doi.org/10.1515/jqas-2012-0036)
- **URL:** https://doi.org/10.1515/jqas-2012-0036
- **Accessed:** 2026-08-27
- **Verification note:** Bibliographic record verified against De Gruyter Brill on 2026-09-04.
- **Research Question(s):** RQ-001
- **Evidence Direction:** Contextual
- **Relevance:** Introduces dynamic pi-ratings, compares them with football Elo variants, and reports a betting strategy against published odds; it is relevant as a simple dynamic-strength baseline.
- **Quality / Limitations:** Peer-reviewed, but its profitability evidence covers five English Premier League seasons ending in 2011–12. RQ-001 must independently test modern closing prices, temporal validity, selection rules, and uncertainty rather than inherit the reported result.
- **Data / Licensing Notes:** A pre-publication manuscript is publicly available from the authors/institutional channels; the version of record is publisher-controlled. Underlying odds and match data licensing requires verification.

### SRC-004

- **Title:** Can Simple Models Predict Football—and Beat the Odds? Lessons from the German Bundesliga
- **Authors:** Sascha Wilkens
- **Year:** 2026
- **Publication / Publisher:** *Journal of Sports Analytics*, 12; SAGE Publications
- **Source Type:** Peer-reviewed journal article
- **DOI:** [10.1177/22150218261416681](https://doi.org/10.1177/22150218261416681)
- **URL:** https://journals.sagepub.com/doi/10.1177/22150218261416681
- **Accessed:** 2026-08-27
- **Verification note:** Bibliographic record and open-access status verified against SAGE Journals on 2026-09-04.
- **Research Question(s):** RQ-001
- **Evidence Direction:** Mixed
- **Relevance:** Compares a calibrated xG/Skellam model with margin-free closing odds over eleven Bundesliga seasons and reports both market forecasting advantages and conditional simulated betting profits.
- **Quality / Limitations:** Peer-reviewed, modern, temporally evaluated, and directly relevant. Results are limited to one league and one modelling/data setup; profitability varies by season and bet type, and apparently conflicting score summaries require careful methodological appraisal before interpretation.
- **Data / Licensing Notes:** Article is CC BY-NC 4.0 and includes a data-availability statement. Match xG comes from Understat and closing odds from football-data.co.uk; their separate terms govern reuse and redistribution.

### SRC-005

- **Title:** Does a Structural Model Add Anything to the Closing Price? Calibrated Forecasting, Incremental Information, and Match Leverage in the Italian Serie A
- **Authors:** Yannik Pitcan
- **Year:** 2026
- **Publication / Publisher:** arXiv, arXiv:2608.11505
- **Source Type:** Preprint; not peer-reviewed
- **DOI:** [10.48550/arXiv.2608.11505](https://doi.org/10.48550/arXiv.2608.11505)
- **URL:** https://arxiv.org/abs/2608.11505
- **Accessed:** 2026-08-27
- **Verification note:** arXiv record and date verified on 2026-09-04. Peer review, code provenance, and upstream data terms remain to be independently assessed.
- **Research Question(s):** RQ-001
- **Evidence Direction:** Challenges
- **Relevance:** Directly tests whether Dixon–Coles and shots-based structural forecasts add information to margin-free closing prices using proper scores and logarithmic forecast pooling across nineteen Serie A seasons.
- **Quality / Limitations:** Highly aligned with RQ-001 and accompanied by a code/data pipeline, but it is a very recent, single-author, non-peer-reviewed preprint limited to Serie A and specified structural signals. Its findings require independent reproduction and do not establish efficiency in every league, market, or earlier prediction horizon.
- **Data / Licensing Notes:** The arXiv record links a code and data pipeline. Repository licenses and all upstream match, shots, and odds data terms must be reviewed before reuse or redistribution.
