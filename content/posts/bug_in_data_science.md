---
title: "A bug in data science"
date: 2020-11-09T07:01:10+02:00
draft: true
---

TL;DR:

Bugs in predictive systems are most of the time silent. Don't expect your users to raise their hands saying something is wrong. That won't happen :simple_smile:. 

That's life!

![That's life](/mohamed-nohassi-odxB5oIG_iA-unsplash.jpg)

<span>Photo by <a href="https://unsplash.com/@coopery?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Mohamed Nohassi</a> on <a href="https://unsplash.com/s/photos/life?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>

**Use monitoring instead of waiting from your end users!**

# The story

Let's suppose you train your model on the 10th of November, you have an AUC of 0.75.

The days after, you do some modifications in the data preparation and around the model. You have a bunch of small modifications.

You decide to retrain on the 26th of November. You have a drop in your AUC. Now, you have 0.65. :confused:. 

This bug is silent. The user might never notice it. They might think that the predictions are weird and stop using them :anguished:.

# The solutions

## Fail loudly

First of all, this bug is silent. Make your system fail loudly. 
Add monitoring. Add alerts.

You can check you AUC. If your AUC is below 0.7 for example, you send an email to your members or in your chat tool.

## Retrain every time you do a modification

When you do a modification that can impact your model, run your model to be sure that everything is okay.
You can launch automatically a model after having done a modification in your codebase and check the results with alerts.

## Version your data

The drop can be due to your data. Anyway, you will have to travel the time to understand what happened.
Then you have to be able to get the current state of the data for each day of November.
If your data is versioned or you have a quick way to get the current state of your previous data, it would be much easier.

Then, version your data. Reproducibility is crucial for predictive systems. A way to get it is to be able to travel the time through your data.

# Conclusion

My 3 pieces of advice would be:
- Make predictive systems fail loudly. 
- Version your data.
- Retrain every time you have a modification.

Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that.
