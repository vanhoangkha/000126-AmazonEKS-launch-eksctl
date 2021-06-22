+++
title = "Cài đặt Kubernetes tools"
date = 2021
weight = 3
chapter = false
pre = "<b>1.3 </b>"
+++

#### Cài đặt công cụ quản trị Kubernetes 

Các cluster của Amazon EKS sẽ cần công cụ kubectl và kubelet và aws-cli hoặc aws-iam-authenticator để cho phép chứng thực IAM cho Kubernetes cluster của bạn.


1. Copy và Paste đoạn lệnh dưới đây vào Terminal của Cloud9 Workspace để cài đặt **kubectl**.

```
sudo curl --silent --location -o /usr/local/bin/kubectl \
   https://amazon-eks.s3.us-west-2.amazonaws.com/1.17.11/2020-09-18/bin/linux/amd64/kubectl

sudo chmod +x /usr/local/bin/kubectl
```

![Cài k8s tool](/images/1-eks/k8stool1.png?width=90pc)

2. Copy và Paste đoạn lệnh dưới đây vào Terminal của Cloud9 Workspace để cập nhật awscli.
```
sudo pip install --upgrade awscli && hash -r
```
![Cài k8s tool](/images/1-eks/k8stool2.png?width=90pc)

3. Copy và Paste đoạn lệnh dưới đây vào Terminal của Cloud9 Workspace để cài đặt các công cụ hỗ trợ xử lý text trên dòng lệnh.
```
sudo yum -y install jq gettext bash-completion moreutils

```
![Cài k8s tool](/images/1-eks/k8stool3.png?width=90pc)
{{%notice tip%}}
**jq** giống như sed cho dữ liệu JSON - bạn có thể sử dụng nó để cắt và lọc cũng như ánh xạ và chuyển đổi dữ liệu có cấu trúc với cùng một cách dễ dàng giống như  sed, awk, grep.
{{%/notice%}}

```
echo 'yq() {
  docker run --rm -i -v "${PWD}":/workdir mikefarah/yq "$@"
}' | tee -a ~/.bashrc && source ~/.bashrc
```
![Cài k8s tool](/images/1-eks/k8stool4.png?width=90pc)

3. Kiểm tra các công cụ đã được cài đặt bằng cách chạy lệnh dưới đây.
```
kubectl completion bash >>  ~/.bash_completion
. /etc/profile.d/bash_completion.sh
. ~/.bash_completion

```
![Cài k8s tool](/images/1-eks/k8stool5.png?width=90pc)

4. Bật tính năng tự động hoàn tất cho công cụ kubectl bằng cách chạy lệnh dưới đây:
```
kubectl completion bash >>  ~/.bash_completion
. /etc/profile.d/bash_completion.sh
. ~/.bash_completion
```
![Cài k8s tool](/images/1-eks/k8stool6.png?width=90pc)
5. Thiết lập phiên bản 2.2.0 khi sử dụng AWS Load Balancer Controller
```
echo 'export LBC_VERSION="v2.2.0"' >>  ~/.bash_profile
.  ~/.bash_profile

```

{{%notice tip%}}
Trước đây chúng ta sử dụng Kubernetes in-tree Load Balancer cho đối tượng instance, và AWS Load Balancer Controller cho đối tượng IP.
Khi sử dụng AWS Load Balancer Controller phiên bản 2.2.0 bạn có thể tạo Network Load Balancer cho cả đối tượng instance và đối tượng IP..\
Đọc thêm tại:.\
 https://docs.aws.amazon.com/eks/latest/userguide/aws-load-balancer-controller.html
{{%/notice%}}
