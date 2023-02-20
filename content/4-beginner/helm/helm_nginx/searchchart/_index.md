---
title : "Search Chart Repositories"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 6.2.2 <b> "
---


Now that our repository Chart list has been updated, we can [search for Charts](https://helm.sh/docs/helm/helm_search/).

To list all Charts:

```
helm search repo
```

![searchCharts](/images/beginner/updatecharts/2.png?width=90pc)

That should output something similar to:

```
NAME                                    CHART VERSION   APP VERSION                     DESCRIPTION
stable/acs-engine-autoscaler            2.2.2           2.1.1                           Scales worker...
stable/aerospike                        0.3.2           v4.5.0.5                        A Helm chart...
...
```

You can see from the output that it dumped the list of all Charts we have added. In some cases that may be useful, but an even more useful search would involve a keyword argument. So next, we’ll search just for `nginx`:

```
helm search repo nginx
```
![searchCharts](/images/beginner/updatecharts/3.png?width=90pc)


That results in:

```
NAME                            CHART VERSION   APP VERSION     DESCRIPTION
stable/nginx-ingress            1.41.3          v0.34.1         DEPRECATED! An nginx Ingress controller ...
stable/nginx-ldapauth-proxy     0.1.6           1.13.5          DEPRECATED - nginx proxy with ldapauth ...
stable/nginx-lego               0.3.1                           Chart for...
stable/gcloud-endpoints         0.1.2           1               DEPRECATED Develop...
...
```

This new list of Charts are specific to nginx, because we passed the nginx argument to the helm search repo command.

Further information on the command can be found here.