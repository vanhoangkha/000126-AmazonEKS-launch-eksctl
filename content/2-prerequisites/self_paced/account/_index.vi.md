---
title : "Tạo tài khoản AWS"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 2.2.1</b> "
---

{{% notice warning %}}
Tài khoản của bạn phải có khả năng tạo vai trò IAM mới và giới hạn quyền IAM
{{% /notice %}}

1. Nếu bạn chưa có tài khoản AWS với quyền truy cập Administrator: hãy tạo một cái bằng cách [click vào đây](https://aws.amazon.com/getting-started/)

2. Khi bạn đã có tài khoản AWS, Đảm bảo rằng bạn đang theo các bước còn lại của workshop như một người dùng IAM với quyền truy cập quản trị viên đến tài khoản AWS.: [Tạo một người dùng IAM mới cho workshop](https://us-east-1.console.aws.amazon.com/iam/home?region=us-east-1#/users$new?step=details)

3. Nhập thông tin user:

![iam-create](/images/Startworkshop/iam-1-create-user.png?featherlight=false&width=90pc?width=90pc)

4. Gán chính sách quyền quản trị viên:

![iam-policy](/images/Startworkshop/iam-2-attach-policy.png?featherlight=false&width=90pc?width=90pc)

5. Nhấp tạo mới user:

![iam-new-user](/images/Startworkshop/iam-3-create-user.png?featherlight=false&width=90pc?width=90pc)

6. Note lại url đăng nhập và lưu::

![iam-save-url](/images/Startworkshop/iam-4-save-url.png?featherlight=false&width=90pc?width=90pc)