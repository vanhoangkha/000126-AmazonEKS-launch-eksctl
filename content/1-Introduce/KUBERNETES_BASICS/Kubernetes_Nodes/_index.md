---
title : "Kubernetes nodes"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 1.3.2  </b> "
---
_The machines that make up a Kubernetes cluster are called **nodes**._

_Nodes in a Kubernetes cluster may be physical, or virtual._

_There are two types of nodes:_

- _A Control-plane-node type, which makes up the [Control Plane](/1-introduce/kubernetes_architecture/architecture_control), acts as the “brains” of the cluster._

- _A Worker-node type, which makes up the [Data Plane](/1-introduce/kubernetes_architecture/architecture_worker), runs the actual container images (via pods)._

_We’ll dive deeper into how nodes interact with each other later in the presentation._