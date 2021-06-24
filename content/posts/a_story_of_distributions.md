---
title: "Issue 16: A story of distributions"
date: 2020-10-26T18:01:10+02:00
draft: true
description: Normal distribution is well known but not the only one.
---

In this issue, I will talk about different distributions and their use.

TL;DR

- **Binomial distribution** presents the number of successes for different random experiments.
- **Beta distribution** presents the probability of an event. The result is bounded between 0 and 1.
- **Poisson distribution** is helpful when you want to model events that occur during a period of time.
- **Gamma distribution** is used to model continuous probability distributions.

## Binomial distribution

### Discrete or continuous values
Discrete

### Example of use
Conversion on a website.

You convert or you don't. It's a success or a failure. 
This is what binomial distribution is about.

## Beta distribution

### Discrete or continuous values
Continuous

### Example of use
Useful to model the prior probability distribution when doing ABTests with binomial distribution.
There are two parameters: alpha is the successes, beta is the failures

### Links
- [Demo of beta distributions](https://www.youtube.com/watch?v=uTUss9ymzpM&list=PLRogqfr-vZMeW8ZXALh78l28QYnQXziaU)
- [Try to model your own beta distribution](https://homepage.divms.uiowa.edu/~mbognar/applets/beta.html)
- [Overview of Bayesian AB Tests](https://mlinreallife.github.io/posts/bayesian-ab-tests/)

## Poisson distribution

### Discrete or continuous values
Discrete

### Example of use
Goals during a football match. 

The period of time is the match. The number of goals are the events.

### Link
[Better Know a Distribution: The Poisson Distribution](http://lineardigressions.com/episodes/2018/10/21/better-know-a-distribution-the-poisson-distribution)

## Gamma distribution

### Discrete or continuous values
Continuous

### Example of use
Useful to model the prior probability distribution when doing ABTests with binomial distribution.
There are two parameters: alpha is the occurrences for a period of time, beta is the number of periods of time.

### Links

- [Try to model your own beta distribution](https://homepage.divms.uiowa.edu/~mbognar/applets/beta.html)

Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that.
