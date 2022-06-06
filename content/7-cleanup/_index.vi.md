+++
title = "Dọn dẹp tài nguyên"
date = 2020
weight = 7
chapter = false
pre = "<b>7. </b>"
+++
Bạn sẽ dọn dẹp tài nguyên theo thứ tự sau:

#### Xóa Elastic Beanstalk application đã tạo
1. Truy cập [**AWS Elastic Beanstalk console**](https://console.aws.amazon.com/elasticbeanstalk/).
* Click **Applications**.
* Chọn **TravelBuddy**
* Click **Action**
* Click **Delete application**
![Clean up reources](/images/7-cleanup/cleanup-001.png?featherlight=false&width=90pc)
2. Điền ```TravelBuddy``` để xác nhận, sau đó click **Delete** để xóa
![Clean up reources](/images/7-cleanup/cleanup-002.png?featherlight=false&width=90pc)

#### Terminate EC2 Instance
1. Truy cập [**Amazon EC2 console**](https://console.aws.amazon.com/ec2/).
* Trên thanh điều hướng bên trái, click **Intances**.
* Chọn **DevAxWindowsHost**. 
* Click **Instance state**
* Click **Terminate instance**
![Clean up reources](/images/7-cleanup/cleanup-003.png?featherlight=false&width=90pc)
2. Click **Terminate**
![Clean up reources](/images/7-cleanup/cleanup-004.png?featherlight=false&width=90pc)

#### Xóa Users
1. Truy cập vào [**AWS IAM Console**](https://console.aws.amazon.com/iamv2/).
* Click **Users**.
* Chọn **awsstudent**. 
* Click **Delete**
![Clean up reources](/images/7-cleanup/cleanup-009.png?featherlight=false&width=90pc)
2. Điền ```awsstudent``` để xác nhận, sau đó click **Delete**
![Clean up reources](/images/7-cleanup/cleanup-010.png?featherlight=false&width=90pc)

#### Xóa CloudFormation Stack
1. Truy cập [AWS CloudFormation Console](https://console.aws.amazon.com/cloudformation/).
* Chọn **aws-stack-for-Devax**.
* Click **Delete**
![Clean up reources](/images/7-cleanup/cleanup-005.png?featherlight=false&width=90pc)
2. Click **Delete stack**
![Clean up reources](/images/7-cleanup/cleanup-006.png?featherlight=false&width=90pc)

#### Xóa Key Pairs
1. Truy cập [**Amazon EC2 console**](https://console.aws.amazon.com/ec2/).
* Trên thanh điều hướng bên trái, click **Key Pairs**.
* Chọn **KPforDevAxInstances**. 
* Click **Actions**
* Click **Delete**
![Clean up reources](/images/7-cleanup/cleanup-007.png?featherlight=false&width=90pc)
2. Điền ```Delete``` để xác nhận, sau đó click **Delete** để xóa
![Clean up reources](/images/7-cleanup/cleanup-008.png?featherlight=false&width=90pc)

#### Xóa S3 bucket
1. Truy cập vào [**giao diện quản trị dịch vụ S3**](https://s3.console.aws.amazon.com/s3/).
* Click **Buckets**
* Click chọn S3 bucket được tạo ra để lưu file **Module1.template.yaml** khi tạo CloudFormation stack.
* Click **Empty**.
![Clean up reources](/images/7-cleanup/cleanup-011.png?featherlight=false&width=90pc)
2. Điền ```permanently delete``` để xác nhận, sau đó click **Empty** để xóa toàn bộ dữ liệu trong S3 bucket.
![Clean up reources](/images/7-cleanup/cleanup-012.png?featherlight=false&width=90pc)
* Click **Exit** để trở lại giao diện S3.
3. Click **Delete**.
![Clean up reources](/images/7-cleanup/cleanup-013.png?featherlight=false&width=90pc)
4. Điền tên bucket sau đó click **Delete bucket** để xóa S3 bucket.
![Clean up reources](/images/7-cleanup/cleanup-014.png?featherlight=false&width=90pc)
5. Làm tương tự cho S3 bucket **elasticbeanstalk-us-east-1**
{{% notice note %}} 
Bạn có thể phải chỉnh sửa **bucket policy** của S3 bucket **elasticbeanstalk-us-east-1**để có quyền xóa bucket này
{{% /notice %}}



