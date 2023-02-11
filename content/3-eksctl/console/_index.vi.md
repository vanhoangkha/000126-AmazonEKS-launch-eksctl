---
title : "Console Credentials"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 3.4 <b> "
---


Bước này là tùy chọn, vì gần tất cả nội dung của workshop sử dụng CLI. Tuy nhiên, nếu bạn muốn truy cập đầy đủ vào cluster của bạn trong EKS Console, bước này được khuyến cáo.

EKS Console cho phép bạn không chỉ xem các thông tin cấu hình của cluster, mà còn có thể xem các đối tượng cluster Kubernetes như Deployments, Pods và Nodes. Để có thể truy cập loại này, tài khoản IAM User hoặc Role trong Console cần được cấp quyền trong cluster.

Theo mặc định, tài khoản được sử dụng để tạo cluster được cấp quyền tự động. Theo quá trình thực hiện workshop, bạn đã tạo một cluster sử dụng tài khoản IAM tạm thời từ Cloud9. Điều này có nghĩa là bạn cần thêm tài khoản Console AWS vào cluster.

## Nhập chứng chỉ EKS Console của bạn vào cluster mới của bạn:

Người dùng IAM và Roles được ràng buộc với cluster Kubernetes EKS thông qua một ConfigMap tên là `aws-auth`. Chúng ta có thể sử dụng `eksctl` để làm điều này bằng một lệnh.

Bạn cần xác định chứng chỉ đúng để thêm cho truy cập AWS Console của bạn. Nếu bạn đã biết điều này, bạn có thể bỏ qua bước` eksctl create iamidentitymappin` bên dưới.

Nếu bạn đã xây dựng cluster của mình từ Cloud9 dưới dạng phần của hướng dẫn này, 
gọi nội dung sau trong môi trường của bạn để xác định Vai trò IAM hoặc ARN người dùng của bạn.

```
c9builder=$(aws cloud9 describe-environment-memberships --environment-id=$C9_PID | jq -r '.memberships[].userArn')
if echo ${c9builder} | grep -q user; then
	rolearn=${c9builder}
        echo Role ARN: ${rolearn}
elif echo ${c9builder} | grep -q assumed-role; then
        assumedrolename=$(echo ${c9builder} | awk -F/ '{print $(NF-1)}')
        rolearn=$(aws iam get-role --role-name ${assumedrolename} --query Role.Arn --output text) 
        echo Role ARN: ${rolearn}
fi
```
Với ARN của bạn, bạn có thể gửi lệnh để tạo bản đồ tương tác bên trong cluster.

```
eksctl create iamidentitymapping --cluster eksworkshop-eksctl --arn ${rolearn} --group system:masters --username admin
```

Lưu ý rằng quyền hạn có thể được giới hạn và chi tiết nhưng vì đây là cluster workshop, bạn đang thêm chứng chỉ console của mình như một quản trị viên.

Bây giờ bạn có thể xác thực bản ghi của bạn trong AWS auth map trong bảng điều khiển.

```
kubectl describe configmap -n kube-system aws-auth
```

Bây giờ tất cả đã được setup xong. Để biết thêm thông tin, hãy xem qua [tài liệu EKS](https://docs.aws.amazon.com/eks/latest/userguide/add-user-role.html) về chủ đề này
