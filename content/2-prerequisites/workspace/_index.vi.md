---
title : "Tạo Workspace"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---
{{% notice warning %}}
Môi trường Cloud9 phải được xây dựng bởi một người dùng IAM có quyền quản trị viên, không phải là người dùng tài khoản root. Vui lòng đăng nhập với tài khoản IAM, không phải tài khoản root.
{{% /notice %}}

{{% notice warning %}}
Nếu bạn tham gia sự kiện được host bởi AWS, môi trường Cloud9 đã được xây dựng sẵn cho bạn. Chỉ cần mở IDE tồn tại trong bảng điều khiển Cloud9.
{{% /notice %}}

{{% notice info %}}
Danh sách trình duyệt được hỗ trợ cho AWS Cloud9 có thể tìm thấy [ở đây](https://docs.aws.amazon.com/cloud9/latest/user-guide/browsers.html).
{{% /notice %}}

{{% notice tip %}}
Bộ lọc quảng cáo, vô hiệu hóa javascript và bộ lọc theo dõi phải bị vô hiệu hóa cho tên miền cloud9 hoặc kết nối tới môi trường có thể bị ảnh hưởng. Cloud9 yêu cầu cookies từ bên thứ ba. You can whitelist the [specific domains](https://docs.aws.amazon.com/cloud9/latest/user-guide/troubleshooting.html#troubleshooting-env-loading).
{{% /notice %}}

## [Chạy cloud9 trên region gần bạn]()

**Singapore**

Tạo môi trường Cloud9: `https://ap-southeast-1.console.aws.amazon.com/cloud9/home?region=ap-southeast-1`

+ Chọn **Create environment**
+ Đặt tên **eksworkshop**, click Next.
+ Chọn **t3.small** cho loại instance , Để tất cả mặc định và click **Create environment**

Khi Cloud9 được mở, bạn có thể tùy chỉnh môi trường bằng cách:

+ Tắt **Welcome tab**

![cloud9](/images/prerequisites/cloud9-1.png?featherlight=false&width=90pc?width=90pc)

+ Mở tab **terminal** mới trong khu vực làm việc chính
+ 
![cloud9](/images/prerequisites/cloud9-2.png?featherlight=false&width=90pc?width=90pc)

+ Tắt terminal ở phía dưới

![cloud9](/images/prerequisites/cloud9-3.png?featherlight=false&width=90pc?width=90pc)

+ Bây giờ workspace của bạn trông giống thế này

![cloud9](/images/prerequisites/cloud9-4.png?featherlight=false&width=90pc?width=90pc)


{{% notice info %}}
Nếu bạn muốn chạy tất cả các phần trong workshop này, có thể hữu ích khi có thêm dung lượng lưu trữ để lưu trữ tất cả các kho lưu trữ và kiểm tra.
{{% /notice %}}

## nâng cấp dung lượng ổ đĩa trên Cloud9

{{% notice note %}}
Lệnh sau sẽ thêm thêm dung lượng đĩa cho phân vùng gốc của thực thể EC2 mà Cloud9 chạy trên. Sau khi lệnh hoàn tất, chúng ta khởi động lại thực thể và có thể mất một hoặc hai phút cho môi trường IDE để trở lại trực tuyến.
{{% /notice %}}

```
pip3 install --user --upgrade boto3
export instance_id=$(curl -s http://169.254.169.254/latest/meta-data/instance-id)
python -c "import boto3
import os
from botocore.exceptions import ClientError 
ec2 = boto3.client('ec2')
volume_info = ec2.describe_volumes(
    Filters=[
        {
            'Name': 'attachment.instance-id',
            'Values': [
                os.getenv('instance_id')
            ]
        }
    ]
)
volume_id = volume_info['Volumes'][0]['VolumeId']
try:
    resize = ec2.modify_volume(    
            VolumeId=volume_id,    
            Size=30
    )
    print(resize)
except ClientError as e:
    if e.response['Error']['Code'] == 'InvalidParameterValue':
        print('ERROR MESSAGE: {}'.format(e))"
if [ $? -eq 0 ]; then
    sudo reboot
fi
```