+++
title = "Truy cập vào dashboard"
date = 2021
weight = 2
chapter = false
pre = "<b>3.2 </b>"
+++

#### Truy cập vào dashboard

Sau khi triển khai dashboard, chúng ta sẽ tiến hành truy cập vào Kubernetes dashboard.

1. Tại giao diện Cloud9 Workspace.
    + Click **Tools**.
    + Click **Preview**.
    + Click **Preview Running Application**.

![dashboard](/images/3-dashboard/dashboard2.png?width=90pc)

2. Click chuột vào vị trí cuối của URL và dán thêm đoạn path dưới đây.
```
/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
```
![dashboard](/images/3-dashboard/dashboard3.png?width=90pc)

3. Cloud9 Preview browser không hỗ trợ chứng thực token, sau khi chúng ta truy cập vào giao diện login, Click vào nút **PopOut** để mở URL dashboard sang một tab trình duyệt mới.

![dashboard](/images/3-dashboard/dashboard4.png?width=90pc)

 URL Dashboard sẽ hiển thị trang Sign in ở tab trình duyệt mới như dưới đây.

![dashboard](/images/3-dashboard/dashboard5.png?width=90pc)

4. Mở 1 tab terminal mới trên Cloud9 Workspace, chạy lệnh dưới đây.
```
aws eks get-token --cluster-name eksworkshop-eksctl | jq -r '.status.token'
```
![dashboard](/images/3-dashboard/dashboard6.png?width=90pc)
5. Copy đoạn token sinh ra từ câu lệnh trên và paste vào phần **Enter token**.
    + Click **Sign in**.
![dashboard](/images/3-dashboard/dashboard7.png?width=90pc)

6. Chúc mừng bạn đã truy cập vào Kubernetes dashboard thành công.
![dashboard](/images/3-dashboard/dashboard8.png?width=90pc)

{{%notice tip%}}
Nếu proxy báo lỗi, bạn có thể thử log out và sign in vào Kubernetes dashboard lại.
{{%/notice%}}

