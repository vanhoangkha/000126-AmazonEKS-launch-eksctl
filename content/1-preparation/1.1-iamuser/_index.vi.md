+++
title = "Chuẩn bị IAM User"
date = 2021
weight = 1
chapter = false
pre = "<b>1.1 </b>"
+++

#### Tạo IAM user với quyền admin

Chúng ta sẽ tiến hành tạo một IAM user có tên là awsstudent-eks có quyền admin để sự dụng trong chuỗi bài lab Amazon EKS workshop.

1. Truy cập vào giao diện quản lý của dịch vụ IAM.
    + Click **Users**.
![Tạo IAM User](/images/1-eks/createiam.png?width=90pc)
    + Click **Add User**.

2. Tại trang **Add User** điền tên user là **awsstudent-eks**
    + Click chọn **Programmatic access**.
    + Click chọn **AWS Management Console access**.
    + Click chọn **Custom password**.
    + Đặt password tùy chọn và lưu lại thông tin password. ( Ở đây chúng ta sẽ đặt là awsstudent123!)
    + Bỏ chọn **User must create a new password at next sign-in**.
    + Click **Next: Permission**.
  
![Tạo IAM User](/images/1-eks/createiam2.png?width=90pc)

3. Click chọn **Attach existing policies directly**.
    + Click chọn policy **Administrator Access**.
    + Click **Next :Tags**.

![Tạo IAM User](/images/1-eks/createiam3.png?width=90pc)

4. Click **Next : Preview**.
5. Click **Create user**.
6. Click **Download .csv** để download thông tin accesskey của user **awsstudent-eks**.
    + Click vào đường link để tiến hành login vào account của bạn bằng user **awsstudent-eks**.
    + Tiếp theo chúng ta sẽ tiếp tục bài lab sử dụng user **awsstudent-eks**.
![Tạo IAM User](/images/1-eks/createiam4.png?width=90pc)