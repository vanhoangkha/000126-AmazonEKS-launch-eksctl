---
title : "Deploy NodeJS BackEnd API"
date: 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.1 <b> "
---

Let’s bring up the NodeJS Backend API!

Copy/Paste the following commands into your Cloud9 workspace:

```
cd ~/environment/ecsdemo-nodejs
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
```

![deploynodejs](/images/beginner/deploynodejs.png?width=90pc)

We can watch the progress by looking at the deployment status:

```
kubectl get deployment ecsdemo-nodejs
```

![deploynodejs](/images/beginner/checkstatus.png?width=90pc)

