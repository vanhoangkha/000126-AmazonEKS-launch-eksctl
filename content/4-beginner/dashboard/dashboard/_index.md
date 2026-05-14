---
title : "Deploy the Offical Kubernetes Dashboard"
date: 2024-01-01
weight : 1
chapter : false
pre : " <b> 4.1.1 <b> "
---

The official Kubernetes dashboard is not deployed by default, but there are instructions in [the official documentation](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)

We can deploy the dashboard with the following command:

```
export DASHBOARD_VERSION="v2.6.0"

kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/${DASHBOARD_VERSION}/aio/deploy/recommended.yaml
```

![nodes](/images/beginner/deploy.png?width=90pc)

Since this is deployed to our private cluster, we need to access it via a proxy. `kube-proxy` is available to proxy our requests to the dashboard service. In your workspace, run the following command:

```
kubectl proxy --port=8080 --address=0.0.0.0 --disable-filter=true &
```

![nodes](/images/beginner/startproxy.png?width=90pc)

This will start the proxy, listen on port 8080, listen on all interfaces, and will disable the filtering of non-localhost requests.

This command will continue to run in the background of the current terminal’s session.