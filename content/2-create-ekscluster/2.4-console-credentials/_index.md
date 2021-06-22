+++
title = "Chứng thực trên Console"
date = 2021
weight = 4
chapter = false
pre = "<b>2.4 </b>"
+++

#### Chứng thực trên Console

{{%notice tip%}}
Mặc dù đa số các bước trong workshop được chạy từ Cloud9 Workspace, nhưng trong quá trình làm lab, sẽ tốt hơn nếu chúng ta có thể vào được EKS console để xem được các đối tượng cấu hình như **Deployments**,**Pods**,**Nodes**. .\
Để đáp ứng yêu cầu này, chúng ta sẽ cấp quyền cho IAM User / Role trong EKS cluster. .\
Mặc định thì IAM User / Role tạo EKS cluster sẽ được cấp quyền này, tuy nhiên nếu bạn tạo cluster khi sử dụng chứng thực IAM tạm thời của Cloud9 thì bạn sẽ phải làm lại các bước dưới đây.
{{%/notice%}}

1. IAM Users và Roles được gán vào 1 EKS Kubernetes cluster thông qua ConfigMap tên là **aws-auth**. Chúng ta có thể sử dụng công cụ **eksctl** để làm việc này với một câu lệnh. Bạn sẽ cần xác định thông tin IAM / Role đúng (ARN) để thêm quyền truy cập console.
    + Để get IAM / Role ARN, chạy câu lệnh sau trong Cloud9 Workspace:
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
![Console](/images/2-ekscluster/console.png?width=90pc)

2. Chạy câu lệnh đưới đây để thực hiện map định danh IAM với EKS cluster username là admin.
```
eksctl create iamidentitymapping --cluster eksworkshop-eksctl --arn ${rolearn} --group system:masters --username admin
``` 
{{%notice tip%}}
Trong thực tế, chúng ta sẽ phân quyền chi tiết hơn chứ không map mọi user vào --username admin trong EKS cluster.
{{%/notice%}}

3. Kiểm tra lại thông tin AWS auth map với câu lệnh dưới.
```
kubectl describe configmap -n kube-system aws-auth
```

![Console](/images/2-ekscluster/console2.png?width=90pc)