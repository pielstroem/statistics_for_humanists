---
title: 3. Examining assumptions through null hypotheses with the binomial test
tags: TeXt
article_header:
  type: cover
  image:
---

## Null hypothesis and p value

**How likely would that happen by chance?**

## Significance levels

**How to decide for a belief?**

## One-sided and two-sided testing 

## How to do the binomial test

### in Python
we can use a function from the `scipy` libarary to make the binomial test.
```
from scipy import stats
```

There is a function requiring the *number of successes* and the overall *sample size* (*n*). For example, to test if 3 out of 10 is a statistically significant proportion, we compute: 
```
stats.binom_test(3, n=10)
```


```
0.3437499999999999
```

The test function returns a *p* value of 0.3438. This means, assuming the result was produced by pure chance, the test shows a 34.38% propability to get a result like this or more extreme. A a significance level of 5%, wo do **not** count this result as statistically significant. According to the evidence, we should therefore stay with the null hypothesis: there is no systematic influnence, the observations are well explained by pure chance.

By default, the function assumes the base **probability for a single trial** to be 50% (`p = 0.5`), but you can specify alternarnative  values. For example
```
stats.binom_test(3, n=10, p=0.75)
```


```
0.003505706787109374
```
With the altered single success probability, we get a sginificant *p* value.


Furthermore the function makes a two-sided test by default, i.e. it calculates the probability for any combination with 3 or less instances of one category. That includes all combinations with no more than three **or** more than seven successes. We can also make a one-sided test, asking for specifically the probabilty of no more than 3 successes only.
```
stats.binom_test(3, n=10, alternative='less')
```


```
0.17187499999999994
```

### in R
there is a function requiring the *number of successes* and the overall *sample size*. For example, to test if 3 out of 10 is a statistically significant proportion, we compute: 
```
binom.test(3, 10)
```


```
	Exact binomial test

data:  3 and 10
number of successes = 3, number of trials = 10, p-value = 0.3438
alternative hypothesis: true probability of success is not equal to 0.5
95 percent confidence interval:
 0.06673951 0.65245285
sample estimates:
probability of success 
                   0.3 

```

The test function returns a *p* value of 0.3438. This means, assuming the result was produced by pure chance, the test shows a 34.38% propability to get a result like this or more extreme. A a significance level of 5%, wo do **not** count this result as statistically significant. According to the evidence, we should therefore stay with the null hypothesis: there is no systematic influnence, the observations are well explained by pure chance.

By default, the function assumes the base **probability for a single trial** to be 50% (`p = 0.5`), but you can specify alternarnative  values. For example
```
binom.test(3, 10, p = 0.75)
```


```
	Exact binomial test

data:  3 and 10
number of successes = 3, number of trials = 10, p-value = 0.003506
alternative hypothesis: true probability of success is not equal to 0.75
95 percent confidence interval:
 0.06673951 0.65245285
sample estimates:
probability of success 
                   0.3 

```
With the altered single success probability, we get a sginificant *p* value.


Furthermore the function makes a two-sided test by default, i.e. it calculates the probability for any combination with 3 or less instances of one category. That includes all combinations with no more than three **or** more than seven successes. We can also make a one-sided test, asking for specifically the probabilty of no more than 3 successes only.
```
binom.test(3, 10, alternative = "less")
```


```
	Exact binomial test

data:  3 and 10
number of successes = 3, number of trials = 10, p-value = 0.1719
alternative hypothesis: true probability of success is less than 0.5
95 percent confidence interval:
 0.0000000 0.6066242
sample estimates:
probability of success 
                   0.3 
```
