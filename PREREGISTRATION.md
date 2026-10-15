# Preregistration

Status: **NOT LOCKED.** Lock before looking at any outcome. When locked, record date and commit hash here: [date] [hash].

## Estimands
| ID | Quantity |
|---|---|
| E1 | Between-method disagreement (top-5 overlap and Kendall's tau) vs within-method split-half disagreement |
| E2 | Within-patch ranking instability (first half vs second half of one patch) |
| E3 | Cross-patch ranking instability (patch k vs k+1) |
| E4 | Out-of-sample log-loss on patch k+1 for predictions from each ranking, vs a champion-average baseline |

## Hypotheses
- **H1:** between-method disagreement exceeds within-method split-half disagreement (threshold: [set from simulation]).
- **H2:** observed matchup cycles exceed those produced by a Bradley-Terry model fitted to our data with real per-pair sample sizes (multiple-testing corrected).
- **H3:** cross-patch instability (E3) exceeds the within-patch noise floor (E2).
- **H4:** a rating fitted on patch k beats the champion-average baseline on patch k+1 (E4). A null result is reported as a null.

## Fixed analysis choices
- Role: [role]. Tier: [tier]. Champions: top ~20 by pick rate. Minimum games per pair: [set from simulation power analysis].
- Side (blue/red) included as a covariate. Resampling by match and by player.
- Exclusions: remakes, early surrenders under [X] minutes, AFK games. Patch transition windows dropped.
- Specification curve choices (only these): tier, minimum games per pair, rating method, [one more].
- Confirmatory split: develop on patch k, lock code, test on patch k+1.

## Decision log
| Date | Decision | Reason |
|---|---|---|
| | | |
