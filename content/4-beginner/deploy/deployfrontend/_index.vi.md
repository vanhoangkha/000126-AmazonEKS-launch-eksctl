---
title : "Deploy FrontEnd Service"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5.5 <b> "
---



Copy/Paste the following commands into your Cloud9 workspace:

```
cd ~/environment/ecsdemo-frontend
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
```

![deployfrontend](/images/beginner/deployfrontend.png?width=90pc)

We can watch the progress by looking at the deployment status:

```
kubectl get deployment ecsdemo-frontend
```

![deployfrontend](/images/beginner/checkstatusfrontend.png?width=90pc)