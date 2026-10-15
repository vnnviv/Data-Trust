# Can You Trust "Best"? Testing Strategy Rankings Across Methods and Game Patches

## Question
How much can players and coaches trust a "best champion" ranking, given that different ranking methods can disagree and a game patch can change the answer?

## Story: three tests of one claim
1. **Do rankings agree?** Compare ranking methods against each method's own sampling noise.
2. **Do they survive noise?** Intervals, a known-truth simulation, and a within-patch noise floor.
3. **Do they survive a patch?** Compare cross-patch change with the within-patch noise floor, and check which ranking predicts held-out matches.

Takeaway: draft guidance for reading a ranking. It is written after the results, not before.

## Design
| Step | What | Key control |
|---|---|---|
| 0 | Known-truth simulation | Planted structure, plus a misspecified generator |
| 1 | Rankings from a pairwise win matrix (raw win rate, Bradley-Terry, Nash averaging) | Cluster bootstrap by match and player; side covariate |
| 2 | Within-method split-half noise floor vs between-method disagreement | Decides whether the headline claim holds |
| 3 | Patch comparison: cross-patch vs within-patch split-half | Confirmatory split: build on patch k, test on k+1 |
| 4 | Held-out predictive check (logistic models, log-loss vs champion prior) | Benchmark not built from the same matrix |
| 5 | Specification curve over 3-4 predefined choices | Choices fixed before analysis |

Cut or deferred: gradient boosting, grouped-split ML, dispersion-decay, equilibrium comparison, paper decision (revisit in May).

## Data
- Riot Games API (match-v5), real ranked matches, one role and tier first. Confirm key type, rate limits, terms, history depth, and version field.
- Collection starts early so enough patches accumulate. Sampling rule logged in `docs/LOG.md`.
- Player IDs anonymized at ingestion. Raw data is never committed.
- Fallback ladder: any-opposing-champion matchups, then Dota 2 via OpenDota, then Part A only.


## Tools
Python 3.12, pandas, numpy, scipy, statsmodels, scikit-learn, matplotlib. SQLite for storage. GitHub for version control. Poster and slides in Google Slides or PowerPoint, exported to PDF.

## Limitations (state on the poster)
Win rate is a noisy payoff in a team game. Players choose champions they are good at. Public ranked data is a proxy for collegiate play. Sampling may not represent the player base. Patches change who plays what. Some matchup pairs have few games. Novelty is unchecked against the literature.
