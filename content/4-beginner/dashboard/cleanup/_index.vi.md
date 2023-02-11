---
title : "Dọn dẹp"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 4.1.3 <b> "
---

Dừng proxy và xoá bảng điều khiển bằng câu lệnh dưới

```
# kill proxy
pkill -f 'kubectl proxy --port=8080'

# delete dashboard
kubectl delete -f https://raw.githubusercontent.com/kubernetes/dashboard/${DASHBOARD_VERSION}/aio/deploy/recommended.yaml

unset DASHBOARD_VERSION
```