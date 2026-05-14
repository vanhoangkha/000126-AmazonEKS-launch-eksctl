---
title : "Update IAM settings for your Workspace"
ddate: 2024-01-01
weight : 7
chapter : false
pre : " <b> 2.7 <b> "
---

{{% notice info %}}
Cloud9 normally manages IAM credentials dynamically. This isn’t currently compatible with the EKS IAM authentication, so we will disable it and rely on the IAM role instead.
{{% /notice %}}

To ensure temporary credentials aren’t already in place we will remove any existing credentials file as well as disabling **AWS managed temporary credentials**:

```
aws cloud9 update-environment  --environment-id $C9_PID --managed-credentials-action DISABLE
rm -vf ${HOME}/.aws/credentials

```
![workspaceiam](/images/prerequisites/rmvcredentials.png?width=90pc)

We should configure our aws cli with our current region as default.


{{% notice info %}}
If you are at an AWS event, ask your instructor which **AWS region** to use.
{{% /notice %}}

```
export ACCOUNT_ID=$(aws sts get-caller-identity --output text --query Account)
export AWS_REGION=$(curl -s 169.254.169.254/latest/dynamic/instance-identity/document | jq -r '.region')
export AZS=($(aws ec2 describe-availability-zones --query 'AvailabilityZones[].ZoneName' --output text --region $AWS_REGION))
```

![workspaceiam](/images/prerequisites/export.png?width=90pc)

Check if AWS_REGION is set to desired region

```
test -n "$AWS_REGION" && echo AWS_REGION is "$AWS_REGION" || echo AWS_REGION is not set
```
![workspaceiam](/images/prerequisites/checkregion.png?width=90pc)

Let’s save these into bash_profile

```
echo "export ACCOUNT_ID=${ACCOUNT_ID}" | tee -a ~/.bash_profile
echo "export AWS_REGION=${AWS_REGION}" | tee -a ~/.bash_profile
echo "export AZS=(${AZS[@]})" | tee -a ~/.bash_profile
aws configure set default.region ${AWS_REGION}
aws configure get default.region
```
![workspaceiam](/images/prerequisites/save.png?width=90pc)

## Validate the IAM role

Use the [GetCallerIdentity](https://docs.aws.amazon.com/cli/latest/reference/sts/get-caller-identity.html) CLI command to validate that the Cloud9 IDE is using the correct IAM role.

```
aws sts get-caller-identity --query Arn | grep eksworkshop-admin -q && echo "IAM role valid" || echo "IAM role NOT valid"
```

![workspaceiam](/images/prerequisites/validate.png?width=90pc)

If the IAM role is not valid, **DO NOT PROCEED**. Go back and confirm the steps on this page.

