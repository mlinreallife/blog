---
title: "A banal machine learning system where interpretability and explainability matter"
date: 2021-01-06T06:11:10+02:00
draft: false
description: As algorithmic systems become more prevalent, the need to understand them grows (Interpretability report from Cloudera).
---

> As algorithmic systems become more prevalent, the need to understand them grows (Interpretability report from Cloudera).

Interpretability and explainability are used for ethics purposes.

It can serve other interests: medical diagnosis, safety decisions, etc.
It can also be used for any kind of ordinary applications.

I would like to tell you a story. Once upon a time, there was a banal machine learning system. For this one, interpretability and explainability mattered.

## A story about predicting breakdowns

Suppose you are working with a system that predicts breakdowns for lifts.

The system is not a complete black box such as a neural network. However, it is not a complete white box such as a linear regression.

You are dealing with a random forest algorithm.

You have different events:
- The time between two floors
- The time between the moment a door opens and the moment it closes
 
All these data are inputs of the algorithm. When the system predicts a breakdown, technicians must trust it. It is easier to intervene when you have the breakdown than when you suppose you will have one.

Imagine you trying to solve a bug that you think you will have but you don’t have yet. For sure, it is challenging.

## Use interpretability to enhance your system

Interpretability helps to gain the technician’s trust.

Interpretability can be global and local.

You can give local interpretability to any machine learning system. There are several methods and tools to do that.

You can detect correlations. For instance, when the time between two floors exceeds two minutes, you might get a breakdown soon.

In this case, interpretability gives some explanations. However, it is not enough.

## Interpretability has limits

Indeed, you know why the system has predicted a breakdown. The answer is: the time between two floors exceeds two minutes.

That’s not so bad.

But, the breakdown still doesn’t exist. You have a hint about your bug. But it still doesn’t exist. You have no way to find the deep root cause of it. You have no idea how to solve it and where to start.

Your hint— the time between two floors exceeds two minutes — does not help.
Interpretability could be great. But if your inputs are not easy to interpret anyway, that is not enough.

Moreover, most of the time, techniques and tools for interpretability give correlations, no causalities.

## Explainability: a way to go beyond these limits

We need interpretability and confidence as a global issue. We need human explainability.

> Interpretability is about being able to discern the mechanics without necessarily knowing why. Explainability is being able to quite literally explain what is happening (Machine Learning Explainability vs Interpretability: Two concepts that could help restore trust in AI).

The idea is to build a reliable and interpretable system.

In our story, you can imagine a way to predict the root cause of a future breakdown. You could have different probabilities about the potential reasons for the breakdown.

## Conclusion

Interpretability and explainability are not only for Google, medical analysis, or military purposes.

In our case, explaining a prediction helps to believe it.

There are other advantages to interpretability and explainability. 

>The more you understand the algorithm, the more you can improve it (Cloudera report).

Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that.
