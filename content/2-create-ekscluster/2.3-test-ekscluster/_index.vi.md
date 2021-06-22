+++
title = "Kiểm tra EKS cluster"
date = 2021
weight = 3
chapter = false
pre = "<b>2.3 </b>"
+++

#### Kiểm tra EKS cluster

1. Chạy câu lệnh để kiểm tra các nodes được tạo. Chúng ta sẽ thấy 3 nodes.
```
kubectl get nodes

```

2. Lưu lại thông tin EKS node role để sử dụng cho các bài lab tiếp theo.
```
STACK_NAME=$(eksctl get nodegroup --cluster eksworkshop-eksctl -o json | jq -r '.[].StackName')
ROLE_NAME=$(aws cloudformation describe-stack-resources --stack-name $STACK_NAME | jq -r '.StackResources[] | select(.ResourceType=="AWS::IAM::Role") | .PhysicalResourceId')
echo "export ROLE_NAME=${ROLE_NAME}" | tee -a ~/.bash_profile
``` 
{{%notice tip%}}
Trình chạy kubelet trong Amazon EKS node sẽ gọi tới các AWS APIs và các EKS node sẽ nhận được quyền để thực hiện các API call đó thông qua EKS node role.
{{%/notice%}}

![EKSCTL](/images/2-ekscluster/ekscluster5.png?width=90pc)