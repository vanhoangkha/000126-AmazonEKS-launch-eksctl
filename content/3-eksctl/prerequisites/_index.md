---
title : "Prerequisites"
date: 2024-01-01
weight : 1
chapter : false
pre : " <b> 3.1 <b> "
---

For this module, we need to download the [eksctl](https://eksctl.io/) binary:

```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

sudo mv -v /tmp/eksctl /usr/local/bin
```

![createkmskey](/images/prerequisites/eksctlbinary.png?width=90pc)


Confirm the eksctl command works:

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


