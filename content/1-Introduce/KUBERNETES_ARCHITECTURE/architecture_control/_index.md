---
title : "Control Plane"
date: 2024-01-01
weight : 2
chapter : false
pre : " <b> 1.2.2 </b> "
---

![Architectural](/images/Introduction/Controlplane/1.png?featherlight=false&width=90pc)

- One or More API Servers: Entry point for REST / kubectl

- etcd: Distributed key/value store

- Controller-manager: Always evaluating current vs desired state

- Scheduler: Schedules pods to worker nodes

Check out [the official Kubernetes documentation](https://kubernetes.io/docs/concepts/overview/components/#master-components) for a more in-depth explanation of control plane components.