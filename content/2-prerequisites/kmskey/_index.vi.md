---
title : "Tạo AWS KMS Custom Managed Key (CMK)"
date :  "`r Sys.Date()`" 
weight : 8
chapter : false
pre : " <b> 2.8 <b> "
---

Tạo một CMK cho EKS cluster sử dụng khi mã hoá bảo mật cho kubernetes của bạn:

```
aws kms create-alias --alias-name alias/eksworkshop --target-key-id $(aws kms create-key --query KeyMetadata.Arn --output text)
```

Hãy lấy ARN của CMK để nhập vào lệnh tạo cluster

```
export MASTER_ARN=$(aws kms describe-key --key-id alias/eksworkshop --query KeyMetadata.Arn --output text)
```

Chúng ta đặt biến môi trường MASTER_ARN để dễ dàng tham chiếu đến khóa KMS sau này.

Bây giờ, hãy lưu biến môi trường MASTER_ARN vào bash_profile

```
echo "export MASTER_ARN=${MASTER_ARN}" | tee -a ~/.bash_profile
```
