---
title: "Different ways to do data versioning"
date: 2020-09-12T07:11:10+02:00
draft: false
---

I have experienced 2 ways of doing data versioning and would like to share it with you.

It was always in a batch context to do supervised or unsupervised learning.

## What is data versioning? 

Data versioning is about keeping snapshots of the state of your data.
This way, you can see how were the data at certain periods of time.

## Why doing data versioning?

There are many benefits:
 
- Rollbacks and replays on a specific date.

- Debug. This is the most important purpose for me. You can dive into a previous state of the data and understand what happens.

- Debug with a reproducible state. By versioning your model and your data, you get a reproducible state. It can be helpful if you want to explain one weird prediction for instance.

## Manual versioning

You can set a versioning manually. For instance, all your data can be partitioned by a date. Suppose you get regular updates of data each day. In an HDFS datalake, you can partition your data this way:

- data
    - year=2019
        - month=02
            -day=01
            -day=02
            -day=03
            - etc.
            
In this case, your data are immutable.
 
To play or replay a specific date, you must pass it in your deployment. 

The benefits of a custom versioning are the following:

- Flexible. You have the control
- Easy to rollback. You develop manually the versioning. Then, you're ready to rollback or replay.

But there are disadvantages:

- Heavy solution. You have many files in your datalake.
- You have to develop, maintain and debug the solution. 

## Automated versioning with DeltaLake

X announced DeltaLake saying that it's a bigger innovation than Spark.

Maybe, it was for the *wahoo* effect. But it's true that DeltaLake is quite impressive. You put under a datalake (HDFS, DBDS, etc) and then you get ACID transactions, updates, deletes and time travel with data versioning.

As explained in the [website](https://delta.io/):
*Delta Lake provides snapshots of data enabling developers to access and revert to earlier versions of data for audits, rollbacks or to reproduce experiments.*

To do that, you have to deal with a delta format instead of a parquet format for instance.

Then, to see the different versions of your data, you can do:

**CODE**

You get:

**TABLE**

You can access older versions with the timestamp or the version number.

**Example with timestamp**

**Example with version**

The benefits of DeltaLake are the following:

- Automated. You don't need to think about how to version your data
- Light
- It looks like a code versioning

Disadvantages:

- If you don't need to think about how to version your data, you always have to think of how to rollback or launch a replay
- DeltaLake is for data, not for your model. By versioning your model, you can link a state of your model to a state of your data. But it's not automatic.

## Conclusion

I think it is too soon for me to correctly evaluate Delta Lake. 

What I can say is that we chose a manual versioning when there was no other option. And now, we chose Delta Lake because we wanted to use it to do ACID transactions and get performance optimisations. Using time travel from Delta Lake comes naturally then.

Automated solutions seem more attractive. That doesn't mean that you have nothing to do when it is set up. You must imagine how to do your rollbacks and replays.

Note that that you can find other ways to make data versioning with some tools like DVC.

Thank you for reading
