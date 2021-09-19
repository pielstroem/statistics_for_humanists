---
title: 2. Describing and summarizing numerical observations
tags: levels_of_measurement, sample_size, mean, median, mode, standard_deviation, quantiles
article_header:
  type: cover
  image:
---

We will begin with a quick overview to some important concepts of data description and summarization. Descriptive statistics is not a focus of this tutorial and I will concentrate on concepts necessary to understand the later chapters.

## The level of measurement

**What type of data do I have?**

When describing observational data, the first aspect is the type of data we have observed. If we measure the body height in centimeter in a group of 10 people, the result may look like this:

> 156, 188, 190, 176, 166, 160, 182, 171, 185, 169

If we ask the same people for their gender, the result might look like this:

> female, female, female, female, female, male, female, female, male, female

The obvious difference is that one data set is **numerical** while the other is **categorical**, i.e. it contains instances of categories, that can be alternatively expressed as a table of counts:

> female: 8
> male: 2

The type of data or **level of measurement** as it is usually called in text books is a concept closely related to the *data types* distinguished in programming languages. In `Python` for example, the first set could be handled as a `list` of `integer`, the second as a `list` of `strings`.

The majority of statistics text books agrees on categorizing data sets according to a system of three levels of measurement.

The **nominal** level describes plain categorical data. Each observation is described as an instance of a category, like *female* and *male*.

*Numerical* data belongs to the so-called **interval** level.  

If the instances of observation are clearly distinct and categorical, but subject to an obvious ordering hierarchy, statisticians ascribe the data to the **ordinal** level. 

The ordinal level usually is the most complicated to explain. Here, your observations are categorical like in the nominal level, they can be ranked like in the interval level, but unlike interval data they are not numbers that can be meaningfully used in mathematical operations. A good example is the German school mark system. In German schools, marks are expressed in numbers ranging from 1 (*very good*) to 6 (*nice try, but you got nothing right*). The marks are expressed in numbers, but these numbers describe distinct categories. They are clearly ranked - 2 is better than a 4 - but a 4 does not describe a performance *twice as bad as a 2*.

## Sample size

**How many observations do I have?**

The **sample size**, i.e. the number if observations is probably the most important auxiliary description of a data set. It hardly tells anything about the subject of an observation (how tall are the people in the data set?), but it tells a lot about the reliability of summaries and conclusions. And it is the basis for many other calculations. In formulas, we usually find it abbreviated as $N$ or $n$.

## Mean, median and mode

**How can I summarize into one representative number?**

Probably the most requested application of descriptive statistics is to give a single value representative for a set of observations. The mot popular way to do that for numerical data is the **arithmetic mean** ($\bar{x}$), colloquially often referred to simply as the *mean* or the *average*. It is calculated by dividing the sum of all measurements by the number of observations:

$$
\bar{x} = \frac{\sum_{i=1}^N x_i}{N}
$$

with $x$ representing the observation value and $N$ sample size.

An often very useful alternative to the arithmetic mean is the **median**. The idea of the median is mathematically very simple: you order all the numbers of a data set according to their value and find the one right in the center. If we do that for the body height data, we get:

> 156, 160, 166, 169, **171**, **176**, 182, 185, 188, 190

Unfortunately now have two numbers in the center, because there is an even number of observations. The simple solution to that problem is to calculate the arithmetic mean of these two numbers and get a median of *173.5*.

The arithmetic mean of the same data set is *174.3*. Now, which statistic should you use? In many cases, they are very close. And if they are close, it is more or less a matter of personal preference. However, more people are familiar with the arithmetic mean, and it is more useful for follow-up mathematical operations, so I would recommend to report the arithmetic mean if it makes little to no difference. If there is a marked difference between mean and median, this is an indicator for extreme values at the high or at the low end of the measurements in the data set. Mean values can be influenced by single extreme values, median values not so much. Therefore you should report the median in that case. 

Obviously, we cannot compute means and medians for purely categorical data. For categorical observations, we can compute the **mode**, which is simply the category we observed most often. So the mode of the categorical set shown above would be *female*.

## Standard deviation and quantiles

**How can I describe variability?**

One representative value is nice, but you often also want to know about the variability in your data. For numerical data, the simplest way to report variability is to report the **range** of the values, i.e. the highest and the lowest value. However, in large data sets with some very extreme outliers this often is not the most useful information.

The most popular alternative is to look at how much the observed values deviate from the arithmetic mean. The individual differences can be squared to treat negative and positive deviations equally, summed and divided by sample size to get what we call the **variance** ($s^2$) of the data set:

$$
s^2 = \frac{1}{N} \sum_{i=1}^N (x_i - \bar{x})^2
$$

Variance calculation can give us values that are very large compared to the mean of the data set. But we can "reduce" it to the scale of the actual data by taking the square root afterwards. The resulting value is called **standard deviation** ($s$):

