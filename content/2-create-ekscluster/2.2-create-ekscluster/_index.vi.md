+++
title = "Tạo một EKS cluster"
date = 2021
weight = 2
chapter = false
pre = "<b>2.2 </b>"
+++

#### Tạo một EKS cluster

Trong phần này chúng ta sẽ thực hiện tạo một EKS cluster bằng công cụ **eksctl**. Đảm bảo bạn đã hoàn tất tất cả các bước chuẩn bị trước đó.

1. Chạy câu lệnh để tạo ra một file cài đặt có tên là **eksworkshop.yaml**. Đây là file cấu hình được sử dụng khi chúng ta tạo EKS cluster bằng **eksctl**.

{{%notice tip%}}
eksctl version phải mới hơn 0.24.0 để triển khai EKS cluster phiên bản 1.17
{{%/notice%}}

```
cat << EOF > eksworkshop.yaml
---
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: eksworkshop-eksctl
  region: ${AWS_REGION}
  version: "1.17"

availabilityZones: ["${AZS[0]}", "${AZS[1]}", "${AZS[2]}"]

managedNodeGroups:
- name: nodegroup
  desiredCapacity: 3
  instanceType: t3.small
  ssh:
    enableSsm: true

# To enable all of the control plane logs, uncomment below:
# cloudWatch:
#  clusterLogging:
#    enableTypes: ["*"]

secretsEncryption:
  keyARN: ${MASTER_ARN}
EOF

```
{{%notice tip%}}
Chúng ta sẽ tạo phiên bản EKS cluster thấp hơn version mới nhất để làm bài lab nâng cấp sau này.
{{%/notice%}}

![EKSCTL](/images/2-ekscluster/ekscluster.png?width=90pc)

2. Tiến hành tạo EKS cluster bằng cách chạy câu lệnh dưới đây.
```
eksctl create cluster -f eksworkshop.yaml

``` 
![EKSCTL](/images/2-ekscluster/ekscluster2.png?width=90pc)
{{%notice tip%}}
Việc tạo EKS cluster sẽ mất khoảng 15 phút.
{{%/notice%}}

3. Chúng ta đã hoàn tất việc tạo một EKS cluster.

![EKSCTL](/images/2-ekscluster/ekscluster3.png?width=90pc)

