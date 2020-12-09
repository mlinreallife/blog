---
title: "Getting started with MLeap and Scikit-Learn"
date: 2020-05-27T17:01:10+02:00
draft: false
description: MLeap, a library to serialize your model.
---

> Deploying machine learning data pipelines and algorithms should not be a time-consuming or difficult task. MLeap allows data scientists and engineers to deploy machine learning pipelines from Spark and Scikit-learn to a portable format and execution engine <cite>(MLeap documentation)</cite>.

*MLeap* helps you to serialize and deserialize your model/pipeline. It exists for *Spark*, *Scikit-Learn* and *Tensorflow*.
You can use it with *Scikit-Learn* but the documentation is quite dry for the moment. This is why I decided to do this small tutorial.

## Prepare some data
I will use *Numpy* and *Pandas* to get some data.

Suppose you want to do a classification. You need a dataframe with a feature column and a label column.

```python
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(100, 1), columns=['a'])

df["y"] = (df['a'] > 0.5).astype(int)

df.head()
```

You might have a result like that:

| a    | y |
|------|---|
| 0.61 | 1 |
| 0.26 | 0 |
| 0.20 | 0 |

A dataframe with variable *a* as a feature column and *y* as a label column for a classification.

## Serialize with MLeap and Scikit-Learn

I will use a logistic regression.

```python
from mleap.sklearn.logistic import LogisticRegression

logistic_regression = LogisticRegression(fit_intercept=True)

logistic_regression.mlinit(input_features='a',
                           prediction_column='e_binary')


logistic_regression.fit(df[['a']], df[['y']])

logistic_regression.serialize_to_bundle(
"/dbfs/FileStore/tables/mleaptestmodel", 
"model.json"
)
```

In *mleaptestmodel folder*, you have different files. They represent your model in a serialized format.

## Deserialize with MLeap and Scikit-Learn
To get back the model and use it for a prediction, you can do that:

```python
from mleap.sklearn.logistic import LogisticRegression

node_name = "{}.node".format("model.json")
 
logistic_regression_tf = LogisticRegression()

model = logistic_regression_tf.deserialize_from_bundle(
"/dbfs/FileStore/tables/mleaptestmodel",
 node_namelog
 )

expected = model.predict(df[["a"]])
```

## Conclusion
*MLeap* seems to be a nice project but not very active. I'm not sure I would recommend it. But at least, you've got a getting started with logistic regression if you must deal with it.

For the moment, the documentation is quite dry. For instance, I found nothing about deserializing with *Scikit-Learn*.

The tests of the project help me to understand this part.

I plan to make a pull request to add some documentation.

Thank you for reading.
