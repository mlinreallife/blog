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

Data Representation
1. Hashed Feature
2. Embeddings
3. Feature Cross X
4. Multimodal input

Problem Representation
5. Reframing X
6. Multilabel X
7. Ensembles
8. Cascade
9. Neutral class X
10. Rebalancing X

Model training

11. Useful overfitting
12. Checkpoints
13. Transfer learning X
14. Distribution strategy
15. Hyperparameter tuning

Resilient Serving

16. Stateless Serving function X
17. Batch Serving X
18. Continued Model Evaluation
19. Two-Phase Predictions
20. Keyed Predictions

Reproducibility

21. Transform X
22. Repeatable Splitting
23. Bridged Schema
24. Windowed Reference
25. Workflow Pipeline X
26. Feature Store
27. Model Versioning

Responsible AI

28. Heuristic Benchmark X
29. Explainable Predictions
30. Fairness Lens

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

### Design Pattern 10: Rebalancing

Various approchaes for handling datasets that are inherently imbalanced.

Solutions:
- Choose the right evaluation metric: precision, recall, F1 over accuracy or AUC.
- Downsampling the majority class
- Upsampling the minority class
- Weighted class: it's possible in Keras. It's also possible with XGBoost.

Trade-offs and alternatives:
We can use reframing and cascade instead.

Be aware of the importance of explainability in such a case.

## Model training patterns

### Design pattern 11: Useful overfitting
For physics model (when you can cover all the cases in the training set) and when you want to be sure that you're able to learn some patterns.

### Design pattern 12: Checkpoints

We store the full state of the model periodically so that we have partially trained models available.

We can save it as the final model (early stopping) or as the starting points for continued training (in the case of machine failure and fine-tuning).

Early stopping = to prevent overfitting, it can be helpful to look at the validation error after each epoch.

Checkpoint selection = be aware that to do early stopping, sometimes you need to wait.
The loss function can decrease, then increase, then decrease again. 
Because data are not equally sampled.

It's better to use regularization and dropout because this way we use the all dataset.

Fine-tuning = store a checkpoint. Refresh with fresh data. => Faster.

### Design pattern 13: Transfer learning

Works for texts and images. Don't work for tabular data because too specific.

Transfer leaning works because it lets us stand on the shoulders of giants, utilizing models that have
already been trained on a large dataset to do image classification.

Typically the penultimate layer of the model is chosen as the bottleneck layer. It's the layer input before the output layer.

In Keras, one of the these 2 methods:

- Load a pretrained model on your own. Remove the layers after and add a new final layer with your own data and labels.
- Use a pretrained Tensorflow hub module as the foundation for your transfer learning task.

Feature extraction (freeze the weights) VS fine tuning (fine-tune the weights)
Tensorflow : trainable = True

fine-tuning: common to leave the weights of your model's initial layers frozen since these have been trained to recognize basic features.

Progressive fine-tuning -> iteratively unfreezeing layers after every training.

### Design pattern 14: Distribution Strategy

data parallelism and model parallelism

data parallelism = train on differents subsets of the training
model parallelism = model is split into different workeers and these carry out the computation for differents parts of the model

tf.distribute.Strategy

a method for different workers to compute grandients and store that info to make updates to the model params.

data parallelism can be carried out either synchronously or asynchronounlsy.

In synchronous training, each worker holds a copy of the model and computes gradients using a slice of the training data mini-batch.

In asynchronous training, each worker performs a gradient descent step with a split of the mini-batch. No one worker waits for updates to the model from any of the other workers.

### Design patern 15: hyperparameter tuning

In hyperparameter tuning, the training loop is itself inserted into an optimization method to find the optimal set of model hyperparameters.

Manual tuning, grid search.

Solution: Keras-tuner Bayesian optimization to do hyperparameter search directly in Keras.

Genetic algorithms can be used.

## Resilient Serving

### Design Pattern 16: Stateless Serving function

Model export
Inference in Python
Create web endpoint

It works because of autoscaling, fully managed, language neutral (if possible).

### Design Pattern 17: Batch serving

A large number of instances all at once

Alternative: lambda architecture -> Supports both online serving and batch serving.

### Design Pattern 18: Continued Model Evaluation

Model drift - data drift

To do that => Save predictions
Capture ground truth
Evaluate model perf
Continuous evaluation

Do that to check triggers for retraining.

Data validation with TFX.

### Design Pattern 19: Two-Phase Predictions

The Two-Phase Predictions design pattern provides a way to address the problem of keeping large, complex models performant when they have to be deployed on distributed devices by splitting the use cases into two phases, with only the simpler phase being carried out on the edge.

Example: Recognize okay google on the device.
Do the request on an API.

### Design Pattern 20: Keyed Predictions

## Reproducibility design patterns

### Design Pattern 21: Transform

The Transform design pattern makes moving an ML model to production much easier by keeping inputs, features, and transforms carefully separate.

To reuse. Can be difficult according to your framework.

### Design Pattern 22: Repeatable splitting

To ensure that sampling is repeatable and reproducible, it is necessary to use a well distributed column and a deterministic hash function to split the available data into training, validation and test datasets.

If you use seed, it leads to leakage information between the training and testing dataset when some of the flights on any particular day are in the training dataset and some other flights on the same day are in the testing dataset.

### Design Pattern 23: Bridged Schema

The bridged schema design pattern provides ways to adapt the data used to train a model from its older, original data schema to newer, better data.

### Design Pattern 25: Workflow Pipeline

In the Worflow Pipeline design pattern, we address the problem of creating an end-to-end reproducible pipeline by containerizing and orchestrating the steps in our machine learning process. The containerization might be done explicitly, or using a framework that simplifies the process.

### Design Pattern 26: Feature Store

The "Feature Store" design pattern simplifies the management and reuse of features accross projects by decoupling the feature creation process from the development of models using those features.

### Design Pattern 27: Model Versioning

In the model versioning design pattern, backward compatibility is achieved by deploying a changed model as a microservice with a different REST endpoint. This is a necessary prerequisite for many of the other patterns discussed in this chapter.

## Responsible AI

### Design Pattern 28: Heuristic Benchmark

The Heuristic Benchmark pattern compares and ML model against a simple, easy-to-understand heuristic in order to explain the model's performance to business decision makers.

### Design Pattern 29: Explainable Predictions

### Design Pattern 30: Fairness Lens
