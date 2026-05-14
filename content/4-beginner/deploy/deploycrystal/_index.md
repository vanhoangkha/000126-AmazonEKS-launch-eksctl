---
title : "Deploy Crystal BackEnd API"
date: 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.2 <b> "
---


Let’s bring up the Crystal Backend API!

Copy/Paste the following commands into your Cloud9 workspace:


```
cd ~/environment/ecsdemo-crystal
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml

```

![deploynodejs](/images/beginner/deploycrystal.png?width=90pc)


We can watch the progress by looking at the deployment status:

```
kubectl get deployment ecsdemo-crystal
```

![deploycrystal](/images/beginner/checkstatuscrystal.png?width=90pc)