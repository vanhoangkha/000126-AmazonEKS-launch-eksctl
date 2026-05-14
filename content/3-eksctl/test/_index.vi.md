---
title : "Kiểm thử Cluster"
date: 2024-01-01
weight : 3
chapter : false
pre : " <b> 3.3 <b> "
---


## Kiểm thử Cluster:

Xác nhận các nodes:

```
kubectl get nodes # nếu bạn thấy 3 nodes, thì bạn đang làm đúng
```

![nodes](/images/prerequisites/nodes.png?width=90pc)

## Cập nhật file  kubeconfig để tương tác với cluster:

```
aws eks update-kubeconfig --name eksworkshop-eksctl --region ${AWS_REGION}
```
![nodes](/images/prerequisites/updatekubeconfig.png?width=90pc)

## Sử dụng biến môi trường để lưu tên vai trò của nhân viên (Worker Role) để sử dụng trong toàn bộ workshop:

```
STACK_NAME=$(eksctl get nodegroup --cluster eksworkshop-eksctl -o json | jq -r '.[].StackName')
ROLE_NAME=$(aws cloudformation describe-stack-resources --stack-name $STACK_NAME | jq -r '.StackResources[] | select(.ResourceType=="AWS::IAM::Role") | .PhysicalResourceId')
echo "export ROLE_NAME=${ROLE_NAME}" | tee -a ~/.bash_profile
```
![nodes](/images/prerequisites/exportRole.png?width=90pc)

## Chúc mừng!

Bạn đã có một Amazon EKS Cluster hoàn chỉnh và sẵn sàng để sử dụng! Trước khi bạn tiến hành bất kỳ thử nghiệm nào khác, hãy chắc chắn hoàn thành các bước trên trang tiếp theo để cập nhật thông tin xác thực trong Console EKS.


