# Statistics Notes

Notes and references for Statistics. Taken from various places on the internet.

## Table of Contents

* [Overview](#overview)
* [Fundamentals](#fundamentals)
  * [Law of Large Numbers](#law-of-large-numbers)
* [Bayes Theorem](#bayes-theorem)
* [Null Hypothesis Significance Testing (NHST)](#null-hypothesis-significance-testing-nhst)
  * [Notation](#notation)
  * [p-value](#p-value)
  * [Type I and Type II Errors](#type-i-and-type-ii-errors)
  * [Power](#power)
  * [Confidence Intervals](#confidence-intervals)
  * [T-statistic vs Z-statistic](#t-statistic-vs-z-statistic)
* [Central Limit Theorem](#central-limit-theorem)
  * [Standard Error of the Mean](#standard-error-of-the-mean)
* [Distributions](#distributions)
  * [Normal Distribution](#normal-distribution)
  * [Bernoulli Distribution](#bernoulli-distribution)
* [Multiple Comparisons](#multiple-comparisons)
* [Machine Learning](#machine-learning)
  * [L1 and L2 Norm](#l1-and-l2-norm)
* [Linear Regression](#linear-regression)
* [Logistic Regression](#logistic-regression)
* [Trees](#trees)
* [Online Controlled Experiments](#online-controlled-experiments)
  * [Variance Reduction Techniques](#variance-reduction-techniques)
* [Chi-squared test](#chi-squared-test)
* [Other](#other)
  * [Bessel's correction](#Bessels-correction)
* [References](#references)

## Overview

## Fundamentals
* Variance is a measure of spread.
  * The sample variance is calculated as the (sum of squared deviations) divided by (n - 1).
      * Note, there is an [alternative formula](https://en.wikipedia.org/wiki/Algorithms_for_calculating_variance) where you do not need to calculate the mean.
  * Standard deviation is the square root of variance.

### Law of Large Numbers


## Bayes Theorem
* Bayes Theorem describes the probability of an event, based on prior knowledge of conditions that might be related to the event.
* Mathematically, `P(A|B) = (P(B|A) * P(A)) / P(B)`
  * `P(A|B)` is a conditional probability: the probability of event A occurring given that B is true. It is also called the posterior probability of A given B.
  * `P(B|A)` is a conditional probability: the probability of event B occurring given that A is true.
  * `P(A)` and `P(B)` are the probabilities of observing A and B respectively without any given conditions; they are known as the marginal probability or prior probability.



## Null Hypothesis Significance Testing (NHST)

Statistical tests use data from samples to assess, or make inferences about, a statistical population. In the concrete setting of a two-sample comparison, the goal is to assess whether the mean values of some attribute obtained for individuals in two sub-populations differ. For example, to test the null hypothesis that the mean scores of men and women on a test do not differ, samples of men and women are drawn, the test is administered to them, and the mean score of one group is compared to that of the other group using a statistical test such as the two-sample t-test.

### Notation

* &beta; = probability of a Type II error, known as a "false negative".
* 1 - &beta; = probability of a "true positive", i.e., correctly rejecting the null hypothesis. "1 - &beta;" is also known as the **power of the test**.
* &alpha; = probability of a Type I error, known as a "false positive".  &alpha; is also known as the **significance level**.
* 1 - &alpha; = probability of a "true negative", i.e., correctly not rejecting the null hypothesis

Here's a summary table:

|  | Null hypothesis is True | Null hypothesis is False |
| --- | --- | --- |
| **Result: don't reject null hypothesis** | Correct inference<br/> (true negative)<br/> (probability = 1−&alpha;) | Type II error<br/> (false negative)<br/> (probability = &beta;) |
| **Result: reject null hypothesis** | Type I error<br/> (false positive)<br/> (probability = &alpha;)  | Correct inference<br/> (true positive)<br/> (probability = 1−&beta;) |

### p-value
* In NHST, the [p-value](https://en.wikipedia.org/wiki/P-value) is the probability of obtaining test results at least as extreme as the results actually observed, **under the assumption that the null hypothesis is correct**.
  * The assumption on the null hypothesis is important!
  * A very small p-value means that such an extreme observed outcome would be very unlikely under the null hypothesis.

### Type I and Type II Errors
In statistical hypothesis testing,

* A **type I error** is the mistaken rejection of an actually true null hypothesis (also known as a "false positive" finding or conclusion; example: "an innocent person is convicted")
* A **type II error** is the mistaken acceptance of an actually false null hypothesis (also known as a "false negative" finding or conclusion; example: "a guilty person is not convicted").

### Power
The statistical **power** of a binary hypothesis test is the probability that the test correctly rejects the null hypothesis when a specific alternative hypothesis is true. It is commonly denoted by 1- &beta; , and represents the chances of a "true positive" detection conditional on the actual existence of an effect to detect.

Statistical power ranges from 0 to 1, and as the power of a test increases, the probability &beta; of making a type II error by wrongly failing to reject the null hypothesis decreases.

At a minimum, power nearly always depends on the following three factors:

* The statistical significance criterion used in the test (&alpha;).
  * One easy way to increase the power of a test is to carry out a less conservative test by using a larger significance criterion, for example 0.10 instead of 0.05.  This increases the chance of rejecting the null hypothesis (obtaining a statistically significant result) when the null hypothesis is false; that is, it reduces the risk of a type II error (false negative regarding whether an effect exists). But it also increases the risk of obtaining a statistically significant result (rejecting the null hypothesis) when the null hypothesis is not false; that is, it increases the risk of a type I error (false positive).
* The magnitude of the effect of interest in the population.
* The sample size used to detect the effect.
  * The sample size determines the amount of sampling error inherent in a test result. Other things being equal, effects are harder to detect in smaller samples. Increasing sample size is often the easiest way to boost the statistical power of a test.

### Confidence Intervals

* General form of a confidence interval: `sample statistic +- margin of error`.
  * General form of margin of error: `Multiplier * Standard Error(Estimate)`.
*  Increasing the confidence level of a confidence interval will only result in larger intervals.
* Interpretation: If we repeatedly draw random samples of size n from the population and calculate the confidence interval each time, we would expect that 100(1-&alpha;)% of the intervals would contain the true parameter.
  * For a **given** CI, either the true parameter is in it or it is not!


### T-statistic vs Z-statistic

The choice in using a z-statistic  versus a t-statistic has to do with whether or not you are using a known population standard deviation or whether you are estimating it using the standard deviation calculated from the sample.

If you are using a sample standard deviation to calculate the standard error (estimate of the standard deviation of the sampling distribution), then you use a t-statistic, regardless of sample size.  Using a t-statistic corrects for the extra variability when using an estimate from a sample rather than a known population parameter.

However, as the samples gets large (n > 30), the difference between the z-statistic and t-statistic gets increasingly small.  This is because the standard deviation estimator comes [very close](https://stats.stackexchange.com/questions/61284/t-tests-vs-z-tests) to the true standard deviation.

### Hypothesis Testing for Two-Sample Means
* Independent Sample or Dependent Sample?
  * Independent: The samples from two populations are independent if the samples selected from one of the populations have no relationship with the samples selected from the other population.
  * Dependent: The samples are dependent (also called paired data) if each measurement in one sample is matched or paired with a particular measurement in the other sample. Another way to consider this is how many measurements are taken off of each subject. If only one measurement, then independent; if two measurements, then paired.

* Pooled or Unpooled Variance for sample variance calculation?
  * There are two versions of this test, one is used when the variances of the two populations are equal (the pooled test) and the other one is used when the variances of the two populations are unequal (the unpooled test).
  * The consequence of using unpooled is that the test is more conservative making it marginally more difficult to reject the null. However, the consequence of using pooled variances is an incorrect model. 


## Central Limit Theorem

* In probability theory, the central limit theorem (CLT) establishes that, in many situations, when independent random variables are summed up, their properly normalized sum tends toward a normal distribution (informally a bell curve) even if the original variables themselves are not normally distributed.
* In other words, the sampling distribution of the sample mean of **any (most)** distribution very closely approximates the normal distribution as n approaches infinity (n is the sample size).
  * In fact, the sampling distribution of the sample sum (or any statistic like the mode, etc.) is also normally distributed.

### Standard Error of the Mean
* The variance of the sampling distribution of the sample mean equals `(the variance of the original distribution) / n`
* *Note*: a larger n (sample size) leads to a lower standard error of the mean (standard deviation of the sampling distribution of the sample mean).  The variance is inversely proportion to n.

## Distributions

### Normal Distribution

* The **normal** distribution, or **Gaussian** distribution, is a type of continuous probability distribution for a real-valued random variable.
* The normal distribution is completely characterized by its mean and its standard deviation.
* Normal distributions are important in statistics and are often used in the natural and social sciences to represent real-valued random variables whose distributions are not known. Their importance is partly due to the central limit theorem.
* A good rule of thumb is the 68-95-99.7 rule in that respectively 68%, 95%, and 99.7% of observations will fall within 1, 2, and 3 standard deviations from the mean.
* We can convert any normal distribution into the standard normal distribution in order to find probability and apply the properties of the standard normal. In order to do this, we use the z-value.
  * The Z-value (or sometimes referred to as Z-score or simply Z) represents the number of standard deviations an observation is from the mean for a set of data. To find the z-score for a particular observation we apply the following formula: `(observed value - mean) / SD`

### Bernoulli Distribution

* The **Bernoulli distribution** is the discrete probability distribution of a random variable which takes the value 1 with probability `p` and the value 0 with probability `q = 1 - p`.
* Mean and Standard Deviation [Standard Error] of the Sample Proportion:
  * The sample mean is just the proportion of successes.
  * The variance of the sample proportion is `p(1-p)/n`

## Multiple Comparisons

## Machine Learning

### L1 and L2 Norm

## Linear Regression

The assumptions of linear regression:
* Text

Why use least squares as the loss (cost) function?
* Text
* Text

## Logistic Regression

## Trees 

## Chi-squared test
*  Pearson's chi-squared test is used to determine whether there is a statistically significant difference between the expected frequencies and the observed frequencies in one or more categories of a contingency table. Used for counts.

Similarly, (One-way) ANOVA is used to investigate whether differences in means (for 3 or more cohorts) between samples are significant or not.  We use the F statistic.

However, these are not really used in online controlled experimentation as we generally need to compare pairs of cohorts.

## Online Controlled Experiments

* **Observational** study is where observations or measurements area analyzed without manipulating any variables. These studies show that there may be a relationship but not necessarily a cause and effect relationship. 
* **Experimental** study involves some random assignment of a treatment; researchers can draw cause and effect (or causal) conclusions.

### Variance Reduction Techniques

#### CUPED
* CUPAC (Doordash)
* VWE (Facebook)

#### Stratification

#### Winsorization

## Other
* Positive skew has long right tail.

![skew](https://upload.wikimedia.org/wikipedia/commons/c/cc/Relationship_between_mean_and_median_under_different_skewness.png)

* Parameter is a number that describes the data from a **population** while a statistic is a number that describes the data from a **sample**.
* Statistical and Practical Significance: Statistical significance is concerned with whether an observed effect is due to chance and practical significance means that the observed effect is large enough to be useful in the real world.
* The covariance is simply a measure of the variance of two variables - how one moves in relation to the other.

### Bessel's correction
In statistics, [Bessel's correction](https://en.wikipedia.org/wiki/Bessel%27s_correction) is the use of `n − 1` instead of `n` in the formula for the sample variance and sample standard deviation, where `n` is the number of observations in a sample. This method corrects the bias in the estimation of the population variance. It also partially corrects the bias in the estimation of the population standard deviation. However, the correction often increases the mean squared error in these estimations. 

The standard deviation calculated with a divisor of n−1 is a standard deviation calculated from the sample as an estimate of the standard deviation of the population from which the sample was drawn. Because the observed values fall, on average, closer to the sample mean than to the population mean, the standard deviation which is calculated using deviations from the sample mean underestimates the desired standard deviation of the population. Using `n − 1` instead of `n` as the divisor corrects for that by making the result a little bit bigger.

## References
* [Wikipedia: Chi-squared test](https://en.wikipedia.org/wiki/Chi-squared_test)
* [Wikipedia: p-value](https://en.wikipedia.org/wiki/P-value)
* [Wikipedia: Power of a Test](https://en.wikipedia.org/wiki/Power_of_a_test)
* [Wikipedia: Type I and type II errors](https://en.wikipedia.org/wiki/Type_I_and_type_II_errors)
* [Wikipedia: Central Limit Theorem](https://en.wikipedia.org/wiki/Central_limit_theorem)
* [Wikipedia: Normal Distribution](https://en.wikipedia.org/wiki/Normal_distribution)
* [Bessel's correction](https://en.wikipedia.org/wiki/Bessel%27s_correction)
* [Statistics How To: T-Score vs. Z-Score: What’s the Difference?](https://www.statisticshowto.com/probability-and-statistics/hypothesis-testing/t-score-vs-z-score/)
* [PSU: STAT 800](https://online.stat.psu.edu/stat800/)
* [Stackexchange: Intuitive explanation for dividing by n−1 when calculating standard deviation?](https://stats.stackexchange.com/questions/3931/intuitive-explanation-for-dividing-by-n-1-when-calculating-standard-deviation)
* [40 Stats Interviews Problems](https://towardsdatascience.com/40-statistics-interview-problems-and-answers-for-data-scientists-6971a02b7eee)
* [Calculation of Variance: MOSSOM](https://www.mun.ca/biology/scarr/Simplified_calculation_of_variance.html)
* [Practical Statistics for Data Scientists: 50 Essential Concepts](https://www.oreilly.com/library/view/practical-statistics-for/9781491952955/)
* [The Art of Statistics](https://www.goodreads.com/book/show/43722897-the-art-of-statistics)