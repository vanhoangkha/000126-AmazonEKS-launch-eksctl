---
title : "Create an IAM role for your Workspace"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 2.5 </b> "
---

1. Follow [this deep link to create an IAM role with Administrator access](https://console.aws.amazon.com/iam/home#/roles$new?step=review&commonUseCase=EC2%2BEC2&selectedUseCase=EC2&policies=arn:aws:iam::aws:policy%2FAdministratorAccess&roleName=eksworkshop-admin).
2. Confirm that **AWS service** and **EC2** are selected, then click **Next: Permissions** to view permissions.

![iam-role](/images/prerequisites/create-role.png?featherlight=false&width=90pc?width=90pc)

3. Confirm that **AdministratorAccess** is checked, then click **Next: Tags** to assign tags.

![iam-role](/images/prerequisites/create-role-2.png?featherlight=false&width=90pc?width=90pc)

4. Take the defaults, and click **Next: Review** to review.

![iam-role](/images/prerequisites/create-role-3.png?featherlight=false&width=90pc?width=90pc)

5. Enter **eksworkshop-admin** for the Name, and click **Create role**.

![iam-role](/images/prerequisites/create-role-4.png?featherlight=false&width=90pc?width=90pc)