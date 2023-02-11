---
title : "Tạo EKS Cluster"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 3.2 <b> "
---

{{% notice warning %}}
Đừng tiếp tục này nếu bạn không [xác nhận IAM role](/2-prerequisites/workspaceiam) in use được sử dụng bởi IDE cloud9. Bạn sẽ không thể chạy các lệnh kubectl cần thiết trong các mô-đun sau nếu cluster EKS không được xây dựng sử dụng vai trò IAM.
{{% /notice %}}

## Create an EKS cluster

{{% notice warning %}}
phiên bản eksctl cần phải là 0.58.0 hoặc cao hơn để triển khai EKS 1.21, [nhấn vô đây](/3-eksctl/prerequisites) để lấy phiên bản cuối cùng.
{{% /notice %}}

Tạo một tệp triển khai eksctl (eksworkshop.yaml) để sử dụng trong việc tạo cluster sử dụng cú pháp sau:

```
cat << EOF > eksworkshop.yaml
---
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: eksworkshop-eksctl
  region: ${AWS_REGION}
  version: "1.21"

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
Sau đó, sử dụng tệp mà bạn đã tạo là đầu vào cho việc tạo cluster eksctl.

{{% notice info %}}
Chúng ta định tạo một phiên bản Kubernetes thấp hơn một phiên bản so với phiên bản mới nhất. Hãy xem qua [phiên bản Kubernetes của Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html) để xác định nhưng phiên bản được hỗ trợ hiện tại. Điều này cho phép bạn thực hiện các bài lab nâng cao.
{{% /notice %}}

```
eksctl create cluster -f eksworkshop.yaml
```
{{% notice info %}}
Khởi chạy EKS và tất cả mọi thứ liên quan sẽ mất khoảng 15 phút
{{% /notice %}}