# Stats Notes

Notes and references for Statistics. Taken from various places on the internet.

## Table of Contents

* [Overview](#overview)
* [Null Hypothesis Significance Testing (NHST)](#null-hypothesis-significance-testing-nhst)
  * [Notation](#notation)
  * [p-value](#p-value)
  * [Power](#power)
  * [T-statistic vs Z-statistic](#t-statistic-vs-z-statistic)
* [Central Limit Theorem](#central-limit-theorem)
* [Multiple Comparisons](#multiple-comparisons)
* [References](#references)

## Overview

## Null Hypothesis Significance Testing (NHST)

### Notation

* &beta; = probability of a Type II error, known as a "false negative"
* 1 - &beta; = probability of a "true positive", i.e., correctly rejecting the null hypothesis. "1 - &beta;" is also known as the power of the test.
* &alpha; = probability of a Type I error, known as a "false positive"
* 1 - &alpha; = probability of a "true negative", i.e., correctly not rejecting the null hypothesis

### p-value
* In NHST, the [p-value](https://en.wikipedia.org/wiki/P-value) is the probability of obtaining test results at least as extreme as the results actually observed, **under the assumption that the null hypothesis is correct**.
  * The assumption on the null hypothesis is important!
  * A very small p-value means that such an extreme observed outcome would be very unlikely under the null hypothesis.

### Type I and Type II Errors

### Power
The statistical **power** of a binary hypothesis test is the probability that the test correctly rejects the null hypothesis when a specific alternative hypothesis is true. It is commonly denoted by 1- &beta; , and represents the chances of a "true positive" detection conditional on the actual existence of an effect to detect.

Statistical power ranges from 0 to 1, and as the power of a test increases, the probability &beta; of making a type II error by wrongly failing to reject the null hypothesis decreases.


### T-statistic vs Z-statistic

The choice in using a z-statistic  versus a t-statistic has to do with whether or not you are using a known population standard deviation or whether you are estimating it using the standard deviation calculated from the sample.

If you are using a sample standard deviation to calculate the standard error (estimate of the standard deviation of the sampling distribution), then you use a t-statistic, regardless of sample size.  Using a t-statistic corrects for the extra variability when using an estimate from a sample rather than a known population parameter.

However, as the samples gets large (n > 30), the difference between the z-statistic and t-statistic gets increasingly small.  This is because the standard deviation estimator comes [very close](https://stats.stackexchange.com/questions/61284/t-tests-vs-z-tests) to the true standard deviation.


## Central Limit Theorem


## Multiple Comparisons

## Variances

## References
* [Wikipedia: p-value](https://en.wikipedia.org/wiki/P-value)
* [Statistics How To: T-Score vs. Z-Score: What’s the Difference?](https://www.statisticshowto.com/probability-and-statistics/hypothesis-testing/t-score-vs-z-score/)
