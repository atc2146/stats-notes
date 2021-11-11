# Stats Notes

Notes and references for Statistics. Taken from various places on the internet.

## Table of Contents

* [Overview](#overview)
* [Null Hypothesis Significance Testing (NHST)](#null-hypothesis-significance-testing-nhst)
  * [p-value](#p-value)
  * [Power](#power)
  * [T-statistic vs Z-statistic](#t-statistic-vs-z-statistic)
* [Central Limit Theorem](#central-limit-theorem)
* [References](#references)

## Overview

## Null Hypothesis Significance Testing (NHST)

### p-value
* In NHST, the [p-value](https://en.wikipedia.org/wiki/P-value) is the probability of obtaining test results at least as extreme as the results actually observed, **under the assumption that the null hypothesis is correct**.
  * The assumption on the null hypothesis is important!
  * A very small p-value means that such an extreme observed outcome would be very unlikely under the null hypothesis.
  


### Power
* The Power of a test is ...


### T-statistic vs Z-statistic

The choice in using a z-statistic  versus a t-statistic has to do with whether or not you are using a known population standard deviation or whether you are estimating it using the standard deviation calculated from the sample.

If you are using a sample standard deviation to calculate the standard error (estimate of the standard deviation of the sampling distribution), then you use a t-statistic, regardless of sample size.  Using a t-statistic corrects for the extra variability when using an estimate from a sample rather than a known population parameter.

However, as the samples gets large (> 30), the difference between the z-statistic and t-statistic gets increasingly small.  This is because the standard deviation estimator comes [very close](https://stats.stackexchange.com/questions/61284/t-tests-vs-z-tests) to the true standard deviation.


## Central Limit Theorem


## Variances

## References
* [Wikipedia: p-value](https://en.wikipedia.org/wiki/P-value)
* [Statistics How To: T-Score vs. Z-Score: What’s the Difference?](https://www.statisticshowto.com/probability-and-statistics/hypothesis-testing/t-score-vs-z-score/)
