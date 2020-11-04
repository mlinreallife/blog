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

Ensemble learning is training an ensemble model, which is a combination of several base models, each individually performing worse than the ensemble model.

Strong models can be combined into an ensemble model by averaging their outputs or by taking a majority vote. Model-stacking being the most effective of the ensembling methods, consists of training a meta-model that takes the output of base models as input.

The performance of the model can be iteratively improved using the following simple process:

1. Train the model using the best values of hyperparameters identified so far
2. Test the model by applying it to a small subset of the validation set (100 - 300 examples)
3. Find the most frequent error patterns on that small validation set. Remove those 

# Evaluation

All statistical models running in production must be carefully and continuously evaluated.

- Estimate legal risks of putting the model in production
- Understand the main properties of the distribution of the data used to train the model
- Evaluate the performance of the model prior to deployment, and
- Monitor the performance of the deployed model

An offline model evaluation happens after the model was trained. It is biased on the historical data. The online model evaluation consists of testing and comparing models in the production environment using online data.

A popular technique of online model evaluation is A/B testing. When performing A/B testing, we split users into two groups. 

Multi-armed brandit is another popular technique of online model evaluation. 

Accuracy, robustness and fairness may have to be evaluated sometimes.

# Model deployment
The most popular deployment pattern is to deploy the model on a server and make it available as a Rest API.

Silent deployment: the old and new versions are running in parallel. The user is exposed to the new version when the switch is done. The predictions made by the new version are only logged and analyzed. Thus, there is enough time to make sure that the new model works as expected without affecting any user. A drawback is the need to run more models wich consumes more resources.

Canary deployment: consists of publishing the new version to a small fraction of the users, while keeping the old version running for most users. Canary deployment allows model performance validation and evaluating the users'experience. It won't affect lots of users in case of possible bugs.

Multi-armed brandits allow us to deploy the new model while keeping the old one. The algorithm replaces the old model with the new one only when it is certain that it performs better.

Experienced scientists and engineers build Python packages with efficiency in mind.

# Model serving, monitoring and maintenance

An effective runtime has the followig properties. It is secure and correct, ensures ease of deployment and recovery, and provides guarantees of model validity.

ML models are served in either batch or on-demand mode. Batch mode for big data and when some latency is tolerable.

The model deployed in production must be constantly monitored. The goals of monitoring are to make sure that the model is served correctly, and that the performance of the model remains within acceptable limits.

A variety of things might go wrong with the model in production, in particular:
- Addition training data made the model perform worse
- the properties of the production data changed, but the model didn't
- the feature extraction code was significantly updated, but the model didn't adapt
- a resource needed to generate a feature changed or became unaivalable
- the model is abused or is under an adversarial attack

An automation must calculate values of the performance metrics critical for the business, and send alerts to the appropriate stakeholders if the values of those metrics change significantly or fall below a threshold. In addition, the monitoring must reveal the distribution shift, numerical instability and a decreasing computatinal performance.

It's important to log enough information to reproduce any erratic system behavior during an analysis in the future.
Most machine learning models must be regularly or occasionnaly updated. The rate of updates depends on several factors.

- How often it makes errors and how critical they are
- How "fresh" the model should be to be usefula
- How fast new training data becomes available
- How much time it takes to retrain a model
- How costly it is to train and deploy the model, and
- How much a model update contributes to the achievement of user goals

After a model update, a good practice is to run the model against the examples in the end-to-end and confidence test sets. It's important to make sure that the outputs are either the same as before, or that the changes are as expected.

Check also that the errors are distributed uniformly across the user categories. It's undesirable if the new model negatively affects users from a minority or specific location.

Hammelina, AUC computing with Spark:
dates = predictions.select("prediction_date").distinct().collect()
formatted_dates = [str(item.prediction_date) for item in dates]

aucs_by_date = []
for item in dates:
  formatted_date = str(item.prediction_date)
  filtered_predictions = predictions.filter(f"prediction_date == '{formatted_date}'")
  prepared_predictions = filtered_predictions.selectExpr("prediction as label", "cast(1.0 as float) as rawPrediction").rdd.map(lambda s: (s.label, s.rawPrediction))
  metrics = BinaryClassificationMetrics(prepared_predictions)
  auc_by_date = (metrics.areaUnderROC, formatted_date)
  aucs_by_date.append(auc_by_date)
  
columns = ["auc","date"]
aucs_by_date_df = spark.createDataFrame(data = aucs_by_date, schema = columns)
display(aucs_by_date_df)

# columns = ["prediction_date", "actual", "prediction"]
# data = [("2020-10-28", 1.0, 1.0),("2020-10-28", 1.0, 0.0),("2020-10-29", 1.0, 1.0),("2020-10-29", 1.0, 1.0),("2020-10-30", 1.0, 0.0), ("2020-10-30", 1.0, 0.0), ("2020-10-31", None, 0.0), ("2020-10-31", None, 0.0)]
# predictions = spark.createDataFrame(data = data, schema = columns)