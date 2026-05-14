---
title : "K8s Objects Detail (1/2)"
date: 2024-01-01
weight : 4
chapter : false
pre : " <b> 1.3.4  </b> "
---

## [Pod](https://kubernetes.io/docs/concepts/workloads/pods/)

_When an application is packaged, it can run in an isolated container. Although we can run isolated containers like starting a monolithic application, Kubernetes does not work that way. Kubernetes uses the concept of a pod to group containers together. A pod is a group of containers that share resources and network, and containers within a pod can communicate with each other as if on a single server while still maintaining necessary isolation._

## [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)

_A DaemonSet is a type of service management that operates on Pods with a rather unique function by ensuring that the service Pod will run on all nodes in a Kubernetes Cluster. (Or on specific **nodes**  within the **Kubernetes_**.

## [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)

_In Kubernetes, the Deployment object is the main entity responsible for deploying and managing our application. It allows us to deploy Pods, update Pods, rollback Pods, and ReplicaSets._.