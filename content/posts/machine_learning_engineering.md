---
title: "Machine learning engineering"
date: 2020-09-18T17:01:10+02:00
draft: true
---

# Introduction

Training data is exposed to the ml algo, whereas holdout data is not.

Supervised learning makes a prediction by taking a feature vector about this feature vector.

Unsupervised learning transforms an input, always a feature vector.

Classification = finite set of classes.
Regression = infinite set of classes.

Direct data is used as an example. Indirect data is used to enrich the previous data.

"Feature engineering is the process of transforming data into a form that machine learning algorithms can use"

A baseline must be set to assess the model against an heuristic.

Most of the time, ML is implemented as a pipeline: data transformation, model training, etc.

This pipeline is used for the prediction.

Parameters of the model, the hyperparameters are tuned by using the validation dataset.

Shallow vs deep learning.

Shallow = predictions done directly from the inputs. 

Deep learning = Each layer generate outputs of the preceding layer as inputs. Only neural networks right now.

When using ML?
- Complex business problem
- Pb is constantly evolving
- Perceptive problem
- Unstudied phenomenon
- Simple objective

When not using ML?
- When explainability is needed
- When errors are intolerable
- When traditional software engineering is a less expensive option
- When data is hard to get or too expensive

Machine learning engineering (MLE) is the use of scientific principles, tools and technique of ml and software engineering to design and build complex computing systems.

# Before the project starts

Build the team.

Impact of ML is high when:
1. ML can replace a complex part of your business.
2. Great benefit in getting inexpensive and imperfect predictions.

Cost of ML influenced by 3 factors:
1. Difficulty of the pb
2. Costs of data
3. The needed model performance quality

Very difficult to estimate an ML project.

Several major unknowns almost impossible to guess:

Whether the required level of model performance is attainable in practice, how much data we need to solve this pb, what features and how many features are needed, how large the model should be, and how long will it take to run one experiment and how many experiments will be needed to reach the desired level of performance.

One way to make a more educated guess is to simplify the problem and solve a simpler one.

The progress is non linear. The error usually decreases fast in the beginning but then the progress slows down.

2 cultures of structuring a ML team: DS and DE are different persons, DS and DE are the same person.

# Data collection and preparation

Before starting collecting the data, 5 questions to answer. Will the data be accessible, sizeable, useable, understandable and reliable.

Common pbs with data are high cost, bias, low predictive power, outdated examples, outliers and leakage.

Good data contains enough information that can be used for modeling, has good coverage of what you want to do with the model, and reflects real inputs that the model will see in production. It is as unbiases as possible and not a result of the model itself, has consistent labels, and is big enough to allow generalization.

To obtain a good partition of your entire dataset into training, validation and test sets:
1) Data was randomized before the split. 2) Split was applied to raw data. 3) same distribution. 4) leakage was avoided

Data imputation for missing attributes in the data.

Data augmentation for more labeled examples. Usually for images but can be used for tests (synonyms).

Class imbalance can significantly affect the performance. Use oversampling or undersampling.
When working with big data, not always good to work with the all datasets.Data sampling strategies.

Data versioning is critical. 
Different labelers may provide labels of varying qualities.

# Feature engineering

Features are values extracted from the data entities your model is designed to work with. Feature engineering represents a specific property of a data entity. Features are organized in feature vectors, and the model learns to perform mathematical operations on those feature vectors to generate the desired output.

For text, features can be generated in bulk by using techniques like bag-of-words. TD-IDF.

Most machine learning algorithms and libraries require numerical features. Techniques such as one-hot-encoding and mean encoding are used. If values are cyclical like days or weeks, convert it into two features, using the sine-cosine transformation.

Feature hashing is a way to convert text data, or categorical attributes with many values, into a feature vector of an arbitrary dimensionality. That can be useful when one-hot-encoding or bag-of-words generate feature vectors with impractical dimensions.
Example: murmur3, sha.

Topic modeling is a family of algorithmic techniques such as LDA or LSA, that allows us to learn a model that converts any document into a vector of topics of a required dimensionality.

Use DL with LSTM, CNN and transformer for time series.

Good features have predictive power, can be computed fast, are reliable and uncorrelated.

Same distribution than the real life. Good features are unitary, easy to understand and maintain. The property of being unitary means that the feature represents a simple-to-understand and -explain quantity.

