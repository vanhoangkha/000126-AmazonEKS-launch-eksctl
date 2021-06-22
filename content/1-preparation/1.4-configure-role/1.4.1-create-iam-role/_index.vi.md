+++
title = "Tạo IAM Role"
date = 2021
weight = 1
chapter = false
pre = "<b>1.4.1 </b>"
+++

#### Tạo IAM Role cho Workspace

1. Click vào biểu tượng Cloud9.
    + Click **Go To Your Dashboard**.
  
![Configure Role](/images/1-eks/role1.png?width=90pc)

2. Từ giao diện dashboard của Cloud9 chúng ta sẽ tiến hành truy cập vào giao diện của dịch vụ IAM.

![Configure Role](/images/1-eks/role2.png?width=90pc)

3. Trong giao diện quản trị của dịch vụ IAM.
     + Click **Roles**.
     + Click **Create role**.

![Configure Role](/images/1-eks/role3.png?width=90pc)
 
4. Tại trang **Create role**.
    + Click **EC2**.
    + Click **Next: Permissions**.

![Configure Role](/images/1-eks/role4.png?width=90pc)

5. Tại trang Attach permissions policies
    + Click chọn **AdministratorAccess**.
    + Click **Next: Tags**.

![Configure Role](/images/1-eks/role5.png?width=90pc)

6. Tại trang Add tags.
    + Click **Next: Review**.
7. Tại trang Review.
    + Đặt tên **Role name** : eksworkshop-admin
    + Click **Create role**.

![Configure Role](/images/1-eks/role6.png?width=90pc)
