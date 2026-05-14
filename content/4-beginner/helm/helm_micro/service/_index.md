---
title : "Test the Service"
date: 2024-01-01
weight : 4
chapter : false
pre : " <b> 6.3.4</b> "
---

To test the service our eksdemo Chart created, we’ll need to get the name of the ELB endpoint that was generated when we deployed the Chart:

```
kubectl get svc ecsdemo-frontend -o jsonpath="{.status.loadBalancer.ingress[*].hostname}"; echo
```

Copy that address, and paste it into a new tab in your browser. You should see something similar to:

![deployeksdemo](/images/beginner/microservices/9.png?width=90pc)