+++
title = "Cập nhật cấu hình IAM"
date = 2021
weight = 4
chapter = false
pre = "<b>1.4.3 </b>"
+++

#### Cập nhật cấu hình IAM cho Workspace

{{%notice info%}}
Cloud9 sẽ quản lý thông tin chứng thực IAM một cách tự động. Cấu hình mặc định này hiện tại không tương thích với chứng thực EKS thông qua IAM, chúng ta sẽ cần phải vô hiệu hóa tính năng này và sử dụng IAM Role.
{{%/notice%}}

1. Click vào biểu tượng Preferences.
    + Kéo thành scroll bar xuống dưới.
    + Click **AWS Settings**.
![Configure Role](/images/1-eks/role10.png?width=90pc)

2. Chuyển chế độ **AWS managed temporaly credentials** sang disabled (màu đỏ)
    + Click **X** để đóng tab **Preferences**.
![Configure Role](/images/1-eks/role11.png?width=90pc)

3. Để đảm bảo các thông tin chứng thực tạm không được lưu lại trong Cloud9, chúng ta sẽ xóa tất cả những thông tin chứng thực đang tồn tại bằng câu lệnh dưới đây.
```
rm -vf ${HOME}/.aws/credentials
```
![Configure Role](/images/1-eks/role12.png?width=90pc)

4. Tiếp theo chúng ta sẽ cấu hình aws cli sử dụng Region hiện tại.
```
export ACCOUNT_ID=$(aws sts get-caller-identity --output text --query Account)
export AWS_REGION=$(curl -s 169.254.169.254/latest/dynamic/instance-identity/document | jq -r '.region')
export AZS=($(aws ec2 describe-availability-zones --query 'AvailabilityZones[].ZoneName' --output text --region $AWS_REGION))
```
5. Kiểm tra xem AWS_REGION đã được thiết lập đúng Region hiện tại chưa.

```
test -n "$AWS_REGION" && echo AWS_REGION is "$AWS_REGION" || echo AWS_REGION is not set
```
6. Tiếp theo chúng ta sẽ lưu các thông tin cấu hình vào bash_profile
```
echo "export ACCOUNT_ID=${ACCOUNT_ID}" | tee -a ~/.bash_profile
echo "export AWS_REGION=${AWS_REGION}" | tee -a ~/.bash_profile
echo "export AZS=(${AZS[@]})" | tee -a ~/.bash_profile
aws configure set default.region ${AWS_REGION}
aws configure get default.region
```
7. Kiểm tra IAM Role
    + Chúng ta sẽ sử dụng câu lệnh để kiểm tra Cloud9 IDE đang sử dụng IAM Role có chính xác không.
```
aws sts get-caller-identity --query Arn | grep eksworkshop-admin -q && echo "IAM role valid" || echo "IAM role NOT valid"
```
![Configure Role](/images/1-eks/role13.png?width=90pc)
{{%notice info%}}
Nếu kết quả là **IAM role NOT valid**, hãy kiểm tra lại các bước trước xem thông tin IAM role bạn tạo và gán vào Cloud9 Workspace có chính xác không nhé.
{{%/notice%}}

