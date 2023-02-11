---
title : "Create an AWS account"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 2.2.1</b> "
---
{{% notice warning %}}
Your account must have the ability to create new IAM roles and scope other IAM permissions.
{{% /notice %}}

1. If you don’t already have an AWS account with Administrator access: [create one now by clicking here](https://aws.amazon.com/getting-started/)

2. Once you have an AWS account, ensure you are following the remaining workshop steps as an IAM user with administrator access to the AWS account: [Create a new IAM user to use for the workshop](https://us-east-1.console.aws.amazon.com/iam/home?region=us-east-1#/users$new?step=details)

3. Enter the user details:

![iam-create](/images/Startworkshop/iam-1-create-user.png?featherlight=false&width=90pc?width=90pc)

4. Attach the AdministratorAccess IAM Policy:

![iam-policy](/images/Startworkshop/iam-2-attach-policy.png?featherlight=false&width=90pc?width=90pc)

5. Click to create the new user:

![iam-new-user](/images/Startworkshop/iam-3-create-user.png?featherlight=false&width=90pc?width=90pc)

6. Take note of the login URL and save:

![iam-save-url](/images/Startworkshop/iam-4-save-url.png?featherlight=false&width=90pc?width=90pc)