---
title : "Chi tiết K8s Objects (1/2)"
date: 2024-01-01
weight : 4
chapter : false
pre : " <b> 1.3.4  </b> "
---

## [Pod](https://kubernetes.io/docs/concepts/workloads/pods/)

_Khi một ứng dụng được đóng gói thì ứng dụng đó sẽ có thể chạy trên một container độc lập, tuy chúng ta có thể chạy container độc lập như cách khởi chạy một ứng dụng monolythic, nhưng Kubernetes sẽ không chạy theo cách như vậy, Kubernetes sử dụng khái niệm pod để nhóm các container lại với nhau. Một pod là một nhóm các container, các container này sẽ dùng chung tài nguyên và network, các container trong một pod có thể duy trì giao tiếp với nhau như trên một máy chủ nhưng vẫn giữ được sự độc lập cần thiết._

## [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)

_DaemonSet là một dạng dịch vụ quản lý các Pod hoạt động với chức năng khá là riêng biệt bằng cách đảm bảo Pod dịch vụ sẽ được chạy trên toàn bộ các Node trong một Kubernetes Cluster (hoặc trên một số **Node**  cụ thể trong **Kubernetes**_.

## [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)

_Trong Kubernetes, đối tượng Deployment là đối tượng chính đảm nhận việc deploy và quản lý ứng dụng của chúng ta. Nó cho phép chúng ta deploy các Pod, update Pod, rollback Pod và các ReplicaSet_.