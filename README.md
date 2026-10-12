[README.md](https://github.com/user-attachments/files/33319484/README.md)
# Diagnosing Broken Confidence Intervals

## Objective

I tested why confidence intervals can give misleading results when data contain tied values, skewness or dependence within groups.

## Methodology

- Bootstrapped the median of 32,561 integer ages and examined the zero standard error and BCa warnings.
- Measured interval coverage on skewed data using samples of 50 across 400 experiments.
- Compared worker-level and firm-level bootstrapping for wages from 25 firms.
- Used `bootstrap_utils.py` to calculate percentile intervals and bootstrap means.
- Revised an AI-generated coverage function’s seed handling and checked its results against Diagnosis 3.

## Key Findings

The age median’s bootstrap standard error was **0.000000**. BCa returned **NaN** with warnings because its adjustment could not be calculated; this did not mean the population median was known exactly.

For nominal 95% intervals on skewed data, mean coverage was **92.5% for the parametric method** and **92.0% for the bootstrap**. Median coverage was **66.8% for the mean-based parametric interval** and **92.8% for the bootstrap**, showing why an interval must match its target statistic.

The firm-level interval was **5.7 times wider** than the worker-level interval. Resampling whole firms increased coverage from **19.5% to 91.0%**, although it remained below 95%.

My revised coverage function reproduced the **19.5% and 91.0%** results exactly.
