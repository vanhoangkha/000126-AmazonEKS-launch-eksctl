---
title : "Triển khai Kubernetes"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 4.1.1 <b> "
---
Bảng điều khiển Kubernetes chính thức không được cài đặt theo mặc định, nhưng có hướng dẫn [trong tài liệu chính thức](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/).

Chúng ta có thể cài đặt bảng điều khiển bằng lệnh sau:

```
export DASHBOARD_VERSION="v2.6.0"

kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/${DASHBOARD_VERSION}/aio/deploy/recommended.yaml
```

Vì đây là được cài đặt trên cluster riêng của chúng ta, chúng ta cần truy cập nó qua một proxy. `kube-proxy` có sẵn để proxy yêu cầu của chúng ta đến dịch vụ bảng điều khiển. Trong Workspace của bạn, chạy lệnh sau:

```
kubectl proxy --port=8080 --address=0.0.0.0 --disable-filter=true &
```

Điều này sẽ bắt đầu proxy, lắng nghe trên cổng 8080, lắng nghe trên tất cả các giao diện và sẽ vô hiệu hóa việc lọc yêu cầu không phải localhost.

Lệnh này sẽ tiếp tục chạy trong phiên làm việc của terminal hiện tại.