---
title : "K8s Objects Detail (2/2)"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 1.3.5  </b> "
---

## [ReplicaSet](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/)

_A ReplicaSet is a controller that ensures the stability of replicas (number and state of PODs, replicas) while running._

## [Job](https://kubernetes.io/docs/concepts/workloads/controllers/job/)

_When deploying and operating systems, we will have many tasks (Jobs) that need to be performed periodically or once. Jobs run in K8s will execute within Pods. Pods will be created when a Job runs and will end when the Job is successful. When a Job is deleted, the related Pods will also be deleted._.

## [Service](https://kubernetes.io/docs/concepts/services-networking/service/)

_A Kubernetes service is a resource that defines a set of pods or a group of pods providing the same service and access policy to those pods. For services, Kubernetes also provides various types of services to cater to different requirements in the IT industry_.

## [Label](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/)

_Labels in Kubernetes are key-value pairs that are assigned to objects within the cluster such as Pods, and they are used to quickly identify and categorize these objects. They allow us to add descriptive metadata to our objects and perform operations based on those labels, such as grouping and selecting objects based on specific criteria_.