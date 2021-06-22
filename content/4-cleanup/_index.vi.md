+++
title = "Dọn dẹp tài nguyên  "
date = 2021
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

Chúng ta sẽ tiến hành xóa các tài nguyên theo thứ tự sau 

1. Dừng proxy và xóa Kubernetes dashboard.

```
# kill proxy
pkill -f 'kubectl proxy --port=8080'

# delete dashboard
kubectl delete -f https://raw.githubusercontent.com/kubernetes/dashboard/${DASHBOARD_VERSION}/aio/deploy/recommended.yaml

unset DASHBOARD_VERSION
```

2. Xóa các demo repo và các ứng dụng triển khai
```
cd ~/environment/ecsdemo-frontend
kubectl delete -f kubernetes/service.yaml
kubectl delete -f kubernetes/deployment.yaml

cd ~/environment/ecsdemo-crystal
kubectl delete -f kubernetes/service.yaml
kubectl delete -f kubernetes/deployment.yaml

cd ~/environment/ecsdemo-nodejs
kubectl delete -f kubernetes/service.yaml
kubectl delete -f kubernetes/deployment.yaml

export DASHBOARD_VERSION="v2.0.0"

kubectl delete -f https://raw.githubusercontent.com/kubernetes/dashboard/${DASHBOARD_VERSION}/src/deploy/recommended/kubernetes-dashboard.yaml
```

![Configure VPN](/images/vpn/clean3.png?width=90pc)

3. Xóa EKS cluster. Quá trình xóa sẽ mất khoảng 15 phút và bạn có thể xem trên giao diện của dịch vụ Cloud Formation https://console.aws.amazon.com/cloudformation/home
```
eksctl delete cluster --name=eksworkshop-eksctl
```

4. Xóa Cloud9 Workspace
    + Vào giao diện của dịch vụ Cloud9.
    + Click chọn Instance **eksworkshop**.
    + Click **Delete**.
    ![dashboard](/images/3-dashboard/cleanup.png?width=90pc)
    + Gõ **Delete** để xác nhận.
    + Click **Delete** để thực hiện xóa Cloud9 Workspace.
    ![dashboard](/images/3-dashboard/cleanup2.png?width=90pc)