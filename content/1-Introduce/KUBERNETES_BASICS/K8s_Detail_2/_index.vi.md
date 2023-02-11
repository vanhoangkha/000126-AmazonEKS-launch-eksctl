---
title : "Chi tiết K8s Objects (2/2)"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 1.3.5  </b> "
---


## [ReplicaSet](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/)

_ReplicaSet là một điều khiển Controller - nó đảm bảo ổn định các nhân bản (số lượng và tình trạng của POD, replica) khi đang chạy._

## [Job](https://kubernetes.io/docs/concepts/workloads/controllers/job/)

_Khi triển khai, vận hành hệ thống, chúng ta sẽ có nhiều tác vụ (Job) cần thực hiện định kỳ hoặc 1 lần. Các Job chạy trong K8s sẽ thực hiện bên trong các Pod. Các Pod sẽ tạo ra khi có Job chạy và kết thúc khi Job thành công. Khi ta xóa Job thì các Pod liên quan cũng được xóa theo_.

## [Service](https://kubernetes.io/docs/concepts/services-networking/service/)

_Kubernetes service là một tài nguyên xác định ra một pod hoặc một nhóm các pod cung cấp cùng một dịch vụ và chính sách truy cập đến các pod đó. Đối với service, Kubernetes cũng cung cấp cho chúng ta nhiều kiểu service khác nhau để phù hợp với nhiều yêu cầu khác nhau_.

## [Label](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/)

_Label là các cặp giá trị key:value được gán vào một đối tượng trong Kubernetes như Pod, được sử dụng để chúng ta có thể định danh một đối tượng Kubernetes một cách nhanh chóng_.