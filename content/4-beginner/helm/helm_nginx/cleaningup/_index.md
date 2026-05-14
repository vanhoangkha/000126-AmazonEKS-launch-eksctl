---
title : "Cleanup"
date: 2024-01-01
weight : 5
chapter : false
pre : " <b> 6.2.5 <b> "
---


To remove all the objects that the Helm Chart created, we can use Helm uninstall.

Before we uninstall our application, we can verify what we have running via the Helm list command:

```
helm list
```

You should see output similar to below, which show that mywebserver is installed:

```
NAME            NAMESPACE       REVISION        UPDATED                                 STATUS          CHART           APP VERSION
mywebserver     default         1               2021-07-15 13:52:34.563653342 +0000 UTC deployed        nginx-9.3.7     1.21.1
```

It was a lot of fun; we had some great times sending HTTP back and forth, but now its time to uninstall this deployment. To uninstall:

```
helm uninstall mywebserver
```

And you should be met with the output:

```
release "mywebserver" uninstalled
```

kubectl will also demonstrate that our pods and service are no longer available:

```
kubectl get pods -l app.kubernetes.io/name=nginx
kubectl get service mywebserver-nginx -o wide
```

As would trying to access the service via the web browser via a page reload.

With that, cleanup is complete.