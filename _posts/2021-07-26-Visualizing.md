---
title: 3. Basics of data visualization
tags: histogram, scatterplot, boxplot, barplot
article_header:
  type: cover
  image:
---

Our brains are probably not meant to process many numbers at once. Working with data therefore becomes a lot more intuitive, at least to many people and I count myself among them, if you are able to look at it in as many stages and through as many angles as possible. And by looking I do not refer to looking at rows and rows of numbers, I mean actual visual input that can convey information about properties of the data set. Therefore, it is hard to talk about statistics without talking about data visualization. Visualizations can tell us things about our data descriptive statistics will not tell us so easily, and often they allow us to *see* what we need to know much more quickly. 
Visualizations are by themselves a vast topic, and not the focus of this tutorial. But I will briefly introduce the most common visualizations here and present the basics needed for the first encounters with statistical thinking.

## The histogram

**A single continuous variable**

The *histogram* is a common way to visualize a single series of continuous data, or a set of numbers, if you prefer to call it that. The basic idea of a histogram is to divide the range of possible numbers into equally-sized chunks, usually called ***bins***, and to count the number of measurements falling into each of these bins. The range of measurements constitutes the *X* axis in the visualization. The length of a bar in the *Y* direction indicates how many observations are in the corresponding bin (Fig. 1).

![Figure 1: Histogram](/statistics_for_humanists/assets/images/histogramR2.png)

*Figure 1: Example histogram*

Somehow, a histogram is transforming a continuous variable into a number of discrete categories - the bins - and the counts for each category. It can tell us a lot about the *shape* of a data set. Is it symmetrical or skewed, i.e. are there more extreme values to one side that to the other? Does it seem to have a single peak, i.e. one most likely value or several? How wide is the range of rather likely values?

There are two caveats when dealing with histograms. First, they are not useful for **small sample sizes**. Histograms show you how often measurement fall into each of the bins. If many of the bins are empty because there are simply not enough measurements to fill them, you will not get a visualization you can learn something from. 

The other caveat is the **number of bins**. Too few bins will convey little information about the shape of the data, too large a number will result in many bins being empty. Some software implementations have default settings based on algorithms that try to find an optimal number of bins for a given data set. 

## The scatterplot

**Two continuous variables**

are visualized in a *scatterplot*. This is the classical diagram with points that have *X* and *Y* coordinates you probably know from school. One convention in experimental research: if there is one variable you are manipulating while observing the other, the manipulated or **independent variable** goes onto the *X* axis, whereas the observed or **dependent variable** goes onto the *Y* axis (Fig. 2).

![Figure 2: Scatterplot](/statistics_for_humanists/assets/images/scatterplotR2.png)

*Figure 2: Example scatterplot*

## The box-whisker plot

**Continuous vs categorical**

If you have multiple categories with a set of continuous measurements belonging to each, you could plot a histogram for each of the categories and compare them. Alternatively, you use the **box-whisker plot** or **boxplot** to put multiple series of measurements into one single visualization. An example is shown in Fig. 3.

![Figure 3: Boxplot](/statistics_for_humanists/assets/images/boxplotR2.png)

*Figure 3: Example boxplot*

In a boxplot, a thick bar indicates the **median** for each series. The range from the **25% quantile** to the **75% quantile** is represented by a box. This box contains the central 50% of the values. The long *whiskers* on each side of the box reach to the **minimum** and **maximum** values respectively. The boxplot therefore conveys a relatively precise idea about the center and variability of each category. It contains a little less information than a series of histograms, but it is very useful to compare several categories. 

## The barplot

**Continuous vs categorical - one number per category**

If there is only one number associated with each of multiple categories - this number may well be just the number of instances or any other kind of numerical measurement - the most common visualization is the barplot. Here, each category is represented by a bar, the length of this bar indicates the measurement for the category (Fig. 4).

![Figure 4: Boxplot](/statistics_for_humanists
/assets/images/barplotPy2.png)

*Figure 4: Example barplot*

