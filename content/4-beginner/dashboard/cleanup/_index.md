---
title : "Cleanup"
date: 2024-01-01
weight : 3
chapter : false
pre : " <b> 4.1.3 <b> "
---


Stop the proxy and delete the dashboard deployment

```
# kill proxy
pkill -f 'kubectl proxy --port=8080'

# delete dashboard
kubectl delete -f https://raw.githubusercontent.com/kubernetes/dashboard/${DASHBOARD_VERSION}/aio/deploy/recommended.yaml

unset DASHBOARD_VERSION
```