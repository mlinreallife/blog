---
title: "How can you connect to MLFlow registry remotely?"
date: 2020-09-18T17:01:10+02:00
draft: true
---

TL;DR:
MLFlow is a tool to do model versioning. You can track your metrics, your parameters, log your model, register it in a *None*, *Staging* or *Production* stage. You can retrieve your model and all the associated informated using MLFlow.
It goes without saying that it's helpful when you are looking for reproducibility and MLOps. And who is not looking for reproducibility and MLOps?

But, I've recently experienced difficulties connecting to MLFlow registry from outside. This is why I've decided to write a small tutorial about that. This tutorial will blow your mind ... or maybe will just help you a bit.

## Caution
This tutorial is for people that already know MLFlow model registry but don't know how to use it from outside.

## Situation
You have a mlflow registry in a location named A.

You are in a location named B and you want to retrieve a model from A.

## Create your secrets 
1. On the Databricks CLI, create a secret scope in your B environment:

```
databricks secrets create-scope --scope <scope>
```

2. Pick a unique name for the target workspace, which we'll refer to. Then create three secrets:
- ```databricks secrets put --scope <scope> --key <prefix>-host```. *Enter the hostname of the A model registry workspace*.
- ```databricks secrets put --scope <scope> --key <prefix>-token```. *Enter the access token from the A model registry workspace*.
- ```databricks secrets put --scope <scope> --key <prefix>-workspace-id```. *Enter the workspace ID for the A model registry workspace which can be found in the URL of any page in the workspace*.

## Indicate where you want to be connected

Then, you have to create a registry_uri in B doing something like that:

```python
model_registry_secrets_scope = "<scope>"
model_registry_secrets_prefix = "<prefix>"

registry_uri = f"databricks://{model_registry_secrets_scope}:{model_registry_secrets_prefix}"
```

## Retrieve your model
Use this registry_uri with MLFlow doing something like that in B:

```python

import mlflow

mlflow.set_tracking_uri(registry_uri)

model_name = "<name-of-your-model>"
stage = '<name-of-your-stage>'

model = mlflow.xgboost.load_model(
    model_uri=f"models:/{model_name}/{stage}"
)
```

Woohoo! You get your model! If you're like me, you're super excited! But sometimes, it's not enough :confused:. 

## Retrieve information about your models

When you want to retrieve information about your models, you need to go through *MLFlowClient*. 

Same here, you can use the *registry_uri* in B:

```python
customized_mlflow_client = mlflow.tracking.MlflowClient(tracking_uri=None, registry_uri=registry_uri)

customized_mlflow_client.list_registered_models()
```

Here you are! :happy:

Thank you for reading. I hope it has helped you a bit. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that or if I can help.
Many people have helped me to understand this problem. Then, I would be delighted to do the same :happy:.

MLFlow is a tool I admire. It was designed by Databricks. This company also offers services to introduce you to this one. I'm not working for Databricks. It's not an advertisement, just a piece of information I give to you.
