# Stats Notes

Notes and references for Statistics. Taken from various places on the internet.

## Table of Contents

* [Overview](#overview)
* [Null Hypothesis Significance Testing (NHST)](#null-hypothesis-significance-testing-nhst)
  * [Notation](#notation)
  * [p-value](#p-value)
  * [Type I and Type II Errors](#type-i-and-type-ii-errors)
  * [Power](#power)
  * [T-statistic vs Z-statistic](#t-statistic-vs-z-statistic)
* [Central Limit Theorem](#central-limit-theorem)
* [Multiple Comparisons](#multiple-comparisons)
* [References](#references)

## Overview

## Null Hypothesis Significance Testing (NHST)

Statistical tests use data from samples to assess, or make inferences about, a statistical population. In the concrete setting of a two-sample comparison, the goal is to assess whether the mean values of some attribute obtained for individuals in two sub-populations differ. For example, to test the null hypothesis that the mean scores of men and women on a test do not differ, samples of men and women are drawn, the test is administered to them, and the mean score of one group is compared to that of the other group using a statistical test such as the two-sample t-test.

### Notation

* &beta; = probability of a Type II error, known as a "false negative"
* 1 - &beta; = probability of a "true positive", i.e., correctly rejecting the null hypothesis. "1 - &beta;" is also known as the **power of the test**.
* &alpha; = probability of a Type I error, known as a "false positive".  &alpha; is also known as the **significance level**.
* 1 - &alpha; = probability of a "true negative", i.e., correctly not rejecting the null hypothesis

### p-value
* In NHST, the [p-value](https://en.wikipedia.org/wiki/P-value) is the probability of obtaining test results at least as extreme as the results actually observed, **under the assumption that the null hypothesis is correct**.
  * The assumption on the null hypothesis is important!
  * A very small p-value means that such an extreme observed outcome would be very unlikely under the null hypothesis.

### Type I and Type II Errors
In statistical hypothesis testing,

* A **type I error** is the mistaken rejection of an actually true null hypothesis (also known as a "false positive" finding or conclusion; example: "an innocent person is convicted")
* A **type II error** is the mistaken acceptance of an actually false null hypothesis (also known as a "false negative" finding or conclusion; example: "a guilty person is not convicted").


|  | Null hypothesis is True | Null hypothesis is False |
| --- | --- | --- |
| **Result: don't reject null hypothesis** | Correct inference, (true negative), (probability = 1−&alpha;) | Type II error, (false negative), (probability = &beta;) |
| **Result: reject null hypothesis** | Type I error, (false positive), (probability = &alpha;)  | Correct inference, (true positive), (probability = 1−&beta;) |

### Power
The statistical **power** of a binary hypothesis test is the probability that the test correctly rejects the null hypothesis when a specific alternative hypothesis is true. It is commonly denoted by 1- &beta; , and represents the chances of a "true positive" detection conditional on the actual existence of an effect to detect.

Statistical power ranges from 0 to 1, and as the power of a test increases, the probability &beta; of making a type II error by wrongly failing to reject the null hypothesis decreases.

At a minimum, power nearly always depends on the following three factors:

* The statistical significance criterion used in the test.
  * One easy way to increase the power of a test is to carry out a less conservative test by using a larger significance criterion, for example 0.10 instead of 0.05.  This increases the chance of rejecting the null hypothesis (obtaining a statistically significant result) when the null hypothesis is false; that is, it reduces the risk of a type II error (false negative regarding whether an effect exists). But it also increases the risk of obtaining a statistically significant result (rejecting the null hypothesis) when the null hypothesis is not false; that is, it increases the risk of a type I error (false positive).
* The magnitude of the effect of interest in the population.
* The sample size used to detect the effect.
  * The sample size determines the amount of sampling error inherent in a test result. Other things being equal, effects are harder to detect in smaller samples. Increasing sample size is often the easiest way to boost the statistical power of a test.

### T-statistic vs Z-statistic

The choice in using a z-statistic  versus a t-statistic has to do with whether or not you are using a known population standard deviation or whether you are estimating it using the standard deviation calculated from the sample.

If you are using a sample standard deviation to calculate the standard error (estimate of the standard deviation of the sampling distribution), then you use a t-statistic, regardless of sample size.  Using a t-statistic corrects for the extra variability when using an estimate from a sample rather than a known population parameter.

However, as the samples gets large (n > 30), the difference between the z-statistic and t-statistic gets increasingly small.  This is because the standard deviation estimator comes [very close](https://stats.stackexchange.com/questions/61284/t-tests-vs-z-tests) to the true standard deviation.


## Central Limit Theorem


## Multiple Comparisons

## Variances

## References
* [Wikipedia: p-value](https://en.wikipedia.org/wiki/P-value)
* [Wikipedia: Power of a Test](https://en.wikipedia.org/wiki/Power_of_a_test)
* [Wikipedia: Type I and type II errors](https://en.wikipedia.org/wiki/Type_I_and_type_II_errors)
* [Statistics How To: T-Score vs. Z-Score: What’s the Difference?](https://www.statisticshowto.com/probability-and-statistics/hypothesis-testing/t-score-vs-z-score/)
