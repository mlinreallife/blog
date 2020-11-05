---
title: "Alibi-detect for data drift detection"
date: 2020-09-18T17:01:10+02:00
draft: true
---

I've recently tested *Alibi-detect*. 
If you're looking for a free and open source tool to detect data drift, this one is for you.

Let's get an overview of what is inside and how you can use it.

# The assumptions
The data drift detection of the library is based on a paper called *Failing Loudly: An Empirical Study of Methods
for Detecting Dataset Shift* and written by Stephan Rabanser, Stephan Günnemann, and Zachary C.Lipton.

In this paper, they want to detect data drift with a practical solution.

They do their tests with the MNIST dataset and use hypothesis tests to detect data drift.
They also use dimensionality reduction to get a practical solution.

The process is the following one:

![The process](/failing_loudly.PNG)

After different tests (data drift detection that gets an impact in the model), they found that the following two solutions are the most efficient:
- BBSDs for dimensionality reduction + multiple-univariate testing case (multiple Kolmogorov-Smirnov tests for each feature aggregated via the Bonferroni correction)
- UAE for dimensionality reduction + multivariate testing (Maximum Mean Discrepancy)

In the end, they open about the possibility to rule new tests. They used a standard image classification. And it would be helpful to explore the results of this paper to other machine learning domains such as natural language processing or graphs.

A study is always a piece of a bigger puzzle. It means that this paper doesn't claim to be the truth to data drift detection.

You can find more about this paper [here](https://arxiv.org/abs/1810.11953).

# How does it work?

The library *Alibi-detect* followed the suggestions of this paper. It might be not the best solution for data drift detection and in a couple of years, we will know better how to deal with that. At least, *Alibi-detect* has the merit to offer a free and open-source solution. It's better than nothing.

To do the dimensionality reduction, you use Keras and an autoencoder for instance:

```python
tf.random.set_seed(0)

# define encoder
encoder_net = tf.keras.Sequential(
  [
      InputLayer(input_shape=(columns)),
      Dense(256, activation='relu')
  ]
)
uae = UAE(encoder_net=encoder_net)
preprocess_kwargs = {'model': uae, 'batch_size': 128}
```

Then you can do the data drift detection using Kolmogorov-Smirnov tests:

```python
# initialise drift detector
p_val = .05
cd = KSDrift(
    p_val=p_val,        # p-value for K-S test
    X_ref=baseline,       # test against original test set
    preprocess_X_ref=True,  # already preprocess X_ref at init stage to save time
    preprocess_kwargs=preprocess_kwargs,
    alternative='two-sided'  # other options: 'less', 'greater'
)

preds_h0 = cd.predict(target, return_p_val=True)
```

Then, you get your result. You know if your data is drifting:

```python
print(preds_h0['data']['is_drift']) # True of False
print(preds_h0['data']['p_val']).mean() # Mean of all the p-values as it is multiple univariate tests in this case
```

You can explore the (documentation)[https://docs.seldon.io/projects/alibi-detect/en/latest/methods/ksdrift.html] for more information.

# Why do I like it?

First of all, I like this library for a simple reason: **this is the only open-source and free tool I found to do data drift detection**. You can use it the way you want. The creators are transparent on the assumptions they had to build this one. You can freely read the paper.
Besides, if you want support for this library, *Seldon-core*, the company behind the library, is improving its platform to include it in it.

This library is simple. You don't have many options. It's a simple test.

From my experience, the learning curve is smooth.

And the computation, thanks to the dimensionality reduction, is fast.

# What is missing in this library?

First of all, the community is small. I hope that it will grow.

Then, it's simple. You don't have much information on your features. This is why If I use this library, I will complete it with some information about my features. You can add some statistics for instance like *mean*, *max*, *min*, *percentile 25*, *percentile 50*, etc.
You can also check if the difference in these statistics is not too high between the target and the baseline. It may be not a scientific suggestion. But at least, it's understandable by anyone and can add value to your monitoring. It can complete the data drift detection offered by *Alibi-detect*.

Finally, you can get two kinds of alerts:
- Is the data drifting according to the test offered by Alibi-detect (Kolmogorov-Smirnov or Maximum Mean Discrepancy)?
- How many features in the target have a median 20% higher or lower than the baseline?

# Conclusion

I recommend you to test *Alibi-detect* and most of all I recommend you to include data drift detection in your monitoring.

Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that.
