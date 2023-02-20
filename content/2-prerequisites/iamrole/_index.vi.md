---
title : "Tạo IAM role cho workspace"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 2.5 </b> "
---
1. Truy cập vào  [this deep link to create an IAM role with Administrator access](https://console.aws.amazon.com/iam/home#/roles$new?step=review&commonUseCase=EC2%2BEC2&selectedUseCase=EC2&policies=arn:aws:iam::aws:policy%2FAdministratorAccess&roleName=eksworkshop-admin).
2. Xác nhận rằng **AWS service** và **EC2** đã được chọn, sau đó nhấn **Next: Permissions** để xem quyền.

![iam-role](/images/prerequisites/create-role.png?featherlight=false&width=90pc?width=90pc)

1. Chắc chắn rằng **AdministratorAccess** đã được chọn, sau đó click **Next: Tags** để thêm tag.

![iam-role](/images/prerequisites/create-role-2.png?featherlight=false&width=90pc?width=90pc)

4. Giữ nguyên mặc định, và click **Next: Review** để xem.

![iam-role](/images/prerequisites/create-role-3.png?featherlight=false&width=90pc?width=90pc)

5. Nhập **eksworkshop-admin** cho tên, và click **Create role**.

![iam-role](/images/prerequisites/create-role-4.png?featherlight=false&width=90pc?width=90pc)