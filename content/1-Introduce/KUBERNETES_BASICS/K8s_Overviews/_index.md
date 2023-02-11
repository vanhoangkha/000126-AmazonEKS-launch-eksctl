---
title : "Kubernetes Overview"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 1.3.3  </b> "
---
_Kubernetes objects are entities that are used to represent the state of the cluster._

_An object is a “record of intent” – once created, the cluster does its best to ensure it exists as defined. This is known as the cluster’s “desired state.”_

_Kubernetes is always working to make an object’s “current state” equal to the object’s “desired state.” A desired state can describe:_

- What pods (containers) are running, and on which nodes
- IP endpoints that map to a logical group of containers
- How many replicas of a container are running
- And much more…

_Let’s explain these k8s objects in a bit more detail.._