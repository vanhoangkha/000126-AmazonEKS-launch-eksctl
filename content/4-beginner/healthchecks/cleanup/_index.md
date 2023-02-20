---
title : "Cleanup"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 7.3</b> "
---

Our Liveness Probe example used HTTP request and Readiness Probe executed a command to check health of a pod. Same can be accomplished using a TCP request as described in the [documentation](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/).

```
kubectl delete -f ~/environment/healthchecks/liveness-app.yaml
kubectl delete -f ~/environment/healthchecks/readiness-deployment.yaml
```