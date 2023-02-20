---
title : "Find the Service Address"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 5.6 <b> "
---


Now that we have a running service that is `type: LoadBalancer` we need to find the ELB’s address. We can do this by using the `get services` operation of kubectl:

```
kubectl get service ecsdemo-frontend
```

![elb](/images/beginner/elbaddress.png?width=90pc)

Notice the field isn’t wide enough to show the FQDN of the ELB. We can adjust the output format with this command:

```
kubectl get service ecsdemo-frontend -o wide
```

![elb](/images/beginner/checkwide.png?width=90pc)

If we wanted to use the data programatically, we can also output via json. This is an example of how we might be able to make use of json output:

```
ELB=$(kubectl get service ecsdemo-frontend -o json | jq -r '.status.loadBalancer.ingress[].hostname')

curl -m3 -v $ELB
```

![elb](/images/beginner/jsonoutput.png?width=90pc)


{{% notice tip %}}
It will take several minutes for the ELB to become healthy and start passing traffic to the frontend pods.
{{% /notice %}}

You should also be able to copy/paste the loadBalancer hostname into your browser and see the application running. Keep this tab open while we scale the services up on the next page.