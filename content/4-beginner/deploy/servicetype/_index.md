---
title : "Let's check Service Types"
date: 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.3 <b> "
---

Before we bring up the frontend service, let’s take a look at the service types we are using: This is `~/environment/ecsdemo-frontend/kubernetes/service.yaml` for our frontend service:

```
apiVersion: v1
kind: Service
metadata:
  name: ecsdemo-frontend
spec:
  selector:
    app: ecsdemo-frontend
  type: LoadBalancer
  ports:
   -  protocol: TCP
      port: 80
      targetPort: 3000
```

Notice type: LoadBalancer: This will configure an ELB to handle incoming traffic to this service.

Compare this to ~/environment/ecsdemo-nodejs/kubernetes/service.yaml for one of our backend services:

```
apiVersion: v1
kind: Service
metadata:
  name: ecsdemo-nodejs
spec:
  selector:
    app: ecsdemo-nodejs
  ports:
   -  protocol: TCP
      port: 80
      targetPort: 3000
```

Notice there is no specific service type described. When we check [the kubernetes documentation](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) we find that the default type is `ClusterIP`. This Exposes the service on a cluster-internal IP. Choosing this value makes the service only reachable from within the cluster.