To increase the predictive power of the data, additional features can be synthesized by discretizing an existing numerical feature, clustering training examples or applying simple transformations to existing features or combining pairs of features.

For text, features can be learned from unlabeled data in the form of word and document embeddings. More generally, embeddings can be trained for any type of data if we manage to formulate an appropriate prediction problem and train a deep model. Embedding vectors are then extracted from several rightmost fully-connected layers.

Wise use of feature selection techniques remove features that don't contribute to a model's quality. Two common techniques are cutting the long tail and Boruta. L1 regularization also works as a feature selection technique.

Dimensionality reduction can improve visualization of high-dimensional datasets. It can also improve the model's predictive quality. Presently such techniques as PCA, UMAP, and autoencoders are used for dimensionality reduction. PCA is very fast, but UMAP and autoencoders produce better visualizations.

It is considered best practices to scale features before training the model, store and document features in schema files or feature stores, and keep code, model and training data in sync.

Feature extraction code is one of the most important parts of a machine learning system. It must be extensively and systematically tested.

# Supervised model training (part 1)

Several checks and decisions before working with the model:
- Data must be conformed to the model
- Define achievable level of performance
- Choose a performance metric

Ideally, the model performance should be a single number.

To choose a machine learning algorithm, ask yourself:
- Do the model's predictions have to be explainable to a non-technical audience? If yes, you would prefer using less accurate, but more explainable algorithms, such as KNN, linear regression and decision tree.
- Can you dataset be fully loaded into the RAM of your laptop of server? If not, you would prefer incremental learning algorithms.
- How many training examples do you have in your dataset and how many features does each example have? Some algorithms, including those used for neural networks and random forests, can handle a huge number of examples and millions of features. Others are relatively modest in their capacity.
- Is your data linearly separable, or can it be modeled using a linear model? If yes, SVM with the linear kernel, linear and logistic regression can be good choices. Otherwise, DL or ensemble models might work better.
- How much time is a learning algorithm allowed to use to train a model? Neural networks are known to be slow to train. Simple algorithms like linear and logistic regression or decision trees are much faster.
- How fast must the scoring perform in production? Models like SVM, linear and logistic regression, as well as not very deep feedforward neural networks, are extremely fast at the prediction time. The scoring using deep and recurrent neural networks, as well as gradient boosting models, is slower.

Tweaking the values of hyperparameters controls two tradeoffs: precision-recall and bias-variance. By varying the complexity of the model, we can reach the so-called "zone of solutions", a situation in which both bias and variance of the model are relatively low. The solution that optimizes the performance metric is usually found inside that zone.

Regularization is an umbrella-term for methods that force the learning algorithm to build a less complex model. It leads to higher bias but reduces variance. L1 and L2. Neural networks benefit from 2 other regularization techniques: dropout and batch normalization.

Most modern ml frameworks support the notion of a pipeline. A pipeline is a sequence of transformations. The pipeline can be saved to a file similar to saving a model. It can be deployed to production and used to generate predictions.

A data analyst must "tune" hyperparameters by experimenting with different combinations of values. Grid search is the simplest and most widely used hyperparameter tuning technique.

A decent validation test contains at least a hundred examples, and each class in the set is represented by at least a couple of dozen examples. When you don't have a decent validation set to tune hyperparameters, you can use cross-validation.

# Supervised model training (part 2)

Instead of training your model from scratch, it can be useful to start with a pre-trained model. 

A pre-trained model can be used in 2 ways:
1. Its learned parameters can be used to initialize your own model.
2. It can be used as a feature extractor for your model.

Using a pre-trained model to build your own is called transfer learning. The fact that deep models allow for transfer learning is one of the most important properties of deep learning.

Minibatch stochastic gradient descent and its variants are the most frequently used cost function optimization algorithms for deep models.

There are several popular upgrades to minibatch stochastic gradient descent, such as Momentum, RMSProp and Adam. These algorithms update the learning rate automatically based on the performance of the learning process. You do not need to choose the initial value of the learning rate, the decay schedule and rate, or the values of other related hyperparameters. These algorithms have demonstrated good performance in practice, and practicioners often use them instead of trying to manually tune the learning rate.

In addition to L1 and L2 regularization, neural networks benefit from neural network specific regularizers: dropout, early stopping, and batch normalization.

Batch-normalization is a best practice.

Ensemble learning is training an ensemble model, which is a combination of several base models, each indivi
