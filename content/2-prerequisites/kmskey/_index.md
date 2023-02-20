---
title : "Create an AWS KMS Custom Managed Key (CMK)"
date :  "`r Sys.Date()`" 
weight : 9
chapter : false
pre : " <b> 2.9 <b> "
---


Create a CMK for the EKS cluster to use when encrypting your Kubernetes secrets:

```
aws kms create-alias --alias-name alias/eksworkshop --target-key-id $(aws kms create-key --query KeyMetadata.Arn --output text)
```

![createkmskey](/images/prerequisites/createkmskey.png?width=90pc)

Let’s retrieve the ARN of the CMK to input into the create cluster command.

```
export MASTER_ARN=$(aws kms describe-key --key-id alias/eksworkshop --query KeyMetadata.Arn --output text)
```

![createkmskey](/images/prerequisites/CMK.png?width=90pc)

We set the MASTER_ARN environment variable to make it easier to refer to the KMS key later.

Now, let’s save the MASTER_ARN environment variable into the bash_profile

```
echo "export MASTER_ARN=${MASTER_ARN}" | tee -a ~/.bash_profile
```

![createkmskey](/images/prerequisites/savekms.png?width=90pc)
