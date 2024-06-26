# Statistics Notes

Notes and references for Statistics. Taken from various places on the internet. For educational use only.

## Table of Contents

* [Overview](#overview)
* [Fundamentals](#fundamentals)
* [Bayes Theorem](#bayes-theorem)
* [Null Hypothesis Significance Testing (NHST)](#null-hypothesis-significance-testing-nhst)
  * [Notation](#notation)
  * [Type I and Type II Errors](#type-i-and-type-ii-errors)
  * [p-value](#p-value)
  * [Power](#power)
  * [Confidence Intervals](#confidence-intervals)
  * [Prediction Intervals](#prediction-intervals)
  * [T-statistic vs Z-statistic](#t-statistic-vs-z-statistic)
  * [Hypothesis Testing for Two-Sample Means](hypothesis-testing-for-two-sample-means)
* [Law of Large Numbers](#law-of-large-numbers)
* [Central Limit Theorem](#central-limit-theorem)
  * [Standard Error of the Mean](#standard-error-of-the-mean)
* [Distributions](#distributions)
  * [Normal Distribution](#normal-distribution)
  * [Uniform Distribution](#uniform-distribution)
  * [Bernoulli Distribution](#bernoulli-distribution)
* [Multiple Comparisons](#multiple-comparisons)
  * [Bonferroni Correction](#bonferroni-correction)
* [Machine Learning](#machine-learning)
  * [Bias Variance Tradeoff](#bias-variance-tradeoff)
  * [L1 and L2 Norm](#l1-and-l2-norm)
  * [Linear Regression](#linear-regression)
  * [Logistic Regression](#logistic-regression)
  * [Trees](#trees)
    * [Bagging](#bagging)
    * [Boosting](#boosting)
  * [Support Vector Machines](#support-vector-machines)
  * [Deep Learning](#deep-learning)
* [Online Controlled Experiments](#online-controlled-experiments)
  * [Variance Reduction Techniques](#variance-reduction-techniques)
* [Causal Inference](#causal-inference)
  * [Propensity Score Matching](#propensity-score-matching)
* [Resampling Methods](#resampling-methods)
* [Chi-Squared Test](#chi-squared-test)
* [Fisher's Exact test](#fishers-exact-test)
* [Other](#other)
  * [Bessel's Correction](#Bessels-correction)
* [References](#references)

## Overview

## Fundamentals
* Variance is a measure of spread.
  * The sample variance is calculated as the (sum of squared deviations) divided by (n - 1).
      * Note, there is an [alternative formula](https://en.wikipedia.org/wiki/Algorithms_for_calculating_variance) where you do not need to calculate the mean.
  * Standard deviation is the square root of variance.


## Bayes Theorem
* Bayes Theorem describes the probability of an event, based on prior knowledge of conditions that might be related to the event.
* Mathematically, `P(A|B) = (P(B|A) * P(A)) / P(B) = (P(B|A) * P(A)) / ( P(B|A)*P(A) + P(B|~A)*P(~A) )`
  * `P(A|B)` is a conditional probability: the probability of event A occurring given that B is true. It is also called the posterior probability of A given B.
  * `P(B|A)` is a conditional probability: the probability of event B occurring given that A is true.
  * `P(A)` and `P(B)` are the probabilities of observing A and B respectively without any given conditions; they are known as the marginal probability or prior probability.

This [blog](https://thestatsninja.com/2019/03/03/how-to-decipher-false-positives-and-negatives-with-bayes-theorem/) has some good examples and further explanation.

## Null Hypothesis Significance Testing (NHST)

Statistical tests use data from **samples** to assess, or make inferences about, a statistical **population**. In the concrete setting of a two-sample comparison, the goal is to assess whether the mean values of some attribute obtained for individuals in two sub-populations differ. For example, to test the null hypothesis that the mean scores of men and women on a test do not differ, samples of men and women are drawn, the test is administered to them, and the mean score of one group is compared to that of the other group using a statistical test such as the two-sample t-test.

### Notation

* &beta; = probability of a Type II error, known as a "false negative".
* 1 - &beta; = probability of a "true positive", i.e., correctly rejecting the null hypothesis.
    * "1 - &beta;" is also known as the **power of the test**.
* &alpha; = probability of a Type I error, known as a "false positive".
    * &alpha; is also known as the **significance level**.
* 1 - &alpha; = probability of a "true negative", i.e., correctly not rejecting the null hypothesis

Here's a summary table:

|  | Null hypothesis is True | Null hypothesis is False |
| --- | --- | --- |
| **Result: don't reject null hypothesis** | Correct inference<br/> (true negative)<br/> (probability = 1−&alpha;) | Type II error<br/> (false negative)<br/> (probability = &beta;) |
| **Result: reject null hypothesis** | Type I error<br/> (false positive)<br/> (probability = &alpha;)  | Correct inference<br/> (true positive)<br/> (probability = 1−&beta;) |

### Type I and Type II Errors
In statistical hypothesis testing,

* A **Type I error** is the mistaken rejection of an actually true null hypothesis (also known as a "false positive" finding or conclusion)
    * Example: "an innocent person is convicted"
* A **Type II error** is the mistaken acceptance of an actually false null hypothesis (also known as a "false negative" finding or conclusion)
    * Example: "a guilty person is not convicted".


### p-value
* In NHST, the [p-value](https://en.wikipedia.org/wiki/P-value) is the probability of obtaining test results at least as extreme as the results actually observed, **under the assumption that the null hypothesis is correct**.
  * The assumption on the null hypothesis is important!
  * A very small p-value means that such an extreme observed outcome would be very unlikely under the null hypothesis.


### Power
The statistical **power** of a binary hypothesis test is the probability that the test correctly rejects the null hypothesis when a specific alternative hypothesis is true. It is commonly denoted by 1- &beta; , and represents the chances of a "true positive" detection conditional on the actual existence of an effect to detect.

Statistical power ranges from 0 to 1, and as the power of a test increases, the probability &beta; of making a type II error by wrongly failing to reject the null hypothesis decreases.

At a minimum, power nearly always depends on the following three factors:

1. The **statistical significance criterion** used in the test (&alpha;).
   * One easy way to increase the power of a test is to carry out a less conservative test by using a larger significance criterion, for example 0.10 instead of 0.05.  This increases the chance of rejecting the null hypothesis (obtaining a statistically significant result) when the null hypothesis is false; that is, it reduces the risk of a type II error (false negative regarding whether an effect exists). But it also increases the risk of obtaining a statistically significant result (rejecting the null hypothesis) when the null hypothesis is not false; that is, it increases the risk of a type I error (false positive).
2. The **magnitude of the effect** of interest in the population.
3. The **sample size** used to detect the effect.
   * The sample size determines the amount of sampling error inherent in a test result. Other things being equal, effects are harder to detect in smaller samples. Increasing sample size is often the easiest way to boost the statistical power of a test.

### Confidence Intervals

* General form of a confidence interval: `(sample statistic) +- (margin of error)`.
  * General form of margin of error: `Multiplier * Standard Error(Estimate)`.
*  Increasing the confidence level of a confidence interval will only result in larger intervals.
* Interpretation: If we repeatedly draw random samples of size n from the population and calculate the confidence interval each time, we would expect that 100(1-&alpha;)% of the intervals would contain the true parameter.
  * For a **given** CI, either the true parameter is in it or it is not!

### Prediction Intervals

TBA

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
  * The consequence of using:
    * The **unpooled version** is that the test is more conservative making it marginally more difficult to reject the null.
    * The **pooled version** is a potentially **incorrect** model. 

## Law of Large Numbers
In probability theory, the law of large numbers (LLN) is a mathematical theorem that states that the average of the results obtained from a large number of independent and identical random samples converges to the true value, if it exists. More formally, the LLN states that given a sample of independent and identically distributed values, the sample mean converges to the true mean.

## Central Limit Theorem

* In probability theory, the [Central Limit Theorem](https://www.youtube.com/watch?v=JNm3M9cqWyc&ab_channel=KhanAcademy) (CLT) establishes that, in many situations, when independent random variables are summed up, their properly *normalized* sum tends toward a normal distribution (informally a bell curve) even if the original variables themselves are not normally distributed.
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
* We can convert any normal distribution into the **standard normal distribution** in order to find probability and apply the properties of the standard normal. In order to do this, we use the z-value.
  * The Z-value (or sometimes referred to as Z-score or simply Z) represents the number of standard deviations an observation is from the mean for a set of data. To find the z-score for a particular observation we apply the following formula: `(observed value - mean) / SD`

### Uniform Distribution

### Bernoulli Distribution

* The **Bernoulli distribution** is the discrete probability distribution of a random variable which takes the value 1 with probability `p` and the value 0 with probability `q = 1 - p`.
* Mean and Standard Deviation [Standard Error] of the Sample Proportion:
  * The sample mean is just the proportion of successes.
  * The variance of the sample proportion is `p(1-p)/n`
  * The Bernoulli distribution is a special case of the binomial distribution where a single trial is conducted (so n would be 1 for such a binomial distribution).

## Multiple Comparisons

### Bonferonni Correction

## Machine Learning

### Bias Variance Tradeoff

* In general, as we increase the number of tunable parameters in a model, it becomes more flexible, and can better fit a training data set. It is said to have lower error, or bias. However, for more flexible models, there will tend to be greater variance to the model fit each time we take a set of samples to create a new training data set. It is said that there is greater variance in the model's estimated parameters.
* High Bias is equivalent to model underfitting the training data.
* High Variance is equivalent to the model overfitting training data. That is, it performs well on training data but poorly on new data.

Some ways to reduce bias and variance include: Cross validation, ensemble methods, feature selection, regularization, etc.

### L1 and L2 Norm

### Linear Regression

The assumptions of linear regression:
* Text

Why use least squares as the loss (cost) function?
* Text
* Text

### Logistic Regression

### Trees 

#### Bagging

#### Boosting


### Support Vector Machines

### Deep Learning

## Resampling Methods

## Chi-Squared Test
Pearson's Chi-Squared Test is used to determine whether there is a statistically significant difference between the expected frequencies and the observed frequencies in one or more categories of a contingency table. It is used for **counts**.

Similarly, (One-way) ANOVA is used to investigate whether differences in means (for 3 or more cohorts) between samples are significant or not.  We use the F statistic.

However, these are not really used in online controlled experimentation as we generally need to compare **pairs** of cohorts.

## Fisher's Exact Test

(Fisher's Exact Test)[https://en.wikipedia.org/wiki/Fisher%27s_exact_test] is a statistical significance test used in the analysis of contingency tables. Although in practice it is employed when sample sizes are small, it is valid for all sample sizes.  Fishers' Exact test is similar to the *Chi-squared test*, except the Chi-squared test uses an approximation.

## Online Controlled Experiments

* **Observational** study is where observations or measurements are analyzed without manipulating any variables. These studies show that there may be a relationship but not necessarily a cause and effect (causal) relationship. 
* **Experimental** study involves some random assignment of a treatment; researchers can draw cause and effect (or causal) conclusions.

### Variance Reduction Techniques

* CUPED: Controlled-experiment Using Pre-Experiment Data
* CUPAC (Doordash)
* VWE (Facebook)

#### CUPED


#### Stratification

#### Winsorization


## Causal Inference

* TBA

### Propensity Score Matching

* TBA


## Other
* Positive skew has a long right tail.

![skew](https://upload.wikimedia.org/wikipedia/commons/c/cc/Relationship_between_mean_and_median_under_different_skewness.png)

* Parameter vs. Statistic.
  * A parameter is a number that describes the data from a **population**. 
  * A statistic is a number that describes the data from a **sample**.
* Statistical and Practical Significance: Statistical significance is concerned with whether an observed effect is due to chance and practical significance means that the observed effect is large enough to be useful in the real world.
* The covariance is a measure of the variance of two random variables - how one moves in relation to the other.

### Bessel's Correction
In statistics, [Bessel's Correction](https://en.wikipedia.org/wiki/Bessel%27s_correction) is the use of `n − 1` instead of `n` in the formula for the sample variance and sample standard deviation, where `n` is the number of observations in a sample. This method corrects the bias in the estimation of the population variance. It also partially corrects the bias in the estimation of the population standard deviation. However, the correction often increases the mean squared error in these estimations. 

The standard deviation calculated with a divisor of `n − 1` is a standard deviation calculated from the sample as an estimate of the standard deviation of the population from which the sample was drawn. Because the observed values fall, on average, closer to the sample mean than to the population mean, the standard deviation which is calculated using deviations from the sample mean underestimates the desired standard deviation of the population. Using `n − 1` instead of `n` as the divisor corrects for that by making the result a little bit bigger.

## References
* [Wikipedia: Bernoulli Distribution](https://en.wikipedia.org/wiki/Bernoulli_distribution)
* [Wikipedia: Bessel's correction](https://en.wikipedia.org/wiki/Bessel%27s_correction)
* [Wikipedia: Bias-variance Tradeoff](https://en.wikipedia.org/wiki/Bias%E2%80%93variance_tradeoff)
* [Wikipedia: Bonferroni Correction](https://en.wikipedia.org/wiki/Bonferroni_correction)
* [Wikipedia: Central Limit Theorem](https://en.wikipedia.org/wiki/Central_limit_theorem)
* [Wikipedia: Chi-squared test](https://en.wikipedia.org/wiki/Chi-squared_test)
* [Wikipedia: Fisher's Exact Test](https://en.wikipedia.org/wiki/Fisher%27s_exact_test)
* [Wikipedia: Law of large numbers](https://en.wikipedia.org/wiki/Law_of_large_numbers)
* [Wikipedia: Normal Distribution](https://en.wikipedia.org/wiki/Normal_distribution)
* [Wikipedia: p-value](https://en.wikipedia.org/wiki/P-value)
* [Wikipedia: Power of a Test](https://en.wikipedia.org/wiki/Power_of_a_test)
* [Wikipedia: Type I and type II errors](https://en.wikipedia.org/wiki/Type_I_and_type_II_errors)
* [40 Stats Interviews Problems](https://towardsdatascience.com/40-statistics-interview-problems-and-answers-for-data-scientists-6971a02b7eee)
* [Calculation of Variance: MOSSOM](https://www.mun.ca/biology/scarr/Simplified_calculation_of_variance.html)
* [Practical Statistics for Data Scientists: 50 Essential Concepts](https://www.oreilly.com/library/view/practical-statistics-for/9781491952955/)
* [PSU: STAT 800](https://online.stat.psu.edu/stat800/)
* [Stackexchange: Intuitive explanation for dividing by n−1 when calculating standard deviation?](https://stats.stackexchange.com/questions/3931/intuitive-explanation-for-dividing-by-n-1-when-calculating-standard-deviation)
* [Statistics How To: T-Score vs. Z-Score: What’s the Difference?](https://www.statisticshowto.com/probability-and-statistics/hypothesis-testing/t-score-vs-z-score/)
* [The Art of Statistics](https://www.goodreads.com/book/show/43722897-the-art-of-statistics)

