---
title: "Issue 3: Feature store, weird chatbot, XGboost for Spark and Airflow in Amazon"
date: 2020-11-09T07:01:10+02:00
draft: true
---

This week, I think I've finally understood what a feature store is (thanks to Tecton). There is also some other news: better integration of the orchestrator Airflow in Amazon, distributed XGboost with Spark, a chatbot from Google which is better than before but still weird.

# [Introducing Amazon Managed Workflows for Apache Airflow (MWAA)](https://aws.amazon.com/fr/blogs/aws/introducing-amazon-managed-workflows-for-apache-airflow-mwaa/)

I'm a big fan of Apache Airflow which is a great tool to orchestrate your tasks. 
Then, I'm glad to hear about 
> A fully managed service that makes it easy to run open-source versions of Apache Airflow on AWS

# [What is a Feature Store?](https://www.tecton.ai/blog/what-is-a-feature-store/)

![What is a feature Store](/Enl1mtNW8AAi9Lz.jpg)

A great article about what a feature store is concretely. In a nutshell:
> A feature store is an ML-specific data system that:
>
> - Runs data pipelines that transform raw data into feature values
> - Stores and manages the feature data itself, and
> - Serves feature data consistently for training and inference purposes

# [Meena, the new chatbot of Google is still weird](https://voicebot.ai/2020/02/03/googles-new-meena-chatbot-imitates-human-conversation-and-bad-jokes/)

Chatbots are better and better year after year, but still weird:

![Meena discussion](/meena.png)

# [How to Train XGBoost With Spark](https://databricks.com/blog/2020/11/16/how-to-train-xgboost-with-spark.html)

> XGBoost is currently one of the most popular machine learning libraries and distributed training is becoming more frequently required to accommodate the rapidly increasing size of datasets. 

> XGBoost4J-Spark can now be quickly used to distribute training on big data for high performance and accuracy predictions

![XGboost with Spark](/xgboost.jpg)


Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss machine learning in real life.
