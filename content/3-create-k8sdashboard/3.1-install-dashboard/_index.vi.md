+++
title = "Triển khai K8s dashboard"
date = 2021
weight = 1
chapter = false
pre = "<b>3.1 </b>"
+++

#### Triển khai K8s dashboard

Trong phần này chúng ta sẽ thực triển khai Kubernetes dashboard. Kubernetes dashboard không được triển khai mặc định.

Bạn có xem thêm thông tin về Kubernetes dashboard tại đây: https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/

1. Chạy câu lệnh dưới đây để triển khai Kubernetes dashboard
```
export DASHBOARD_VERSION="v2.0.0"

kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/${DASHBOARD_VERSION}/aio/deploy/recommended.yaml
```
{{%notice tip%}}
Kubernetes dashboard được triển khai trong một private cluster, chúng ta sẽ cần  truy cập tới nó thông qua 1 proxy. **kube-proxy** đã sẵn sàng để chúng ta yêu cầu truy xuất tới dịch vụ của dashboard.
{{%/notice%}}

2. Chạy câu lệnh dưới đây để khởi chạy **kube-proxy**.
```
kubectl proxy --port=8080 --address=0.0.0.0 --disable-filter=true &
```
{{%notice tip%}}
Câu lệnh trên khởi chạy proxy và lắng nghe trên tất cả các interfaces. Đồng thời cũng vô hiệu hóa việc lọc các yêu cầu truy cập từ ngoài mạng local. .\
Lệnh trên sẽ chạy ngầm dưới background và sẽ chạy cho tới khi phiên kết nối terminal hiện tại bị tắt.
{{%/notice%}}
{{%notice warning%}}
Việc chúng ta vô hiệu hóa lọc các yêu cầu truy cập từ ngoài mạng local chỉ để áp dụng cho môi trường lab. Không nên sử dụng trong môi trường Production.\
{{%/notice%}}

![Console](/images/3-dashboard/dashboard.png?width=90pc)

