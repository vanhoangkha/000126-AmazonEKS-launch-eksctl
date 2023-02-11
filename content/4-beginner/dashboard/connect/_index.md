---
title : "Access the Dashboard"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 4.1.2 <b> "
---

Now we can access the Kubernetes Dashboard

In your Cloud9 environment, click **Tools / Preview / Preview Running Application**
Scroll to **the end of the URL** and append:

```
/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
```

The Cloud9 Preview browser doesn’t appear to support the token authentication, so once you have the login screen in the cloud9 preview browser tab, press the **Pop Out** button to open the login screen in a regular browser tab, like below:

![pic1](/images/beginner/1.png?featherlight=false&width=90pc?width=90pc)

Open a New Terminal Tab and enter

```
aws eks get-token --cluster-name eksworkshop-eksctl | jq -r '.status.token'
```
Copy the output of this command and then click the radio button next to Token then in the text field below paste the output from the last command.

![pic1](/images/beginner/2.png?featherlight=false&width=90pc?width=90pc)

Then press Sign In

![pic1](/images/beginner/3.png?featherlight=false&width=90pc?width=90pc)