$$
s = \sqrt{s^2} = \sqrt{\frac{1}{N} \sum_{i=1}^N (x_i - \bar{x})^2}
$$

In programming languages, some implementations of standard deviation use *degrees of freedom*, that is sample size minus one, instead of sample size as a denominator. Therefore, when using different programming libraries to calculate variance or standard deviation for the same data set, results can be slightly different. However, with sufficiently large sample sizes that is usually not a serious problem.

A numerical data set without one-sided extremes can be well described by a combination of arithmetic mean (the "typical" value), standard deviation (variability) and sample size.

But data sets can be heavy on the upper or the lower end of the spectrum and that is why arithmetic means are not always the best choice. Luckily, the concept of the median described above can be generalized to derive descriptions for data variability too. The generalization of the idea behind the median is known as the **quantile**.

What is a quantile? Well, if we order all values by size, we can identify the value in the center, the one at half distance (50%) between the smallest and the largest, to get the median. 50% Of all measurements are smaller than the median. The other 50% are larger. But we can also identify a value that is 30% on the way from smallest to largest. 30% Of the measurements have (equal or) smaller values than this one. In our example:

> 156, 160, **166**, 169, 171, 176, 182, 185, 188, 190

This value (166 cm) is called the **30% quantile** of the data set. Or, to confuse readers, it is also known as the **30th percentile**. To add to confusion, there is also the term **quartile** referring the quantiles/percentiles that divide the data set into four equally large parts. The following overview should clarify the relations between the terms:

- 0% quantile = 0th quartile = smallest value
- 25% quantile = 1st quartile
- 50% quantile = 2nd quartile = median
- 75% quantile = 3rd quartile
- 100% quantile = 4th quartile = highest value

The 1st and 3rd quartile are often referred to, because the central 50% of all measurements are between these values. To report variability in a addition to a median value, researchers often use the **interquartile range**, that is the difference between the 1st and 3rd quartile.


## How to do descriptive statistics

### in Python

There are multiple libraries in `Python` that provide functions for descriptive statistics. To keep it simple, we will stick mostly `numpy` here.
```
import numpy as np
```

Now we can create a `numpy` array with our example data.
```
height = np.array([156, 188, 190, 176, 166, 160, 182, 171, 185, 169])
```

#### The sample size
of that array can simply be indicated with:
```
len(height)
```


```
10
```

#### Mean and median
The **arithmetic mean** be computed with the following command:
```
np.mean(height)
```


```
174.3
```

To get the **median** we type:
```
np.median(height)
```


```
173.5
```

#### Maximum and minimum values
can be computed using 
```
np.max(height)
```


```
190
```

and
```
np.min(height)
```


```
156
```

#### Variance and standard deviation
are calculated with the functions
```
np.var(height)
```


```
125.81000000000002
```

and
```
np.std(height)
```


```
11.21650569473399
```

#### For quantiles
there is a function that takes a proportion of 1 instead of percentage as an argument (e.g. *0.3* instead of *30%*). So we can reproduce the median using
```
np.quantile(height, 0.5)
```


```
173.5
```

or compute the 25% quantile with
```
np.quantile(height, 0.25)
```


```
166.75
```

The **interqunatile range** can be either calculated
```
np.quantile(height, 0.75) - np.quantile(height, 0.25)
```


```
17.5
```

or you can resort to the `scipy` library:
```
from scipy import stats
```

and use the function
```
stats.iqr(height)
```


```
17.5
```

### in R

Our example data sets can be implemented as `R` variables with the following lines of code:

```
height = c(156, 188, 190, 176, 166, 160, 182, 171, 185, 169)
```

and
```
gender = c("female", "female", "female", "female", "female", "male", "female", "female", "male", "female")
```

#### The sample size
of a vector can simply be indicated with:
```
length(height)
```


```
[1] 10
```

#### Mean, median and mode
The **arithmetic mean** is computed with the following command:
```
mean(height)
```


```
[1] 174.3
```

To get the **median** we type:
```
median(height)
```


```
[1] 173.5
```

There is no dedicated function to compute the **mode**. But we can easily find it using the `table()` function.
```
table(gender)
```


```
gender
female   male 
     7      3 
```

#### Maximum and minimum values
can be computed using 
```
max(height)
```


```
[1] 190
```

and
```
min(height)
```


```
[1] 156
```

#### Variance and standard deviation
are calculated with the functions
```
var(height)
```


```
[1] 139.7889
```

and
```
sd(height)
```


```
[1] 139.7889
```

#### For quantiles
there is a function that takes a proportion of 1 instead of percentage as an argument (e.g. *0.3* instead of *30%*). So we can reproduce the median using
```
quantile(height, 0.5)
```


```
  50% 
173.5
```

or compute the 25% quantile with
```
quantile(height, 0.25)
```


```
  25% 
166.75
```

The **interqunatile range** can be computed directly with the function
```
IQR(height)
```


```
[1] 17.5
```
