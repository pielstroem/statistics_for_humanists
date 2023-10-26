---
title: 4. Analyzing proportions - null hypothesis and the binomial test
tags: null_hypothesis, p-value, significance, binomial_test, errors, one-sided_testing
article_header:
  type: cover
  image:
---

In the categorial data set I introduced in the past chapter, there were 8 females and 2 males. In research we often deal with proportions like this one. And as often, we have to ask ourselves if that proportion means something. When observing proportions, the important question is often:

> Is this proportion a result of random chance only, or has it been influenced by other effects?

8 Females and 2 males in one group at first glace look like the result of a selection process that preferred one side. With a 5:5 distribution we would be less suspicious. However, if the people in the sample were selected by random chance only and there is a 50% chance for each single person to be female, it is actually not that likely to end up exactly at 5:5. And if you toss a coin 10 times, 8 heads is not an impossible result. So what to do with our suspicion that 8 out of ten is too extreme a result to believe in random chance?

## Null hypothesis and p value

**How likely would that happen by chance?**

In (frequentist) analytical statistics we evaluate our beliefs based on the concept of the **null hypothesis**. This means, we construct a model of reality without the effects we suspect, a model in which our observations are only the result probabilistic processes, i.e. of random chance. A useful null hypothesis 

1. allows to model the generation of the observational data mathematically.

2. It ascribes all variability in the data to random processes.

3. And it usually represents the opposite of the researchers suspicions.

In our example, that is quite easy. If people in the sample were chosen randomly with a 50% chance from the normal population, that process can be simulated by a simple coin toss. Let us first look at an even smaller sample, say 4 people, to go through all the possible combinations. In a group of 4 people, that is a sample with 4 consecutive random selections, we have the following possible combinations:

> ffff, mfff, fmff, ffmf, fffm, mmff, fmmf, ffmm, mffm, fmfm, mfmf, mmmf, mmfm, mfmm, fmmm, mmmm

We have 16 possible combinations, 1 with four females, 4 with 3 females, 6 with 2 females, 4 with 1 female, and 1 with 0 females. What can we learn from this? The probability to have four females in a group of four, if only random chance is to choose, is $\frac{1}{16}$. The probability for any kind of gender homogeneous group is $\frac{1}{16}+\frac{1}{16}=\frac{1}{8}$. The chance to have **at least** three females in the group, that is either three or four, is $\frac{1}{16}+\frac{4}{16}=\frac{5}{16}$, and the chance that either one of the genders is represented by at least three people twice is as large ($\frac{10}{16}$).

I could write all the possible combinations for a group of ten now, find all the probabilities for 8, 9, 10 females and sum them up to get the probability for at least 8 females under random conditions. Fortunately, there are fancy looking formulae that can help us calculate the numbers. Generally, the probability $P_k$ to $k$ or more heads in $n$ coin tosses at a single toss probability of $p$ (0.5 for any normal coin) is:

$$
P_k = \binom nk p^k (1-p)^{n-k}
$$

If we multiply that figure by two, we get the probability for any single one of the genders being represented by at least 8 people. I will spare you the steps (computers are perfectly capable of doing that calculation for us) and tell you that the result is around 0.109 or 10.9%.

What do we know now? We know that under the assumption that our observation is a result of random chance, this proportion or an even more extreme one can be found with a probability of 0.109. This probability is known as the ***p-value**. It is

> **the probability to observe a result at least that extreme, under the assumption that the null hypothesis is true.**

A very important point: the *p*-value is **not** the probability of the null hypothesis. It is not the probability of any assumption/belief/hypothesis to be true! It is an attribute of our observational data given certain assumptions.

Well, and if the reality we observe seems unlikely under a certain assumption, our null hypothesis, our temporarily accepted belief in random chance, this assumption may be flawed and we can see our observation as evidence against it. The concept of null hypothesis and *p*-value can be summed up as

> proiding evidence for influencing effects by demonstrating, that the things we observed very unlikely happened by chance.

The thing you really have to wrap your head around is: After making an observation, we assumed in the first place that something is odd with this proportion, that some mechanism has influenced it. But to examine that, we have to artificially assume randomness, because we can model that mathematically, and demonstrate how unlikely our observation would be under that contrary assumption.

## Significance levels and errors

**How to decide for a belief?**

But what should we believe now with our 10.9% probability under the assumption of randomness? Is that probability small enough to not believe in the null hypothesis? There are two answers to this question and both have nothing to do with mathematics.

The first answer is: that is up to you! At this point we leave the solid ground of mathematics. Mathematics have produced a number, but now we are left to interpretation and there is no single truth.

The second answer: accepted convention in most research communities is to draw the line at 5%. Why 5%? Because it is an accepted convention. No other reason. Period. This 5% figure is called the **significance level** or $\alpha$. If your *p*-value is smaller than $\alpha$, you assume your null hypothesis to be false and the non-random effect you usually suspected in the first place to be true. You are allowed to call the result of the experiment **statistically significant** (which does not necessarily equal *relevant*). Researchers hunt for small *p*-values.

Long story short: 10.9% is not *statistically significant*, the observation provides no acceptable evidence for a non-random selection of people (given $\alpha = 0.05$).

