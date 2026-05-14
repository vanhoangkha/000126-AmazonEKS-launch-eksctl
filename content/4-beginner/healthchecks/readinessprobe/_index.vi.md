---
title : "Configure Readiness Probe"
date: 2024-01-01
weight : 2
chapter : false
pre : " <b> 7.2</b> "
---

Configure the Probe
Run the following code block to populate **~/environment/healthchecks/readiness-deployment.yaml.** The readinessProbe definition explains how a linux command can be configured as healthcheck. We create an empty file **/tmp/healthy** to configure readiness probe and use the same to understand how kubelet helps to update a deployment with only healthy pods.

```
cat <<EoF > ~/environment/healthchecks/readiness-deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: readiness-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: readiness-deployment
  template:
    metadata:
      labels:
        app: readiness-deployment
    spec:
      containers:
      - name: readiness-deployment
        image: alpine
        command: ["sh", "-c", "touch /tmp/healthy && sleep 86400"]
        readinessProbe:
          exec:
            command:
            - cat
            - /tmp/healthy
          initialDelaySeconds: 5
          periodSeconds: 3
EoF
```

![readiness](/images/beginner/healthchecks/9.png?width=90pc)

We will now create a deployment to test readiness probe:

```
kubectl apply -f ~/environment/healthchecks/readiness-deployment.yaml
```

![readiness](/images/beginner/healthchecks/10.png?width=90pc)

The above command creates a deployment with 3 replicas and readiness probe as described in the beginning.

```
kubectl get pods -l app=readiness-deployment
```

![readiness](/images/beginner/healthchecks/11.png?width=90pc)

The output looks similar to below:


```
NAME                                    READY     STATUS    RESTARTS   AGE
readiness-deployment-7869b5d679-922mx   1/1       Running   0          31s
readiness-deployment-7869b5d679-vd55d   1/1       Running   0          31s
readiness-deployment-7869b5d679-vxb6g   1/1       Running   0          31s
```

Let us also confirm that all the replicas are available to serve traffic when a service is pointed to this deployment.

```
kubectl describe deployment readiness-deployment | grep Replicas:
```

![readiness](/images/beginner/healthchecks/12.png?width=90pc)

The output looks like below:


```
Replicas:               3 desired | 3 updated | 3 total | 3 available | 0 
unavailable
```

Introduce a Failure
Pick one of the pods from above 3 and issue a command as below to delete the **/tmp/healthy** file which makes the readiness probe fail.

```
kubectl exec -it <YOUR-READINESS-POD-NAME> -- rm /tmp/healthy
```

![readiness](/images/beginner/healthchecks/13.png?width=90pc)

**readiness-deployment-548975dcc5-ggdtc** was picked in our example cluster. The **/tmp/healthy** file was deleted. This file must be present for the readiness check to pass. Below is the status after issuing the command.

```
kubectl get pods -l app=readiness-deployment
```

![readiness](/images/beginner/healthchecks/14.png?width=90pc)

The output looks similar to below:

```
NAME                                    READY     STATUS    RESTARTS   AGE
readiness-deployment-7869b5d679-922mx   0/1       Running   0          4m
readiness-deployment-7869b5d679-vd55d   1/1       Running   0          4m
readiness-deployment-7869b5d679-vxb6g   1/1       Running   0          4m
```

Traffic will not be routed to the first pod in the above deployment. The ready column confirms that the readiness probe for this pod did not pass and hence was marked as not ready.
We will now check for the replicas that are available to serve traffic when a service is pointed to this deployment.

```
kubectl describe deployment readiness-deployment | grep Replicas:
```
![readiness](/images/beginner/healthchecks/15.png?width=90pc)

The output looks like below:

```
Replicas:               3 desired | 3 updated | 3 total | 2 available | 1 unavailable
```

When the readiness probe for a pod fails, the endpoints controller removes the pod from list of endpoints of all services that match the pod.