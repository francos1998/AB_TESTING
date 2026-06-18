# Cookie Cats A/B Test Analysis

## Overview

Cookie Cats is a mobile puzzle game developed by Tactile Entertainment where players progress through increasingly difficult levels. As players advance, they encounter gates that temporarily block progress, requiring either a wait or an in-app purchase to continue. These gates serve a dual purpose: generating revenue and potentially improving long-term engagement by encouraging players to take breaks rather than burning out.
This project analyzes a real A/B test run by the game's development team to evaluate the impact of moving the first progression gate from level 30 to level 40 on player retention. The central business question is whether delaying the gate encounter changes how likely players are to return to the game after one day and after seven days.

## Dataset

The dataset contains 90,189 players who installed the game during the A/B test window and were randomly assigned to one of two groups. The variables in the data are:

userid: Unique player identifier

version: gate_30 (control) or gate_40 (treatment)

sum_gamerounds: Game rounds played in the first 14 days

retention_1: Whether the player returned 1 day after installing

retention_7: Whether the player returned 7 days after installing

## Analysis Structure
The notebook covers the following steps in order:

1. Exploratory data analysis: group balance check, distribution of game rounds, outlier identification and removal
Hypothesis definition — null and alternative hypotheses for both retention metrics, and the practical decision being informed

2. Power analysis: retrospective calculation of the minimum detectable effect given the actual sample size, and a prospective calculation of the sample size required to detect a 1 percentage point lift

3. Hypothesis testing: two-proportion z-tests comparing retention rates between gate_30 and gate_40 for both metrics

4. Confidence intervals: 95% confidence intervals for the difference in retention rates between groups

5. Segment analysis and robustness checks: engagement-based segmentation using a median split on game rounds, Mann-Whitney U test on overall engagement volume, and confirmation that outlier removal did not materially affect results

## Key Findings

The analysis provides clear evidence that moving the gate from level 30 to level 40 negatively affects 7-day player retention. Gate_30 outperforms gate_40 by approximately 0.83 percentage points on 7-day retention, a statistically significant result (z = 3.212, p = 0.0013) with a 95% confidence interval of 0.32 to 1.34 percentage points entirely above zero. For 1-day retention the result is not statistically significant (p = 0.0704), however the observed gap falls below the minimum detectable effect of 0.93 percentage points, suggesting a real but smaller effect may exist that the test lacks sufficient power to confirm. The segment analysis shows the retention advantage is concentrated almost entirely among high-engagement players, consistent with the expectation that low-engagement players likely never reach either gate.

## Recommendation

The evidence supports keeping the gate at level 30 rather than moving it to level 40, with the caveat that the absolute magnitude of the retention difference is modest, roughly one percentage point, and should be weighed against any product or monetization considerations that may favor the level 40 placement.

## Libraries Used
pandas, numpy, scipy, statsmodels, matplotlib
