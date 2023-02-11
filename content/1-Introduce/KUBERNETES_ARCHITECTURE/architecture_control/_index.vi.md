---
title : "Control Plane"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 1.2.2 </b> "
---

![Architectural](/images/Introduction/Controlplane/1.png?featherlight=false&width=90pc)

- Một hoặc nhiều Máy Chủ API: Entry point for REST / kubectl

- etcd: : Một kho lưu trữ khóa-giá trị

- Controller-manager: Liên tục đánh giá trạng thái hiện tại so với trạng thái mong muốn.

- Scheduler: Lập lịch cho các pod đến các nút làm việc.

Hãy xem qua [tài liệu chính thức của kubernetes](https://kubernetes.io/docs/concepts/overview/components/#master-components) để biết thêm thông tin.