---
title : "Tổng quan về Kubernetes"
date: 2024-01-01
weight : 3
chapter : false
pre : " <b> 1.3.3  </b> "
---

_Đối tượng Kubernetes là các thực thể được sử dụng để biểu thị trạng thái của cluster._

_Một đối tượng là một "hồ sơ ý định" - sau khi được tạo, cluster sẽ cố gắng đảm bảo nó tồn tại như đã định. Điều này được gọi là "trạng thái mong muốn" của cluster._

_Kubernetes luôn làm việc để khiến trạng thái "hiện tại" của một đối tượng bằng với trạng thái "mong muốn" của đối tượng. Trạng thái mong muốn có thể mô tả:_

- Pod (container) nào đang chạy và trên nodes nào
- Điểm cuối IP tương ứng với nhóm logic của container
- Số bản sao của một container đang chạy
- Và nhiều thứ hơn nữa...

_Bây giờ chúng ta sẽ giải thích các đối tượng k8s chi tiết hơn..._