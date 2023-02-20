---
title : "Cleanup the Applications"
date :  "`r Sys.Date()`" 
weight : 9
chapter : false
pre : " <b> 5.9 <b> "
---


To delete the resources created by the applications, we should delete the application deployments:

Undeploy the applications:

```
cd ~/environment/ecsdemo-frontend
kubectl delete -f kubernetes/service.yaml
kubectl delete -f kubernetes/deployment.yaml

cd ~/environment/ecsdemo-crystal
kubectl delete -f kubernetes/service.yaml
kubectl delete -f kubernetes/deployment.yaml

cd ~/environment/ecsdemo-nodejs
kubectl delete -f kubernetes/service.yaml
kubectl delete -f kubernetes/deployment.yaml
```