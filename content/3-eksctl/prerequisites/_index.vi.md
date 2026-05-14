---
title : "Chuẩn bị"
date: 2024-01-01
weight : 1
chapter : false
pre : " <b> 3.1 <b> "
---

Để sử dụng eksctl trong phần này, bạn cần phải tải xuống tiện ích [eksctl](https://eksctl.io/):

```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

sudo mv -v /tmp/eksctl /usr/local/bin
```

![createkmskey](/images/prerequisites/eksctlbinary.png?width=90pc)

Xác nhận lệnh eksctl hoạt động:

```
eksctl version
```
![createkmskey](/images/prerequisites/version.png?width=90pc)

Enable eksctl bash-completion

```
eksctl completion bash >> ~/.bash_completion
. /etc/profile.d/bash_completion.sh
. ~/.bash_completion

```
![createkmskey](/images/prerequisites/enable-eksctl.png?width=90pc)
