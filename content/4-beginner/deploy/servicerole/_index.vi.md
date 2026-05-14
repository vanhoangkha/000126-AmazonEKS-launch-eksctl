---
title : "Ensure the ELB Service Role exists"
date: 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.4 <b> "
---

In AWS accounts that have never created a load balancer before, it’s possible that the service role for ELB might not exist yet.

We can check for the role, and create it if it’s missing.

Copy/Paste the following commands into your Cloud9 workspace:

```
aws iam get-role --role-name "AWSServiceRoleForElasticLoadBalancing" || aws iam create-service-linked-role --aws-service-name "elasticloadbalancing.amazonaws.com"
```

![checkrole](/images/beginner/checkrole.png?width=90pc)