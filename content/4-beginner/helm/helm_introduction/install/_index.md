---
title : "Install Helm CLI"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 6.1.1 <b> "
---

Install the Helm CLI
Before we can get started configuring Helm, we’ll need to first install the command line tools that you will interact with. To do this, run the following:

```
curl -sSL https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
```
![helmCLI](/images/beginner/helm.png?width=90pc)

We can verify the version

```
helm version --short
```

![helmCLI](/images/beginner/versioncli.png?width=90pc)

Let’s configure our first Chart repository. Chart repositories are similar to APT or yum repositories that you might be familiar with on Linux, or Taps for Homebrew on macOS.

Add the stable repository so we have something to start with:

```
helm repo add stable https://charts.helm.sh/stable
```

![helmCLI](/images/beginner/addstable.png?width=90pc)

Once this is installed, we will be able to list the charts you can install:

helm search repo stable
Finally, let’s configure Bash completion for the helm command:

```
helm completion bash >> ~/.bash_completion
. /etc/profile.d/bash_completion.sh
. ~/.bash_completion
source <(helm completion bash)
```
