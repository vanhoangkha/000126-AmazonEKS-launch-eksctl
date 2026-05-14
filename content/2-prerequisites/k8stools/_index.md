---
title : "Install Kubernetes Tools"
date: 2024-01-01
weight : 4
chapter : false
pre : " <b> 2.4 </b> "
---

Amazon EKS clusters require kubectl and kubelet binaries and the aws-cli or aws-iam-authenticator binary to allow IAM authentication for your Kubernetes cluster.

{{% notice tip %}}
In this workshop we will give you the commands to download the Linux binaries. If you are running Mac OSX / Windows, [please see the official EKS docs for the download links](https://docs.aws.amazon.com/eks/latest/userguide/getting-started.html).
{{% /notice %}}

## Install kubectl

Kubectl is a command-line tool for managing Kubernetes, allowing you to perform tasks such as deploy, scale, configure, and control various objects within a Kubernetes cluster. The main objects include Pods, Services, Deployments, and ReplicaSets. Kubectl also allows you to view logs, check status, and manage resources. With kubectl, you can control and monitor your applications in a Kubernetes environment with ease.

``` 
sudo curl --silent --location -o /usr/local/bin/kubectl \
   https://s3.us-west-2.amazonaws.com/amazon-eks/1.21.5/2022-01-21/bin/linux/amd64/kubectl

sudo chmod +x /usr/local/bin/kubectl

```

![install-kubectl](/images/Startworkshop/install-kubectl.png?width=90pc)

## Update awscli

Upgrade AWS CLI according to guidance in [AWS documentation](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).

```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

![install-kubectl](/images/Startworkshop/awscli-update.png?width=90pc)

## Install jq, envsubst (from GNU gettext utilities) and bash-completion

```
sudo yum -y install jq gettext bash-completion moreutils
```

![install-kubectl](/images/Startworkshop/jq-envsubst.png?width=90pc)

## Install yq for yaml processing

```
echo 'yq() {
  docker run --rm -i -v "${PWD}":/workdir mikefarah/yq "$@"
}' | tee -a ~/.bashrc && source ~/.bashrc
```

![install-kubectl](/images/Startworkshop/yq-for-yaml.png?width=90pc)

## Verify the binaries are in the path and executable

```
for command in kubectl jq envsubst aws
  do
    which $command &>/dev/null && echo "$command in path" || echo "$command NOT FOUND"
  done
```

![install-kubectl](/images/Startworkshop/verify.png?width=90pc)

## Enable kubectl bash_completion

```
kubectl completion bash >>  ~/.bash_completion
. /etc/profile.d/bash_completion.sh
. ~/.bash_completion
```

![install-kubectl](/images/Startworkshop/enablekubectl.png?width=90pc)

## set the AWS Load Balancer Controller version

```
echo 'export LBC_VERSION="v2.4.1"' >>  ~/.bash_profile
echo 'export LBC_CHART_VERSION="1.4.1"' >>  ~/.bash_profile
.  ~/.bash_profile
```

![install-kubectl](/images/Startworkshop/loadblc.png?width=90pc)