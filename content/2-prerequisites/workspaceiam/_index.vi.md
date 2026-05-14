---
title : "Cập nhật cài đặt IAM cho workspace của bạn"
ddate: 2024-01-01
weight : 7
chapter : false
pre : " <b> 2.7 <b> "
---

{{% notice info %}}
Cloud9 thông thường quản lý chứng chỉ IAM một cách tự động. Điều này hiện tại không tương thích với xác thực IAM của EKS, nên chúng ta sẽ tắt nó và phụ thuộc vào vai trò IAM.
{{% /notice %}}

Để đảm bảo rằng chứng chỉ tạm thời không được sẵn có, chúng ta sẽ xóa bất kỳ tệp chứng chỉ hiện tại và tắt **chứng chỉ tạm thời được quản lý bởi AWS**:

```
aws cloud9 update-environment  --environment-id $C9_PID --managed-credentials-action DISABLE
rm -vf ${HOME}/.aws/credentials

```

![workspaceiam](/images/prerequisites/rmvcredentials.png?width=90pc)

Chúng ta nên cấu hình cli aws của chúng ta với region mặc định hiện tại của chúng ta.


{{% notice info %}}
Nếu bạn đang trong một sự kiện của AWS, hãy hỏi người hướng dẫn về **AWS region** để sử dụng.
{{% /notice %}}

```
export ACCOUNT_ID=$(aws sts get-caller-identity --output text --query Account)
export AWS_REGION=$(curl -s 169.254.169.254/latest/dynamic/instance-identity/document | jq -r '.region')
export AZS=($(aws ec2 describe-availability-zones --query 'AvailabilityZones[].ZoneName' --output text --region $AWS_REGION))
```

![workspaceiam](/images/prerequisites/export.png?width=90pc)


Kiểm tra AWS_REGION có được set trong region mong muốn

```
test -n "$AWS_REGION" && echo AWS_REGION is "$AWS_REGION" || echo AWS_REGION is not set
```

![workspaceiam](/images/prerequisites/checkregion.png?width=90pc)

Lưu tất cả vào bash_profile

```
echo "export ACCOUNT_ID=${ACCOUNT_ID}" | tee -a ~/.bash_profile
echo "export AWS_REGION=${AWS_REGION}" | tee -a ~/.bash_profile
echo "export AZS=(${AZS[@]})" | tee -a ~/.bash_profile
aws configure set default.region ${AWS_REGION}
aws configure get default.region
```

![workspaceiam](/images/prerequisites/save.png?width=90pc)

## Xác nhận vai trò IAM

Sử dụng [GetCallerIdentity](https://docs.aws.amazon.com/cli/latest/reference/sts/get-caller-identity.html) công cụ dòng lệnh CLI để xác nhận rằng IDE Cloud9 đang sử dụng đúng IAM role.

```
aws sts get-caller-identity --query Arn | grep eksworkshop-admin -q && echo "IAM role valid" || echo "IAM role NOT valid"
```
![workspaceiam](/images/prerequisites/validate.png?width=90pc)

Nếu IAM role không hợp lệ, **ĐỪNG TIẾP TỤC**. Quay lại và xác nhận các bước trên trang này.

