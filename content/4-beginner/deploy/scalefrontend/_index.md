---
title : "Scale the FrontEnd"
date: 2024-01-01
weight : 8
chapter : false
pre : " <b> 5.8 <b> "
---


Let’s scale up the frontend services:

```
kubectl get deployments
kubectl scale deployment ecsdemo-frontend --replicas=3
kubectl get deployments
```
![getdeployment](/images/beginner/scalefrontend.png?width=90pc)

Check the browser tab where we can see our application running. You should now see traffic flowing to multiple frontend services.

![getdeployment](/images/beginner/scalefe.gif?width=90pc)