What is the difference between a barplot and a histogram? Well, they are certainly related and they can look kind of similar, but conceptually they serve completely different purposes. The histogram, as described above, is used to visualize the distributional shape of a single, continuous series. In a barplot on the contrary, the variable on the *X* axis is a discrete one, and each category of this variable is combined with a single numerical measurement on the *Y* axis.

## How to do basic visualizations

### in Python

Many libraries in `Python` allow you to do visualizations. `matplotlib` Is probably the most basic option, and the one many other libraries are built on. For our current needs it will suffice. For data handling we will need `numpy` again.
```
import matplotlib.pyplot as plt
import numpy as np
```


#### Histogram

To plot a pretty histogram, we use the life spans (age at death) of Spanish novelists from the 19th and 20th century as example data:

```
life_span = np.array([48, 68, 70, 60, 77, 68, 58, 58, 73, 81, 
77, 70, 49, 85, 64, 71, 66, 61, 47, 98, 52, 66, 78, 56, 80, 48,
63, 62, 47, 82, 46, 65, 62, 80, 52, 51, 85, 67, 72, 84, 94, 51,
82, 75, 83, 71, 90, 80, 55, 59, 51, 59, 55, 66, 56, 73, 66, 55,
54, 59, 73, 63, 88, 61, 78, 78, 42, 48, 41, 75, 83, 88, 85, 81,
86, 62, 79, 52, 42, 66, 34, 85, 51, 72, 84, 92, 73, 60, 88, 81,
36, 54, 71, 70, 72, 65, 75, 74, 60, 74, 59, 39, 92, 68, 77, 36,
61, 83, 32, 65, 84, 64, 65, 60, 61, 90, 68, 53, 96, 81, 103, 60,
65, 84, 71, 86, 68, 86, 72, 70, 80, 49, 53])
```

Now we have to tell `matplotlib` to turn this data series into a histogram, and show it.

```
plt.hist(life_span)
plt.show()
```

![Histogram](/statistics_for_humanists/assets/images/histogramPy1.png)

This is the distribution of life spans. Without descriptive statistics we can see on an instant that a vast majority of the authors in the data set died at ages between 50 and 90 years.

Among scientists it is custom to give labels to axes, so let us turn this output into something presentable.

```
plt.hist(life_span)
plt.xlabel('life span (years)')
plt.ylabel('Frequency')
plt.show()
```

![Histogram](/statistics_for_humanists/assets/images/histogramPy2.png)


#### Scatterplot

For a scatterplot we will need second variable, another set of numbers. Let us add the year of death for each of the Spanish authors.

```
year_of_death = np.array([1885, 1897, 1889, 1882, 1895, 1896,
1893, 1891, 1906, 1905, 1920, 1921, 1901, 1938, 1915, 1923, 1922,
1928, 1909, 1971, 1916, 1943, 1955, 1912, 1939, 1908, 1936, 1936,
1922, 1953, 1910, 1911, 1936, 1921, 1899, 1913, 1951, 1940, 1936,
1956, 1967, 1930, 1962, 1963, 1964, 1946, 1966, 1963, 1940, 1943,
1936, 1945, 1936, 1948, 1941, 1953, 1948, 1940, 1932, 1938, 1952,
1942, 1975, 1949, 1963, 1972, 1939, 1947, 1945, 1985, 1983, 1975,
1976, 1975, 1983, 1963, 1969, 1947, 1940, 1964, 1936, 1988, 1952,
1954, 1981, 1978, 1960, 1940, 1983, 1964, 1924, 1954, 1933, 1936,
1945, 1929, 1947, 1947, 1939, 1954, 1947, 1925, 1982, 1955, 1958,
1931, 1959, 1978, 1933, 1969, 1977, 1966, 1968, 1951, 1963, 1994,
1977, 1962, 1994, 1982, 2009, 1957, 1965, 1987, 1988, 1989, 1977,
2003, 1966, 1936, 1962, 1916, 1959])
```

Scatterplots can be easily drawn with the `scatter()` function.

