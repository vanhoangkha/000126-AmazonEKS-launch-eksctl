+++
title = "Tạo AWS KMS CMK"
date = 2021
weight = 6
chapter = false
pre = "<b>1.6 </b>"
+++

#### Tạo AWS KMS CMK
Ở bước này, chúng ta sẽ tiến hành tạo một CMK cho EKS cluster sử dụng khi mã hóa các Kubernetes secrets.

1. Chạy lệnh để tạo key và alias.
```
aws kms create-alias --alias-name alias/eksworkshop --target-key-id $(aws kms create-key --query KeyMetadata.Arn --output text)
```

2. Lấy thông tin ARN của key chúng ta vừa tạo, lưu vào biến môi trường **MASTER_ARN** để dùng sau này.
```
export MASTER_ARN=$(aws kms describe-key --key-id alias/eksworkshop --query KeyMetadata.Arn --output text)
```

3. Lưu thông tin biến môi trường **MASTER_ARN** vào bash_profile
```
echo "export MASTER_ARN=${MASTER_ARN}" | tee -a ~/.bash_profile
```
![KMS](/images/1-eks/kms.png?width=90pc)

4. Kiểm tra KMS đã được tạo trong giao diện của dịch vụ **Key Management Service**.
![KMS](/images/1-eks/kms2.png?width=90pc)