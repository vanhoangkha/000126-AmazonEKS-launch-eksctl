---
title : "Create a Chart"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 6.3.1</b> "
---

Helm charts have a structure similar to:

```
/eksdemo
├── charts/
├── Chart.yaml
├── templates/
│   ├── deployment.yaml
│   ├── _helpers.tpl
│   ├── hpa.yaml
│   ├── ingress.yaml
│   ├── NOTES.txt
│   ├── serviceaccount.yaml
│   ├── service.yaml
│   └── tests
│       └── test-connection.yaml
└── values.yaml
```

We’ll follow this template, and create a new chart called eksdemo with the following commands:

```
cd ~/environment
helm create eksdemo
cd eksdemo
```
![eksdemo](/images/beginner/microservices/1.png?width=90pc)