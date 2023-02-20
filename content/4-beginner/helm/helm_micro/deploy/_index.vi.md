---
title : "Deploy the eksdemo Chart"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 6.3.3</b> "
---

Use the dry-run flag to test our templates
To test the syntax and validity of the Chart without actually deploying it, we’ll use the `--dry-run` flag.

The following command will build and output the rendered templates without installing the Chart:

```
helm install --debug --dry-run workshop ~/environment/eksdemo
```

![deployeksdemo](/images/beginner/microservices/6.png?width=90pc)


Confirm that the values created by the template look correct.

Deploy the chart
Now that we have tested our template, let’s install it.

```
helm install workshop ~/environment/eksdemo
```


![deployeksdemo](/images/beginner/microservices/7.png?width=90pc)


Similar to what we saw previously in the [nginx Helm Chart example](/4-beginner/helm/helm_nginx), an output of the command will contain the information about the deployment status, revision, namespace, etc, similar to:


```
NAME: workshop
LAST DEPLOYED: Sat Jul 17 08:47:32 2021
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
```

In order to review the underlying services, pods and deployments, run:

```
kubectl get svc,po,deploy
```

![deployeksdemo](/images/beginner/microservices/8.png?width=90pc)