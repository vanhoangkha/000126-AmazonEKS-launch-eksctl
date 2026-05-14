---
title : "Tạo AWS KMS Custom Managed Key (CMK)"
date: 2024-01-01
weight : 9
chapter : false
pre : " <b> 2.9 <b> "
---

Tạo một CMK cho EKS cluster sử dụng khi mã hoá bảo mật cho kubernetes của bạn:

```
aws kms create-alias --alias-name alias/eksworkshop --target-key-id $(aws kms create-key --query KeyMetadata.Arn --output text)
```

![createkmskey](/images/prerequisites/createkmskey.png?width=90pc)

Hãy lấy ARN của CMK để nhập vào lệnh tạo cluster

```
export MASTER_ARN=$(aws kms describe-key --key-id alias/eksworkshop --query KeyMetadata.Arn --output text)
```

![createkmskey](/images/prerequisites/CMK.png?width=90pc)

Chúng ta đặt biến môi trường MASTER_ARN để dễ dàng tham chiếu đến khóa KMS sau này.

Bây giờ, hãy lưu biến môi trường MASTER_ARN vào bash_profile

```
echo "export MASTER_ARN=${MASTER_ARN}" | tee -a ~/.bash_profile
```
![createkmskey](/images/prerequisites/savekms.png?width=90pc)