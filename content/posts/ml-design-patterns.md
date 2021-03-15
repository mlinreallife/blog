---
title: "Machine Learning Design Patterns"
date: 2021-02-23T07:01:10+02:00
draft: false
images: [mia_cute.jpg] 
description: I would like to tell you a story. I was trying to understand a bug. I spent maybe 5 pomodoros on it. Pomodoro is a technique that helps you to stay focus. I couldn't find the root cause of my bug. I was quite frustrated but still motivated. I decided to stop my session of pomodoros and left my work for the day. I went to my beautiful cat and started petting her. I was starting relaxing when at a sudden I got the solution to my bug.
---

A design pattern is a way to answer to a well known problem.
Giving a name to the problem and the solution helps to handle it.

There are common challenges in machine learning:
- data quality: data accuracy, data completeness, data consistency, timeliness
- reproducibility: you can add seed. Problem of the repeatability with distributed training
- data drift
- scale
- multiple objectives: different stakeholders, different teams

## Data Representation Design Patterns

Data representation = feature engineering

Scaling is desirable:
- Gradient descent optimizers require more steps to converge as the curvature of the loss function increases.
- Better to scale for L1 and L2 optimization
- Better to scale for algorithms such as Kmeans that are sensible to large numbers

Four forms of scaling:
- Min-max scaling: pb => the min and max value have to be estimated from the training dataset, and they are often outliers. The real data often gets shrunk to a very narrow range in the [-1, 1] band.

- Clipping: use "reasonable values instead of min and max". This has the effect of treating outliers as -1 or 1.

- Z-score normalization: Addresses the problem of outliers without requiring prior knowledge of what the reasonable range is by linearly scaling the input using the mean and standard deviation.

- Winsorizing: Use the empirical distribution in the training dataset to clip the dataset to bounds given by the 10th and 90th percentile of the data values.

Don't throw away outliers that are valid data.

1. Hashed Feature
2. Embeddings
3. Feature Cross X
4. Multimodal input
5. Reframing X
6. Multilabel X
7. Ensembles
8. Cascade
9. Neutral class X

### Design Pattern 1: Hashed feature
It addresses 3 possible problems: incomplete vocabulary, model size due to cardinality and cold start.

Pb: One-hot-encoding requires knowing the vocabulary beforehand.

Solution: Transform into string, then do a hash, divide by the desired number of buckets. 
2 or more airports then are in the same bucket.

Trade-Offs and alternatives: Bucket collision. It is a lossy operation.

Skew: the loss of accuracy is particularly acute when the distribution of the categorical input is highly skewed.

Aggregate feature: find other features that you aggregate to get more useful information

Hyperparameter tuning: treat the number of buckets as a hyperparameter that is tuned.

Cryptographic hash: don't choose a hash that is a random hash.

Empty hash buckets: although unlikely, there is a remote possibility that even if we choose 10 hash buckets to represent 347 airports, one of the hash buckets will be empty.
Then, it may be beneficial to also use L2 regularization so that the weights associated with an empty bucket will be driven to near-zero.

### Design Pattern 2: Embeddings
Problem: one-hot-encoding can be enormous if we have many possibilities.
One-hot-encoding treats the values as independent. They are not. A world like walk is closer to the word run than to the word book.

Solution: Embeddings to capture closeness relationships in the input data.

Autoencoders can be used for that. Word2Vec, Bert. We can store embeddings in a data warehouse.

Can reduced the size of the features.

### Design Pattern 3: Feature Cross

Pb: Using only the features x_1 and x_2, it's not possible to find a linear boundary that separates the + and - classes. This means that to solve the pb, we have to make the model more complex, perhaps by adding more layers to the model. However, a simpler solution exists.

It's the ability of crossing two features. For instance, you can concatenate hour_of_day + day_of_week. 

Feature cross is naturally done in trees and DNN. But you can do it yourself in a simpler model which will computes faster. You can use the function "crossed_column" from TensorFlow or do it yourself with a concatenation.

Handling numerical features: transform them into categorical features with buckets.

Handling high cardinality: can increase the cardinality. To avoid that, use an embedding layer.

### Design Pattern 4: Multimodal Input

This is the ability to add different inputs: images and tabular text, numerical features and categorical features.

Use hot-one-encoding for categorical features.
Flatten everything to get images and tabular text.

You can represent the same data in different ways. For instance for text, we can use BOW (Bag of words, absence or presence of a word in a document) + embeddings.
We get a complete description of the features.


## Problem representation design patterns

### Design Pattern 5: Reframing

From a regression to a classification. Example: instead of predicting the prefect time, we bucketize the outputs and predict bucketized outputs.
We can also do the contrary. For example with ratings.

The more a distribution is wide spread, the more it is accuracte as a classification.
The more a distribution is tiny, the more it is accuracte as a regression.

### Design Pattern 6: Multilabel

Where we can assign more than one label to a given dataset.

Solution: Use "sigmoid" activation function in our final output layer. Instead of softmax.
The difference is that the softmax array is guaranteed to contain three values that sum to 1, whereas the sigmoid output will contain three values, each between 0 and 1.

Use binary_cross_entropy as loss function even for multilabel models. 3 classes is essentially 3 smaller binary classification problems.

To get the good values, we use a threshold.

Another alternative is one versus rest.

### Design Pattern 7: Ensembles
Improve performance and produce predictions that are better than any single model.

- Bagging => Example => RandomForest => high bias (underfitting)
- Boosting => Example => XGBoost => high variance (overfitting)
- Stacking: one model after another

Alternative = dropout as bagging. Even if it's on the same data.

pbs: It decreases model interpretability.

### Design Pattern 8: Cascade

We choose which model to run based on whether the activity belonged to a reseller.

1. First predict which model to use
2. Then use the result of the first classifier to choose which model to use

Pb: the first classifier can be mistaken. So you send a data to a model that it has never seen. 

Cascade = when the output of th one model is an input to the following model or determines the selection of subsequent models.

1. A classification model to identify the circumstance
2. 1 model trained on unusal circustamces
3. A model trained on typical circumstances
4. A model to combine the output of the 2 separate models

A kind of ensemble but a bit different.

But try to avoid cascade. It adds complexity. Instead add the discriminant as an input. 

Because the first model will get errors, train the second with the result of the first one.
In fact, train all.

### Design Pattern 9: Neutral class

Classification with yes, no and maybe.

Maybe is the neutral class.

Useful when human experts disagree.

useful to evaluate customer satisfaction because customers tend to be neutral.

We can reframe with neutral class from regression to classification introducing a neutral class.
