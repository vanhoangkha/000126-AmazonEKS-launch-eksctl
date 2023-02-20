---
title : "Scale the Backend Services"
date :  "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 5.7 <b> "
---


When we launched our services, we only launched one container of each. We can confirm this by viewing the running pods:

```
kubectl get deployments
```

![getdeployment](/images/beginner/getdeployments.png?width=90pc)

Now let’s scale up the backend services:

```
kubectl scale deployment ecsdemo-nodejs --replicas=3
kubectl scale deployment ecsdemo-crystal --replicas=3
```
![getdeployment](/images/beginner/scalebackend.png?width=90pc)

Confirm by looking at deployments again:

```
kubectl get deployments
```

![getdeployment](/images/beginner/lookdeploy.png?width=90pc)

Also, check the browser tab where we can see our application running. You should now see traffic flowing to multiple backend services.

![getdeployment](/images/beginner/giphy.gif?width=90pc)
