---
title : "Launch EKS"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 3.2 <b> "
---


{{% notice warning %}}
DO NOT PROCEED with this step unless you have [validated the IAM role](/2-prerequisites/workspaceiam) in use by the Cloud9 IDE. You will not be able to run the necessary kubectl commands in the later modules unless the EKS cluster is built using the IAM role.
{{% /notice %}}

## Create an EKS cluster

{{% notice warning %}}
eksctl version must be 0.58.0 or above to deploy EKS 1.21, [click here](/3-eksctl/prerequisites) to get the latest version.
{{% /notice %}}

Create an eksctl deployment file (eksworkshop.yaml) use in creating your cluster using the following syntax:

```
cat << EOF > eksworkshop.yaml
---
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: eksworkshop-eksctl
  region: ${AWS_REGION}
  version: "1.21"

availabilityZones: ["${AZS[0]}", "${AZS[1]}", "${AZS[2]}"]

managedNodeGroups:
- name: nodegroup
  desiredCapacity: 3
  instanceType: t3.small
  ssh:
    enableSsm: true

# To enable all of the control plane logs, uncomment below:
# cloudWatch:
#  clusterLogging:
#    enableTypes: ["*"]

secretsEncryption:
  keyARN: ${MASTER_ARN}
EOF
```
![createkmskey](/images/prerequisites/createyaml.png?width=90pc)

Next, use the file you created as the input for the eksctl cluster creation.

{{% notice info %}}
We are deliberatly launching at least one Kubernetes version behind the latest available. Please review [Amazon EKS Kubernetes versions](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html) to determine what supported versions are currently available. This allows you to perform the cluster upgrade lab.
{{% /notice %}}

```
eksctl create cluster -f eksworkshop.yaml
```

![createkmskey](/images/prerequisites/createcluster.png?width=90pc)


{{% notice info %}}
Launching EKS and all the dependencies will take approximately 15 minutes
{{% /notice %}}