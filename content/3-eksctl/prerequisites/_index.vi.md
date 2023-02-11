---
title : "Chuẩn bị"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 3.1 <b> "
---

Để sử dụng eksctl trong phần này, bạn cần phải tải xuống tiện ích [eksctl](https://eksctl.io/):

```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

sudo mv -v /tmp/eksctl /usr/local/bin
```

Xác nhận lệnh eksctl hoạt động:

```
eksctl version
```

Enable eksctl bash-completion

```
eksctl completion bash >> ~/.bash_completion
. /etc/profile.d/bash_completion.sh
. ~/.bash_completion

```