```
plt.scatter(year_of_death, life_span)
plt.show()
```

![Scatterplot](/statistics_for_humanists/assets/images/scatterplotPy1.png)

This example quite nicely shows us how a scatterplot can give you insights to data, provoke interpretations and lead to new hypotheses. What we probably see here is the increase in life expectancy during the recent century, and the adverse effects of the Spanish civil war...

Now the pretty version:

```
plt.scatter(year_of_death, life_span)
plt.xlabel('year of death')
plt.ylabel('life span (years)')
plt.show()
```

![Scatterplot](/statistics_for_humanists/assets/images/scatterplotPy2.png)

#### Boxplot

Boxplots are used to compare sets of numerical measurements between categories. Let us compare life spans in female and male authors. As many historical data sets, this one is also extremely gender-biased. Only 7 of 133 authors are females. To even the odds a little I will only use a random sample of 7 male authors. 

```
female = np.array([58, 70, 78, 54, 85, 96, 84])
male = np.array([51, 77, 67, 51, 62, 68, 84])
```

For the `plt.boxplot()` function, the two sets should be combined into a single list of two series.

```
data = [female, male]
```

Now, we can produce the plot.

```
plt.boxplot(data)
plt.show()
```

![Boxplot](/statistics_for_humanists/assets/images/boxplotPy1.png)

To make it pretty we must, among other things, specify labels for the categories.

```
plt.boxplot(data, labels=['female', 'male'])
plt.xlabel('author gender')
plt.ylabel('life span (years)')
plt.show()
```

![Boxplot](/statistics_for_humanists/assets/images/boxplotPy2.png)

#### Barplot

With the barplot, we can look at the life spans of the individual female authors now. But first we need their names as labels for the bars.

```
names = np.array(['Castro', 'Bazan', 'Espina', 'Burgos', 'León', 'Chacel', 'Mulder'])
```

Now, we can draw the figure.

```
plt.bar(names, female)
plt.show()
```

![Barplot](/statistics_for_humanists/assets/images/barplotPy1.png)

And with axis labels, it looks like this.

```
plt.bar(names, female)
plt.xlabel('author')
plt.ylabel('life span (years)')
plt.show()
```

![Barplot](/statistics_for_humanists/assets/images/barplotPy2.png)


### in R

#### Histogram

To plot a pretty histogram, we use a data set cotaining life spans (age at death) of Spanish novelists from the 19th and 20th century as example data:

```
life_span = c(48, 68, 70, 60, 77, 68, 58, 58, 73, 81, 77, 70, 
49, 85, 64, 71, 66, 61, 47, 98, 52, 66, 78, 56, 80, 48, 63, 62,
47, 82, 46, 65, 62, 80, 52, 51, 85, 67, 72, 84, 94, 51, 82, 75,
83, 71, 90, 80, 55, 59, 51, 59, 55, 66, 56, 73, 66, 55, 54, 59,
73, 63, 88, 61, 78, 78, 42, 48, 41, 75, 83, 88, 85, 81, 86, 62,
79, 52, 42, 66, 34, 85, 51, 72, 84, 92, 73, 60, 88, 81, 36, 54,
71, 70, 72, 65, 75, 74, 60, 74, 59, 39, 92, 68, 77, 36, 61, 83,
32, 65, 84, 64, 65, 60, 61, 90, 68, 53, 96, 81, 103, 60, 65, 84,
71, 86, 68, 86, 72, 70, 80, 49, 53)
```

Plotting a histogram for a vector of numbers is quite straightforward: with the `hist()` function.

```
hist(life_span)
```

![Histogram](/statistics_for_humanists/assets/images/histogramR1.png)

This is the distribution of life spans. Without descriptive statistics we can see on an instant that a vast majority of the authors in the data set died at ages between 50 and 90 years.

There are two minor improvements I would recommend for this graph. It is custom among scientists to mention the unit of any measurement indicated in a visualization. And it is not custom to have a title on top of the graphic, even though some functions produce them by default. The reason is that figures in printed publications ought to have a caption below anyway that contains that kind of information.

