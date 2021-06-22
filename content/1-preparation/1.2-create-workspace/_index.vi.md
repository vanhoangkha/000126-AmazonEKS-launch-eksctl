+++
title = "Tạo một Workspace"
date = 2021
weight = 2
chapter = false
pre = "<b>1.2 </b>"
+++

#### Tạo một Workspace sử dụng AWS Cloud9

Ở bước này, chúng ta sẽ tiến hành tạo một Workspace để quản trị Amazon EKS sử dụng dịch vụ AWS Cloud9.

1. Truy cập vào giao diện quản lý của dịch vụ Cloud9.
    + Click **Create Environment**.

![Tạo Workspace](/images/1-eks/cloud9.png?width=90pc)

2. Tại trang **Name environment** điền tên Name là **eksworkshop**
    + Click **Next step**.

![Tạo Workspace](/images/1-eks/cloud92.png?width=90pc)

3. Tại trang **Configure settings**.
    + Click chọn **t3.small**.
    + Kéo thanh scroll bar xuống dưới.
    + Click **Next step**.

![Tạo Workspace](/images/1-eks/cloud93.png?width=90pc)

4. Tại trang **Review**.
    + Kiểm tra lại cấu hình.
    + Click **Create environment**.

5. Sau khi Cloud9 Workspace được tạo hoàn tất.
    + Click **X** để đóng các tab mặc định.

![Tạo Workspace](/images/1-eks/cloud94.png?width=90pc)

6. Click **+** , sau đó click **New Terminal** để mở giao diện terminal mới.

![Tạo Workspace](/images/1-eks/cloud95.png?width=90pc)

7. Chạy đoạn script sau đây để tăng dung lượng Cloud9 Workspace lên 30 GB.
    + Copy đoạn lệnh sau và paste vào giao diện terminal trên workspace của bạn.
    + Sau khi thực thi các lệnh xong, Cloud 9 Workspace sẽ restart lại.
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

![Tạo Workspace](/images/1-eks/cloud96.png?width=90pc)

8. Chúng ta đã hoàn tất việc tạo workspace cho Amazon EKS workshop. Tiếp theo chúng ta sẽ tiến hành **eksctl**.
