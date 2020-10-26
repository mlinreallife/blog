---
title: "Model drift or how the pandemic killed thousands of predictive systems"
date: 2020-09-18T17:01:10+02:00
draft: true
---

In a very near world, machine learning was more and more used.
All of a sudden, a pandemic strikes this world. Machine learning crashes.

# Why does machine learning crash in such a period?

Machine learning learns patterns from data at a certain period of time. We evaluate and tune the performance of a predictive system at this certain period of time.
But, only the change is permanent.

With Covid-19, the lockdowns, the recession, the curfews, everything has changed. Maybe not everything, but enough to make machine learning systems crash. People don't buy the same products. People don't discuss the same topics.

The change due to the pandemic is sudden. It is called an abrupt drift. But, in reality, gradual drift can also happen. For instance, the word *troll* has changed a lot. In the beginning, it was often related to J.R Tolkien. Now, it can refer to a joke. This change was smooth.

# Different terminologies of drift

This situation refers to the *model drift* concept. Different kinds of drift exist.

*Model drift* is when you observe your model drifting. But, it's always because of the data. Then, you can also observe your data drifting. *Data drift* is the name for this concept.

You can observe model drift during retraining and when comparing your predictions with the real values. To do that, you need to track the results of your retraining, store the given predictions and build a comparison with the real outcomes.

To observe data drift, you must monitor your data after having ingested them.

I would recommend starting by monitoring model drift by doing retraining. Then, compare your results with the real ones and do data drift. If you set up retraining once a month, you could realise that you need to retrain more often. To realise that, you need to see the real results or if not possible evaluate the data drift.

Data drift is also a way to understand better why there's a model drift. It is a help for investigation.

## Conclusion
Because of the pandemic, many people have started realising the importance of *model drift* and *data drift*. However, these two concepts are crucial even during normal times if you want your predictive system to stay efficient.
