---
title : "Truy cập vào Bảng điều khiển"
date: 2024-01-01
weight : 2
chapter : false
pre : " <b> 4.1.2 <b> "
---


Bây giờ chúng ta có thể truy cập vào bảng điều khiển Kubernetes

Trên môi trường cloud9, click **Tools / Preview / Preview Running Application**
Di chuyển trỏ chuột **vào phía cuối URL** và và thêm vào dòng ở phía dưới:

```
/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
```

Trình duyệt Cloud9 Preview có vẻ không hỗ trợ xác thực bằng token, nên sau khi có màn hình đăng nhập trong tab trình duyệt Cloud9 Preview, nhấn nút Pop Out để mở màn hình đăng nhập trong một tab trình duyệt thông thường, như bên dưới:

![pic1](/images/beginner/1.png?featherlight=false&width=90pc?width=90pc)

Mở tab terminal mới và enter
```
aws eks get-token --cluster-name eksworkshop-eksctl | jq -r '.status.token'
```
Copy câu lệnh phía trên để lấy token và dán vào mục Token ở trang web

![pic1](/images/beginner/4.png?featherlight=false&width=90pc?width=90pc)

Sau đó ấn Sign in để đăng nhập

![pic1](/images/beginner/3.png?featherlight=false&width=90pc?width=90pc)