That way, we have created something like a classifier distinguishing true and false null hypotheses. Of course you always have to keep in mind that any classification has an error rate. The probability to reject a null hypothesis, even though it is true, is equal to the significance level. This case is called a **type I error** or **$\alpha$** error, usually leading to a **false positive** study result. And then there is the possibility to accept a false null hypothesis. This is known as the **type II error** or **$\beta$** error, producing a **false negative** study result. The probability of type II errors is hard to quantify.

## Significance tests

This is how null hypotheses are used to evaluate observational data. Researchers have developed null-hypothesis-based analytical procedures for all kinds standard situations that we often encounter in data analysis. These procedures are called **statistical tests** or **significance tests**. The procedure I described above as an introductory example is known as the **binomial test**. Others, like the *t*-test or the *F*-test will be introduced in later chapters. Many more can be found in statistics text books. The problem with these tests is their tendency to lure people into using them as soon as they can squeeze their data into the algorithm in any way possible. They are an easy, out-of-the-box solution that can produce impressive *p*-values without much reflection on the user's part. The advantage of significance tests is their accessibility. There are numerous implementations in programming libraries and even in point-and-click software aaplications. 

## One-sided and two-sided testing

In many tests including the binomial test there are two slightly alternative ways to formulate and model your analyis. In our example we could ask:

> How likely is it to observe 8 or more **people of one gender** (either 8+ females or 8+ males) in my sample under random conditions?

or

> How likely is it to observe 8 or more **females** in my sample under random conditions?

Obviously, in the fist case we get a higher probability, i.e. a higher *p*-value. The first case is called a **two-sided** or **two-tailed** test design, which usually is the default option, the second case as **one-sided** or **one-tailed** test.


## How to do the binomial test

### in Python
we can use a function from the `scipy` libarary to make the binomial test.
```
from scipy import stats
```

The function requires the *number of successes* and the overall *sample size* (*n*). For example, to test if 2 out of 10 is a statistically significant proportion, we compute: 
```
stats.binom_test(2, 10)
```


```
0.10937500000000003
```

The test function returns a *p* value of 0.109. This means, assuming the result was produced by pure chance, the test shows a 10.9% propability to get a result like this or more extreme. At a significance level of 5%, we do **not** count this result as statistically significant. According to the evidence, we should therefore stay with the null hypothesis: there is no systematic influnence, the observations are well explained by pure chance.

By default, the function assumes the base **probability for a single trial** to be 50% (`p = 0.5`), but you can specify alternarnative  values. For example
```
stats.binom_test(2, 10, p=0.75)
```


```
0.00041580200195312505
```

With the altered single success probability, we get a significant *p* value.


Furthermore the function makes a two-sided test by default, i.e. it calculates the probability for any combination with 3 or less instances of one category. That includes all combinations with no more than two **or** more than seven successes. We can also make a one-sided test, asking for specifically the probabilty of no more than 2 successes.
```
stats.binom_test(2, 10, alternative='less')
```


```
0.054687500000000014
```

### in R
there is a function requiring the *number of successes* and the overall *sample size*. For example, to test if 2 out of 10 is a statistically significant proportion, we compute: 
```
binom.test(2, 10)
```


```
	Exact binomial test

data:  2 and 10
number of successes = 2, number of trials = 10, p-value = 0.1094
alternative hypothesis: true probability of success is not equal to 0.5
95 percent confidence interval:
 0.02521073 0.55609546
sample estimates:
probability of success 
                   0.2
```

If you have looked at the `Python` code above before, you will realize that the output of the `R` function is a bit more detailed. This is true for the majority of implemented statistical tests.

The test function returns a *p* value of 0.109. This means, assuming the result was produced by pure chance, the test shows a 10.9% propability to get a result like this or more extreme. At a significance level of 5%, we do **not** count this result as statistically significant. According to the evidence, we should therefore stay with the null hypothesis: there is no systematic influnence, the observations are well explained by pure chance.

By default, the function assumes the base **probability for a single trial** to be 50% (`p = 0.5`), but you can specify alternarnative  values. For example
```
binom.test(2, 10, p = 0.75)
```


```
	Exact binomial test

data:  2 and 10
number of successes = 2, number of trials = 10, p-value = 0.0004158
alternative hypothesis: true probability of success is not equal to 0.75
95 percent confidence interval:
 0.02521073 0.55609546
sample estimates:
probability of success 
                   0.2 
```

With the altered single success probability, we get a sginificant *p* value.


Furthermore the function makes a two-sided test by default, i.e. it calculates the probability for any combination with 2 or less instances of one category. That includes all combinations with no more than two **or** more than seven successes. We can also make a one-sided test, asking specifically for the probabilty of no more than 2 successes.
```
binom.test(2, 10, alternative = "less")
```


```
	Exact binomial test

data:  2 and 10
number of successes = 2, number of trials = 10, p-value = 0.05469
alternative hypothesis: true probability of success is less than 0.5
95 percent confidence interval:
 0.0000000 0.5069013
sample estimates:
probability of success 
                   0.2 
 
```
