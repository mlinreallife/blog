---
title: "Issue 4: Resources to get an overview of a machine learning project"
date: 2020-11-09T07:01:10+02:00
draft: true
description: It's not easy to start when doing machine learning. This is why I would like to highlight some useful resources to get an idea of what a data science project looks like from end to end.
---

It's not easy to start when doing machine learning. This is why I would like to highlight some useful resources to get an idea of what a data science project looks like from end to end.

I also wanted to put forward a new tool to do data monitoring and tell you a story about debugging silent bugs in data science.

# [Machine learning engineering by Andriy Burkov](http://www.mlebook.com/wiki/doku.php)

A book about machine learning in real life. From data preparation to deployment, you will learn how to handle a real data science project.

As a summary, I can highlight 2 ideas I like:
 - Validating your model is not only about evaluating your accuracy. You also must be sure that your model is ethical and will be appreciated and used by your end-users.
 - Feature engineering is important. Test it intensively.

# [ML Production pipelines: a classification example by Adriana Menegozzo](https://databricks.com/session_eu20/ml-production-pipelines-a-classification-model)

30 minutes of video to get an overview from end to end of how to productionalize models.
It's straightforward and concise. 

As a summary: Test and monitor your predictive system. Don't forget that productionalizing a model is not a one-shot but a progressing process. You will improve over time.

# [Awesome production machine learning](https://github.com/EthicalML/awesome-production-machine-learning)

An awesome list of tools to productionalize models. If you're looking for a tool, it might be there. And if you know a tool that is not in the list, you can open a pull request.

Very good to know.

# [EvidentyAI](https://github.com/evidentlyai/evidently)

Amazing! A tool to do data monitoring!

> Evidently helps analyze machine learning models during development, validation, or production monitoring. The tool generates interactive reports from pandas DataFrame. Currently, the Data Drift report is available.

![Data monitoring](/evidently_github.png)

# [Bugs are silent]({{< ref "/post/drift.md" >}})

As a summary: Bugs in predictive systems are most of the time silent. Don't expect your users to raise their hands saying something is wrong. That won't happen. 

**Use monitoring instead of waiting from your end-users!**
