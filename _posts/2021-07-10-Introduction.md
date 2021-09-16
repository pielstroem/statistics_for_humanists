---
title: 1. Introduction
tags: TeXt
article_header:
  type: cover
  image:
---

## Examining Assumptions through Null Hypotheses - A Short Introduction to Analytical Statistics for (Digital) Humanists

*by Steffen Pielström*

The job of a researcher, probably of almost any researcher in any field, is to improve our knowledge and understanding of the world, to make assumptions in other words, based on observational evidence. In some research fields - natural sciences, psychology, parts of social sciences and, increasingly, in the digitally inclined parts of humanities research - observations often come in the shape of numbers. 

The thing about numbers, albeit their obvious advantages, is that they can be quite tricky to interpret. If an archaeological excavation unearths an adults skeleton only 140 cm in height, what does that say about the people of that period and culture? If a word is used 20% more often in one decade's literary publications as compared to the preceding decade, is that evidence for a linguistic change, or a shift in interests, or more likely just an artifact of probabilistic processes at work when collecting or selecting the texts? How can we relate such numbers to the assumptions they evoke in us? To deal with that type of problem, researchers have developed a set of mathematical tools based on probability theory that is meant to help us examining how well assumptions can be be backed by numerical observations. This set of tools is known as *statistics*.

The aim of this tutorial is give you a very quick (one might even say shallow) introduction into some standard techniques that allow you to examine the plausibility of an observation under particular probabilistic assumptions. If these assumptions render the observed reality implausible, there is little reason to hold on to them. You will do this using the concept of the *null hypothesis*, we will get to know that concept in detail later. One of its main advantages is that there is a number established implementations for standard research problems (e.g. are these 20 measurements fundamentally different from those 20 measurements) known as *statistical tests*. How use some very common of these *off-the-shelf* will be the focus of this tutorial. 



## How to use this tutorial
This tutorial offers two things. First, it offers a very short introduction to the basic concepts of statistical hypothesis testing. The material is therefore arranged in a way motivated by didactic considerations and can be read or worked through from the beginning to the end. Some chapters are longer because they introduce new concepts, others decribe only new procedures that rely on concepts explained in previous chapters. These are naturally a bit shorter. Secondly, if you are sufficiently familiar with the underlying concepts or simply not interested in them you can use the tutorial as a reference and look up specific methods in their respective *HowTo* section. However, if you are really not interested in the concepts of statistics, I would strongly advise against using its methods. simply too many things can be done or interpreted wrong without an understanding of the fundamentals. If you just don't like my explanations, I will hint you to some great books by more talented authors further below.

All the procedures described come with code examples in `Python` and `R`. Both are among the most popular programming languages among digital humanists, and among data scientists as well. Both can do a great job when it comes to number crunching, the primary use we will make of them here. Each of them can outrival the other in one type of task but is more complicated to use in the next. It is basically a matter of taste. Sufficient familiarity with either `Python` or `R` to run the code and to flexibly apply it to the data of your choosing is a prerequisite to work with this tutorial.

### To run the `Python` code
you find in this tutorial, the first thing you require is a distribution of `Python 3.x`. Some operating systems come with a pre-installed `Python` on board, it is however not recommended to use the system's `Python` for statistical work (or other development tasks) as messing around with its packages can interfere with system functionalities that rely on `Python`. The way to go is to install an independent instance and, in the best case, work with virtual environments. I will not dive too deep into this topic as is goes beyond the scope of this tutorial, but those completely new to the topic might consider one of the following solutions widely relied on by people doing data analysis:

- [Anaconda](https://www.anaconda.com/) is a `Python` that can be easily installed on Windows systems (installers for MacOS and Linux are also available), comes with all packages needed for data analysis and even brings its own capabilities for working in virtual environment. 
- On Unix systems, many people rely on [PyEnv](https://github.com/pyenv/pyenv) on create and manage `Python` systems and virtual environments.
- If you are familiar with [Docker](https://www.docker.com/) and unwilling to mess around with the intricacies of managing your `Python` environment, you can simply run your [Machine Learning Workspace](https://github.com/ml-tooling/ml-workspace) in Docker and have everything you need there. Why do you fund everything you need in the 'Machine Learning Workspace'? Well, many machine learning algorithms really are just statistical procedures put a slightly alternative use. 

The next thing to consider is the necessary **`Python` packages**. Being an all-purpose programming language, `Python` provides few of the functionalities we need *out-of-the-box*. But there is a number of great packages providing all the functions and methods we need. If you use [Anaconda](https://www.anaconda.com/) or [Machine Learning Workspace](https://github.com/ml-tooling/ml-workspace), all packages you need are part of the bundle. If not, you should take care to have the following packages installed:
- `numpy`
- `pandas`
- `scipy`

### To run the `R` code
you basically only have to install the `R` language from the [project site](https://cran.r-project.org/mirrors.html). `R` is a language specifically developed for data science applications and it brings all we need with the basic installation. Of the things more comfortable to do with `R` than with `Python`: Getting the system to work in the first place! For convenience's sake you can download the [RStudio IDE](https://www.rstudio.com/).

## What the tutorial will not offer
is instruction on technical basics like system preparation, programming fundamentals and proper data handling in the respective scripting languages. I must kindly ask you to seek out one of the copious sources available elsewhere on these topics.

Apart from that, this tutorial wants to provide a short, practical, hands-on overview. If you aspire thorough text book knowledge about the statistical sciences I would recommend to consult a real text book. There is an abundance of books available, many good ones among them. Some recommendations are given below. 

## Acknowledgements
This tutorial has been deveoped as part of project [CLARIAH-DE](https://www.clariah.de/), which was funded by the German [Federal Ministry of Education and Research](https://www.bmbf.de/bmbf/en/home/home_node.html). Its contents are greatly influenced by Dr. José Calvo Tello, who co-hosted the introductory statistics course for BA students of Digital Humanities at the University of Würzburg with me for several years.

## Further Reading
- *A comprehensible introduction to the concepts and ideas of statistical science:* David Spiegelhalter: The Art of Statistics - Learning from Data. Penguin UK, 2019.
- *A very hands-on introductory book with a focus on implementation in R:* Michael J. Crawley: Statistics - An Introduction Using R. John Wiley and Sons, 2014.
- *A very thorough reference work on statistical computing in R:* Michael J. Crawley: The R Book. John Wiley and Sons, 2012.
- *Another take on statistical science - directly examining the plausibility of a hypothesis with Bayesian methods:* Richard McElrath: Statistical Rethinking - A Bayesian Course with Examples in R and Stan. Chapman and Hall/CRC, 2018.
- *Hands-on introduction to Bayesian statistics in Python:* [Cameron Davidson Pilon: Probabilistic Programming and Bayesian Methods for Hackers. Addison-Wesley Professional, 2015.](https://camdavidsonpilon.github.io/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers/)
