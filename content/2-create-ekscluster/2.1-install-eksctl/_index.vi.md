+++
title = "Cài đặt eksctl"
date = 2021
weight = 1
chapter = false
pre = "<b>2.1 </b>"
+++

#### Cài đặt eksctl

Trong phần này chúng ta sẽ thực hiện cài đặt công cụ **eksctl** vào Cloud9 Workspace.

1. Chạy câu lệnh để tải về công cụ **eksctl**.

```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

sudo mv -v /tmp/eksctl /usr/local/bin
```

2. Kiểm tra **eksctl** hoạt động hay không bằng câu lệnh dưới đây.
```
eksctl version
``` 

3. Kích hoạt tính năng bash-completion của eksctl
```
eksctl completion bash >> ~/.bash_completion
. /etc/profile.d/bash_completion.sh
. ~/.bash_completion
```
![EKSCTL](/images/2-ekscluster/eksctl.png?width=90pc)