```
hist(life_span,
	xlab = 'life span (years)',
	main = NULL)
```

![Histogram](/statistics_for_humanists/assets/images/histogramR2.png)


#### Scatterplot

For a scatterplot we will need second variable, another set of numbers. Let us add the year of death for each of the Spanish authors.

```
year_of_death = c(1885, 1897, 1889, 1882, 1895, 1896, 1893, 1891,
1906, 1905, 1920, 1921, 1901, 1938, 1915, 1923, 1922, 1928, 1909,
1971, 1916, 1943, 1955, 1912, 1939, 1908, 1936, 1936, 1922, 1953,
1910, 1911, 1936, 1921, 1899, 1913, 1951, 1940, 1936, 1956, 1967,
1930, 1962, 1963, 1964, 1946, 1966, 1963, 1940, 1943, 1936, 1945,
1936, 1948, 1941, 1953, 1948, 1940, 1932, 1938, 1952, 1942, 1975,
1949, 1963, 1972, 1939, 1947, 1945, 1985, 1983, 1975, 1976, 1975,
1983, 1963, 1969, 1947, 1940, 1964, 1936, 1988, 1952, 1954, 1981,
1978, 1960, 1940, 1983, 1964, 1924, 1954, 1933, 1936, 1945, 1929,
1947, 1947, 1939, 1954, 1947, 1925, 1982, 1955, 1958, 1931, 1959,
1978, 1933, 1969, 1977, 1966, 1968, 1951, 1963, 1994, 1977, 1962,
1994, 1982, 2009, 1957, 1965, 1987, 1988, 1989, 1977, 2003, 1966,
1936, 1962, 1916, 1959)
```

Scatterplots can be easily drawn with the generic `plot()` function.

```
plot(year_of_death, life_span)
```

![Scatterplot](/statistics_for_humanists/assets/images/scatterplotR1.png)

This example quite nicely shows us how a scatterplot can give you insights to data, provoke interpretations and lead to new hypotheses. What we probably see here is the increase in life expectancy during the recent century, and the adverse effects of the Spanish civil war...

However, before we show this visualization to anybody, we want to add some minor improvements. Both axes are already labeled, which is nice, but the life span is lacking information on the time unit. Yes, it is obvious, but - as I said before - good scientific practice requires us to name units explicitly.

```
plot(year_of_death, life_span,
	xlab = 'year of death',
	ylab = 'life span (years)')
```

![Scatterplot](/statistics_for_humanists/assets/images/scatterplotR2.png)

#### Boxplot

Boxplots are used to compare sets of numerical measurements between categories. The data set about Spanish novelists also contains data on author gender. Let us compare life spans in female and male authors. As many historical data sets, this one is also extremely gender-biased. Only 7 of 133 authors are females. To even the odds a little I will only use a random sample of 7 male authors. 
```
female = c(58, 70, 78, 54, 85, 96, 84)
male = c(51, 77, 67, 51, 62, 68, 84)
```


```
boxplot(female, male)
```

![Boxplot](/statistics_for_humanists/assets/images/boxplotR1.png)

Now the same in pretty:

```
boxplot(female, male,
	range = 0,
	names = c('female', 'male'),
	xlab = 'author gender',
	ylab = 'life span (years)')
```

![Boxplot](/statistics_for_humanists/assets/images/boxplotR2.png)

#### Barplot

With the barplot, we can look at the life spans of the individual female authors now.

```
barplot(female)
```

![Barplot](/statistics_for_humanists/assets/images/barplotR1.png)

This function however gives us an output that is not too informative by default. You definitely want to add some names for the categories. The names of the female novelists are:

```
names = c('Castro', 'Bazan', 'Espina', 'Burgos', 'León', 'Chacel', 'Mulder')
```

And then, of course, we want proper axis labels.

```
barplot(female,
	names = names,
	xlab = 'author',
	ylab = 'life span (years)')
```

![Barplot](/statistics_for_humanists/assets/images/barplotR2.png)