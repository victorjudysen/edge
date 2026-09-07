# RQ-001 — Football-Data Source Verification

- Status: Verification incomplete; closing-benchmark acquisition not yet approved
- Last updated: 2026-09-07
- Research question: RQ-001
- Related audit: `research/rq-001-data-audit.md`

## Objective

Verify whether Football-Data.co.uk can support the narrowed closing-market
benchmark path without treating undocumented timing or licensing assumptions as
facts.

## Evidence reviewed

### Publisher documentation

The publisher’s historical-data page states that CSV and Excel files are
available for multiple European leagues, including England, Germany, and Italy,
and that closing odds are identified by a `C` in the data column headings. The
download page lists a 2023/24 season file set. The fixture notes describe
current collection schedules, but do not establish a fixed historical
72-hour, 24-hour, or 1-hour observation for every match.

The publisher also acknowledges the sources used to compile results and odds,
including third-party results and odds-comparison sources. This matters because
the fact that Football-Data hosts a file does not automatically prove that the
underlying third-party data may be redistributed or used commercially.

### File-level inspection attempt

On 2026-09-07, an 8 KB range request was made for the public 2023/24 Premier
League file at:

`https://www.football-data.co.uk/mmz4281/2324/E0.csv`

The server returned a 489-byte HTML “page temporarily unavailable” response,
not CSV data. A second browser-based fetch also failed. No full file was
downloaded, and no raw data was committed.

Therefore this audit has not independently verified:

- the actual header in the current file;
- the row count or match coverage;
- the presence and completeness of closing columns;
- missing-value patterns;
- whether all three target-league files have the same structure.

### Secondary schema references

Public documentation and downstream schema references describe conventional
Football-Data fields including `FTR` for the full-time result, bookmaker
columns such as `B365H/B365D/B365A`, and closing columns such as
`B365CH/B365CD/B365CA`. These references are useful navigation aids, but they
are not treated as authoritative evidence of the current raw files.

## Licensing finding

The publisher describes the data as free and provides a disclaimer, but this
review did not locate a clear, broad licence granting all of the following:

- redistribution of raw files;
- publication of joined or derived datasets;
- commercial reuse;
- sublicensing of data originating from third parties.

The safe current position is **review-only / possible private research**, pending
written clarification or a sufficiently explicit licence. No data may be
published or made a repository dependency on the basis of “free download” alone.

## Decision

Football-Data remains a **conditional candidate** for a closing-market
benchmark, not an approved data dependency.

The closing-benchmark study may proceed only after:

1. the source is reachable for a small, permitted sample inspection;
2. the three target league files are checked for coverage and closing-field
   completeness;
3. the match identity and kickoff-time fields are confirmed;
4. the exact de-vigging and consensus construction rules are frozen;
5. reuse and publication terms are clarified; and
6. Victor approves acquisition and any resulting data handling.

Until then, the registered conclusion remains **Further Study Required**. This
verification does not approve a model, provider, architecture, paid access,
deployment, or betting decision.

## Source records

- [Football-Data historical data](https://www.football-data.co.uk/data)
- [Football-Data downloads](https://www.football-data.co.uk/downloadm.php)
- [Football-Data fixture notes](https://www.football-data.co.uk/matches/resources/notes.txt)
- [Football-Data disclaimer](https://www.football-data.co.uk/disclaimer.php)
- [StatsBomb open-data schema reference used for comparison only](https://github.com/hudl/open-data)

