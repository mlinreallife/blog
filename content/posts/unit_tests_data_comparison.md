---
title: "Comparison of different tools to do unit tests for data"
date: 2021-01-08T07:01:10+02:00
draft: false
description: "Recently, I benchmarked different tools to do unit tests for data. Here are the results."
images: ["unit_test_data.png"]
---

TL;DR:

Recently, I benchmarked different tools to do unit tests for data. Here are the results.

|                       | Pydeequ                                           | Drunken Data Quality | Dataframes rule engine | Great Expectations | Apache Griffin                |
|-----------------------|---------------------------------------------------|----------------------|------------------------|--------------------|-------------------------------|
| **Language**              | Python                                            | Python               | Scala                  | Python             | Json, outside of code         |
| **Compatible Spark 3**    | No                                                | No                   | Not tested             | Yes                | X                             |
| **Compatible Databricks** | Unknown error. Pydeequ never tested in Databricks | Not tested           | Not tested             | Yes                | Not tested. Need Hive to work |

# Pydeequ

I must say that I'm disappointed. I like Deequ, the version for Scala users, very much.
But I was unable to make Pydeequ work in Databricks. There's an open issue.
Besides, it's not compatible with Spark 3.

# Apache Griffin

Apache Griffin seems to be mature. But it's a bit scary. 
You have to dedicate a special infrastructure and project to work with it.

# Dataframes rules engine

This project is developed by Databricks but only for Scala users.

Note that a new project named *Delta expectations* from Databricks is supposed to be released soon to do unit tests for data.

# Drunken Data Quality

As this project is not compatible with Spark 3, I didn't test it.

# Great Expectations

Great Expectations can check all my checkboxes: Python, Spark 3, and Databricks.
Besides, the support is excellent.

My only problem is that some helpful features (profiling) take time to be executed.


Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that.
