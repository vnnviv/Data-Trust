**Project Title:** Can You Trust "Best"? Three Tests for Strategy Rankings

## Problem
How much can players and coaches trust a "best champion" ranking in League of Legends, given that different ranking methods can disagree and a game patch can change the answer?

## Why it is Important
Players and coaches decide what to practice and draft using claims that a champion is "the best." In games where strategies counter each other, one ranking can mislead, win rates in team games are noisy, and a patch can change the picture within weeks. Anyone who acts on a ranking has a stake in knowing how much it depends on how it was measured. The same questions apply wherever there is no single agreed measure of "best."

## Hypothesis
- Rankings from different methods will disagree about the top champions by more than the sampling noise within any single method.
- Rankings will change after a patch by more than they change within a single patch.
- A rating fitted on one patch will predict matchups in the next patch better than a simple champion-average baseline.

Thresholds are set from a simulation before we look at results. Hypotheses are recorded in `PREREGISTRATION.md`. Results that do not support them will be reported.

## Data Required
- Riot Games API, match-v5 (real ranked matches with patch numbers): https://developer.riotgames.com/apis#match-v5
- Backup if matchup counts are too small: OpenDota API (Dota 2): https://docs.opendota.com/

[Confirm API terms, rate limits, and history depth before submitting. Add any further links.]

## Analysis Plan
We build a champion-vs-champion win matrix for about 20 champions in one role and rank tier, then rank them three ways (raw win rate, a Bradley-Terry rating, and Nash averaging). To tell real disagreement from noise, we compare how much two methods differ with how much a single method differs between two random halves of the data, and we test the methods first on simulated games where we know the right answer. We repeat the analysis across patches, comparing change across patches with change within a patch, and we check which ranking best predicts matches from the following patch. Results come with uncertainty intervals, and we rerun the main comparison under a few predefined analysis choices. Planned figures: a rank-shift chart across methods with uncertainty bars, a noise-floor comparison, and a prediction-accuracy chart.
