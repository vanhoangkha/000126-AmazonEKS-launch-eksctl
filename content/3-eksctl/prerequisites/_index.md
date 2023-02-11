---
title : "Prerequisites"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 3.1 <b> "
---

For this module, we need to download the [eksctl](https://eksctl.io/) binary:

```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

sudo mv -v /tmp/eksctl /usr/local/bin
```

Confirm the eksctl command works:

```
eksctl version
```

Enable eksctl bash-completion

```
eksctl completion bash >> ~/.bash_completion
. /etc/profile.d/bash_completion.sh
. ~/.bash_completion

```

