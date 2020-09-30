---
title: "Data drift monitoring: hypothesis tests or statistical distances?"
date: 2020-09-30T17:01:10+02:00
draft: true
---

Today, I would like to talk about a tough and important subject in my opinion: input data drift monitoring.

Data drift monitoring is critical. Input data drift leads to model performance decrease.
At the same time, IMHO, it's hard to get a satisfactory solution for at least two reasons:
- It's challenging to develop a custom solution.
- It's laborious to know if it is preferable to compute statistical distances or try to reject a hypothesis test with a p-value?

## What is "input data drift"?

*Input data drift* is when you get such a change in your coming data that it can impact the performance of the model.

What I name *data drift* has synonyms such as *data shift*.
The word gets also many subnames to describe the specificities of each kind of *data drift*. You can get *gradual drift*, *abrupt drift*, *extended drift*, etc.

I think it's important to understand that there are many kinds of drifts and that they don't say the same thing.

- A short but abrupt drift can be due to a problem in your data.
- An extended abrupt drift can be due to a recession.
- A seasonal drift can be due to the seasons.

You can see all these nuances in the paper [Characterizing Concept Drift](https://www.researchgate.net/publication/283761478_Characterizing_Concept_Drift) by Geoffrey I Webb, Roy Hyde, Hong Cao, Hai-Long Nguyen and François Petitjean.

## How to monitor "input data drift"?

There are two solutions that are presented in the literature.

### Statistical distances
I get the impression that the favourite one is computing a distance measure between your different distributions.
You can use *wasserstein distance*, *mahalanobis distance*, *euclidean distance* etc. Among all of them, you must choose one. *Hellinger distance* is the preferred one of the paper [Survey of distance measures for quantifying concept drift and shift in numeric data](https://www.researchgate.net/publication/327539525_Survey_of_distance_measures_for_quantifying_concept_drift_and_shift_in_numeric_data) written by Igor Goldenberg and Geoffrey I Webb.

They built different tests and find *Hellinger distance* more suitable because this distance is *robust* and *provide an "absolute" value, bounded between 0 and 1*.

Martin Schmidtz, the author of the article [How to Detect Drifting Models](https://rapidminer.com/blog/how-to-detect-drifting-models/) explains that he doesn't think hypothesis tests useful for monitoring data drift:

> A low p-value only means that we cannot confirm it. This does not mean that we can prove that these distributions are different! Not very useful…
><cite>Martin Schmidtz</cite>

> So I asked myself—isn’t there something else to use? And there is—distance measures for distributions!
><cite>Martin Schmidtz</cite>

The big winner seems to be: statistical distances.

### Hypothesis tests

A paper struck me recently: [Monitoring and explainability of models in production](https://arxiv.org/pdf/2007.06299.pdf) written by Janis Klaise, Arnaud Van Looveren, Clive Cox, Giovanni Vacanti and Alexandru Coca.

The authors speak about hypothesis tests to monitor data drift.

I had a discussion with one of the authors and found his explanation quite clarifying.

The distance between two distributions doesn't tell you when you have to be concerned. You must set a threshold to send an alert. This is what a statistical test does. *p-value* is surely not the best metric. But at least, it's easier to understand a *p-value* than a *wasserstein distance*.

The paper talks about a library I definitively want to test: [alibi-detect](https://github.com/SeldonIO/alibi-detect). It was designed to detect data drift with hypothesis tests: *Kolmogorov-Smirnov* and *Maximum Mean Discrepancy*.

## Conclusion

To answer the question previously asked *Data drift monitoring: hypothesis tests or statistical distances?*, I don't know. *Data Drift* is currently an open research area. So, it's normal not to know. What I definitively believe is that it's a tough but important topic. Then I would say it's better to do something - hypothesis test or statistical distance - instead of nothing.

[Azure Machine learning](https://azure.microsoft.com/fr-fr/services/machine-learning/) or [Mona Labs](https://www.monalabs.io/) proposes off-the-shelf solutions.

Thank you for reading.
