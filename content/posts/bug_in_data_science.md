---
title: "A bug in data science"
date: 2020-12-13T17:01:10+02:00
draft: false
description: Bugs in predictive systems are most of the time silent. Don't expect your users to raise their hands saying something is wrong. That won't happen
images: [path_learn.jpg] 
---

TL;DR:

Bugs in predictive systems are most of the time silent. Don't expect your users to raise their hands saying something is wrong. That won't happen. 

That's life!

![Learning path](/path_learn.jpg)

**Use monitoring instead of waiting from your end users!**

# The story

Let's suppose you train your model in production on the 10th of November, you have an AUC of 0.81.

The days after, you do some modifications in the data preparation and around the model. You have a bunch of very small modifications.

You decide to retrain in production on the 26th of November. You have a drop in your AUC. Now, you have 0.65. :confused:. 

This bug is silent. The user might never notice it :anguished:.

# The solutions

## Fail loudly

First of all, this bug is silent. Make your system fail loudly. 
Add monitoring. Add alerts.

You can check your AUC. If your AUC is below X, you send an email to your data scientists.

## Retrain every time you do a modification

When you do a modification, even a small one, run immediately your model with real data to be sure that everything is okay.
You can launch automatically a model after having done a modification in your codebase and check the results with alerts.

It's like a unit test for data science. 

**Even a small modification can break everything.**

## Version your data

The drop can be due to your data. You will have to travel the time to understand what happened.
Then you have to be able to get the current state of the data for each day of November.
If your data is versioned or you have a quick way to get the current state of your previous data, it would be much easier.

Then, version your data. Reproducibility is crucial for predictive systems. A way to get it is to be able to travel the time through your data.

## Monitor your system in real life

Don't wait for your next retraining to be sure that everything is okay in production.

You can check the results of your predictions in real life. You can evaluate if you have an online model drift. You can also evaluate if your data are evolving. It will impact your model sooner or later.

# Conclusion

My 4 pieces of advice would be:
- Make predictive systems fail loudly. 
- Version your data.
- Retrain every time you have a modification.
- Monitor your system in production.

Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that.
