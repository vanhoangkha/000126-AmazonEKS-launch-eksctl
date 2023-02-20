---
title : "Cài đặt Kubernetes Tools"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 2.4 </b> "
---

Amazon EKS cần các tập tin kubectl và kubelet và tập tin aws-cli hoặc aws-iam-authenticator để cho phép xác thực IAM cho cụm Kubernetes của bạn.

{{% notice tip %}}
Trong workshop này, chúng tôi sẽ cung cấp cho bạn các lệnh để tải xuống các tập tin nhị phân Linux. Nếu bạn đang chạy Mac OSX / Windows, [vui lòng xem tài liệu chính thức EKS để tìm liên kết tải xuống](https://docs.aws.amazon.com/eks/latest/userguide/getting-started.html).
{{% /notice %}}

## Cài đặt kubectl

Kubectl là công cụ dòng lệnh quản lý cho Kubernetes, cho phép bạn thực hiện các tác vụ như deploy, scale, cấu hình và kiểm soát các đối tượng trong cluster Kubernetes. Các đối tượng chính bao gồm Pods, Services, Deployments và ReplicaSets. Kubectl cũng cho phép bạn xem log, kiểm tra trạng thái và quản lý tài nguyên. Sử dụng kubectl, bạn có thể điều khiển và giám sát các ứng dụng của mình trên môi trường Kubernetes một cách dễ dàng.

``` 
sudo curl --silent --location -o /usr/local/bin/kubectl \
   https://s3.us-west-2.amazonaws.com/amazon-eks/1.21.5/2022-01-21/bin/linux/amd64/kubectl

sudo chmod +x /usr/local/bin/kubectl

```
![install-kubectl](/images/Startworkshop/install-kubectl.png?width=90pc)

## Cập nhật awscli

Nâng cấp AWS CLI theo hướng dẫn trong [AWS documentation](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).

```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

![install-kubectl](/images/Startworkshop/awscli-update.png?width=90pc)

## Cài đặt jq, envsubst (from GNU gettext utilities) and bash-completion

```
sudo yum -y install jq gettext bash-completion moreutils
```
![install-kubectl](/images/Startworkshop/jq-envsubst.png?width=90pc)


## Cài đặt yq cho việc xử lý yaml 

```
echo 'yq() {
  docker run --rm -i -v "${PWD}":/workdir mikefarah/yq "$@"
}' | tee -a ~/.bashrc && source ~/.bashrc
```

![install-kubectl](/images/Startworkshop/yq-for-yaml.png?width=90pc)

## Xác minh tập tin nhị phân trên đường dẫn và thực thi

```
for command in kubectl jq envsubst aws
  do
    which $command &>/dev/null && echo "$command in path" || echo "$command NOT FOUND"
  done
```
![install-kubectl](/images/Startworkshop/verify.png?width=90pc)

## Kích hoạt kubectl bash_completion

```
kubectl completion bash >>  ~/.bash_completion
. /etc/profile.d/bash_completion.sh
. ~/.bash_completion
```
![install-kubectl](/images/Startworkshop/enablekubectl.png?width=90pc)

## Điều chỉnh phiên bản AWS Load Balancer Controller 

```
echo 'export LBC_VERSION="v2.4.1"' >>  ~/.bash_profile
echo 'export LBC_CHART_VERSION="1.4.1"' >>  ~/.bash_profile
.  ~/.bash_profile
```

![install-kubectl](/images/Startworkshop/loadblc.png?width=90pc)