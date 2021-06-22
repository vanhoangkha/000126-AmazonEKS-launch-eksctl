+++
title = "Gán IAM Role"
date = 2021
weight = 2
chapter = false
pre = "<b>1.4.2 </b>"
+++

#### Gán IAM Role cho Workspace

1. Quay trở lại giao diện của Cloud9 Workspace.
    + Click vào icon tròn màu xám góc bên trên tay phải.
    + Click **Mange EC2 Instance**.

![Configure Role](/images/1-eks/role7.png?width=90pc)

2. Trong giao diện quản lý EC2.
    + Click chọn EC2 instance của Cloud9 Workspace.
    + Click **Actions**.
    + Click **Security**.
    + Click **Modify IAM role**.

![Configure Role](/images/1-eks/role8.png?width=90pc)

3. Trong trang **Modify IAM role**.
    + Click chọn **eksworkshop-admin** role.
    + Click **Save**.

![Configure Role](/images/1-eks/role9.png?width=90pc)

