---
title : "Test the Cluster"
date: 2024-01-01
weight : 3
chapter : false
pre : " <b> 3.3 <b> "
---


## Test the cluster:

Confirm your nodes:

```
kubectl get nodes # if we see our 3 nodes, we know we have authenticated correctly
```

![nodes](/images/prerequisites/nodes.png?width=90pc)

## Update the kubeconfig file to interact with you cluster:

```
aws eks update-kubeconfig --name eksworkshop-eksctl --region ${AWS_REGION}
```
![nodes](/images/prerequisites/updatekubeconfig.png?width=90pc)

## Export the Worker Role Name for use throughout the workshop:

```
STACK_NAME=$(eksctl get nodegroup --cluster eksworkshop-eksctl -o json | jq -r '.[].StackName')
ROLE_NAME=$(aws cloudformation describe-stack-resources --stack-name $STACK_NAME | jq -r '.StackResources[] | select(.ResourceType=="AWS::IAM::Role") | .PhysicalResourceId')
echo "export ROLE_NAME=${ROLE_NAME}" | tee -a ~/.bash_profile
```

![nodes](/images/prerequisites/exportRole.png?width=90pc)

## Congratulations!

You now have a fully working Amazon EKS Cluster that is ready to use! Before you move on to any other labs, make sure to complete the steps on the next page to update the EKS Console Credentials.


