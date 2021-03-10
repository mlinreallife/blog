---
title: "Kubernetes - Be sure of being ready for real zero downtime deployment"
date: 2020-08-27T06:11:10+02:00
draft: true
description: Readiness is an important concept in Kubernetes that avoids you getting a temporary error when deploying.
It's a key to get real zero downtime deployment.
---

TLDR;

Readiness is an important concept in Kubernetes that avoids you getting a temporary error when deploying.
It's a key to get real zero downtime deployment. Don't forget it!

## The problem

Let's suppose that you deploy an application.
When doing it, you notice that your users receive a temporary error when deploying the application.

Oops.

## The explanation

Let's suppose that you have one replica. The process is the following when deploying:

- In the beginning, you have the old pod
- A new pod is created
- When the new pod is ready, the old one is removed

The problem is this concept of readiness. If you do nothing, you get the default configuration and there's almost no doubt that it's not what you want. The default configuration from the [Kubernetes documentation](https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/) is the following one:

> If a Container does not provide a readiness probe, the default state is Success

## The solution

You can configure a readiness probe by adding something like that in your yaml file:

```
readinessProbe:
  httpGet:
    path: /status
    port: 8000
  initialDelaySeconds: 10
  periodSeconds: 5
```

This way, we have a custom readiness probe. We check that a specific path is available before declaring the pod is ready to receive input traffic.

I let you check the [documentation](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/) for more information.
