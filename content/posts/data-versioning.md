---
title: "Different ways to do data versioning"
date: 2020-09-07T06:11:10+02:00
draft: true
---

I have experienced two ways of doing data versioning and would like to share it with you.

It was always in a batch context to do supervised or unsupervised learning.

## What is data versioning? 

Data versioning is about keeping snapshots of the state of your data.
This way, you can see the state of the data at certain periods of time.

## Why doing data versioning?

There are many benefits:
 
- Rollbacks and replays on a specific date.

- Debug. This is the most important purpose for me. You can dive into a previous state of the data and understand what happened.

- Debug with a reproducible state. By versioning your model and your data, you get a reproducible state. It can be helpful if you want to explain one weird prediction for instance.

## Custom data versioning system

You can set a custom versioning system. For instance, all your data can be partitioned by a date. Suppose you get regular updates of data each day. With HDFS, you can partition your data this way:

- data
    - year=2019
        - month=02
            - day=01
            - day=02
            - day=03
            - etc.
            
In this case, your data is immutable.
 
To play or replay a specific date, you must pass it in your development as a variable to call the right partition. For instance with Spark:

```
spark-submit yourjob --year=2019 --month02 --day=01
```
And in your code, you must call the right data:

```python
spark.read.parquet("path").filter(s"year = '{year}' and month= '{month}' and day = '{day}'")
```

The benefits of a custom versioning system are the following:

- Flexible. You have the control
- Easy to rollback. You develop the versioning system. Then, you're ready to rollback or replay.

But there are disadvantages:

- Heavy solution. You have many files in your data lake.
- You have to develop, maintain and debug the solution. 

## Automated versioning with Delta Lake

Delta Lake was announced as a bigger innovation than Spark.

Maybe, it was for the *wow* effect. But it's true that Delta Lake is quite impressive. You put it above a data lake (HDFS, DBDS, etc) and then you get ACID transactions, updates, deletes and time travel with data versioning.

As explained in the [website](https://delta.io/):
*Delta Lake provides snapshots of data enabling developers to access and revert to earlier versions of data for audits, rollbacks or to reproduce experiments.*

To do that, you have to deal with a *delta* format instead of a *parquet* format for instance.

Then, to see the different versions of your data, you can do:

```python
delta_table = DeltaTable.forPath(spark, path)
delta_table.history().show()
```

Then, you get something like that:

|version|          timestamp|userId|userName|operation| operationParameters| job|notebook|clusterId|readVersion|   isolationLevel|isBlindAppend|    operationMetrics|
|----------|:-------------:|------| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
|      5|2019-07-29 14:07:47|   t|     Tom|   DELETE|[predicate -> ["(...|null|     ###|      ###|          4|WriteSerializable|        false|[numTotalRows -> ...|
|      4|2019-07-29 14:07:41|   t|     Tom|   UPDATE|[predicate -> (id...|null|     ###|      ###|          3|WriteSerializable|        false|[numTotalRows -> ...|
|      3|2019-07-29 14:07:29|   t|     Tom|   DELETE|[predicate -> ["(...|null|     ###|      ###|          2|WriteSerializable|        false|[numTotalRows -> ...|
|      2|2019-07-29 14:06:56|   t|     Tom|   UPDATE|[predicate -> (id...|null|     ###|      ###|          1|WriteSerializable|        false|[numTotalRows -> ...|
|      1|2019-07-29 14:04:31|   t|     Tom|   DELETE|[predicate -> ["(...|null|     ###|      ###|          0|WriteSerializable|        false|[numTotalRows -> ...|
|      0|2019-07-29 14:01:40|   t|     Tom|    WRITE|[mode -> ErrorIfE...|null|     ###|      ###|       null|WriteSerializable|         true|[numFiles -> 2, n...|

You can access older versions with the timestamp or the version number.

**Example with timestamp:**

```python
spark.read.format("delta").option("timestampAsOf", timestamp).load(path)
```

**Example with version:**

```python
spark.read.format("delta").option("versionAsOf", version).load(path)
```

The benefits of Delta Lake are the following:

- Automated. You don't need to think about how to version your data
- Light
- It looks like a code versioning

Disadvantages:

- If you don't need to think about how to version your data, you always have to think of how to rollback or launch a replay
- Delta Lake is for data, not for your model. By versioning your model, you can link a state of your model to a state of your data. But it's not automatic.

## Conclusion

I think it is too soon for me to correctly evaluate Delta Lake. 

What I can say is that we chose a custom versioning system when there was no other option. And now, we chose Delta Lake because we also use Databricks. We wanted to use Delta Lake performance optimisations too. Using time travel from Delta Lake comes naturally.

Automated solutions seem more attractive. That doesn't mean that you have nothing to do when it is set up. You must imagine how to do your rollbacks and replays.

Note that you can find other ways to make data versioning with some tools like [DVC](https://dvc.org/).

Thank you for reading. 
