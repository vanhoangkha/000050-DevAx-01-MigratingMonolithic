+++
title = "Tạo CloudFormation stack"
date = 2020
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++
#### Tạo CloudFormation stack
* Chúng ta sẽ dùng tập tin template dưới đây để tạo CloudFormation stack. Template hỗ trợ chúng ta tạo :
  * Một VPC có tên **CdkStack/DevAxNetworkVPC**:
    * 2 Public Subnet
    * 2 Private Subnet
    * 2 NAT gateways
  * Một EC2 Instance có tên **DevAxWindowsHost**
  * Một RDS có tên **ad12azpxp74wamj**
  * User **awsstudent**

{{%attachments title="Template File" style="orange" pattern="Module1.yaml"/%}}

1. Tải tệp tin **Module1.yaml**.
2. Truy cập [**Amazon CloudFormation Console**](https://console.aws.amazon.com/cloudformation/home).
* Click **Stacks**
* Click **Create stack**.
* Click **With new resource (standard)**

![Create CloudFormation stack](/images/2-prepare/2.2-createstack/createstack-001.png?featherlight=false&width=90pc)

3. Trong phần **Specify template**.
* Chọn **Upload a template file**
* Click **Choose file**, sau đó chọn tệp tin **Module1.yaml** chúng ta đã tải về.
* Click **Next**.

![Create CloudFormation stack](/images/2-prepare/2.2-createstack/createstack-002.png?featherlight=false&width=90pc)

4. Trong phần **Stack name** gõ ```aws-stack-for-Devax```.
* Trong phần **Stack name** chọn **KPforDevAxInstances**.
* Click **Next**.

![Create CloudFormation stack](/images/2-prepare/2.2-createstack/createstack-003.png?featherlight=false&width=90pc)

5. Tại trang **Configure stack options**, Kéo màn hình xuống dưới sau đó Click **Next**.

![Create CloudFormation stack](/images/2-prepare/2.2-createstack/createstack-004.png?featherlight=false&width=90pc)

6. Tại trang **Review aws-stack-for-Devax**.
* Kéo màn hình xuống dưới sau đó Click **I acknowledge that AWS CloudFormation might create IAM resources with custom names.**
* Click **Create stack**.

![Create CloudFormation stack](/images/2-prepare/2.2-createstack/createstack-005.png?featherlight=false&width=90pc)

{{% notice note %}} 
**Cloudformation** sẽ mất khoảng 5 phút để tạo stack . Hãy đợi cho đến khi tất cả các stack ở trạng thái **CREATE_COMPLETE**.
{{% /notice %}}

![Create CloudFormation stack](/images/2-prepare/2.2-createstack/createstack-006.png?featherlight=false&width=90pc)

#### Kiểm tra VPC được tạo
1. Truy cập [**Amazon VPC Console**](https://console.aws.amazon.com/vpc/).
* Click **Your VPCs**.
* Chúng ta sẽ thấy 1 VPC có tên **CdkStack/DevAxNetworkVPC**

![Create CloudFormation stack](/images/2-prepare/2.2-createstack/createstack-007.png?featherlight=false&width=90pc)

2. Click **Subnets**.
* Gõ ```CdkStack/DevAxNetworkVPC``` vào ô tìm kiếm. Nhấn **Enter**
* Chúng ta sẽ thấy 4 Subnet

![Create CloudFormation stack](/images/2-prepare/2.2-createstack/createstack-008.png?featherlight=false&width=90pc)

3. Click **NAT Gateways**.
* Gõ ```CdkStack/DevAxNetworkVPC``` vào ô tìm kiếm. Nhấn **Enter**
* Chúng ta sẽ thấy 2 NAT gateways

![Create CloudFormation stack](/images/2-prepare/2.2-createstack/createstack-009.png?featherlight=false&width=90pc)


#### Kiểm tra EC2 Instance được tạo
1. Truy cập [**Amazon EC2 console**](https://console.aws.amazon.com/ec2/).
* Click **Instances**.
* Gõ ```DevAxWindowsHost``` vào ô tìm kiếm. Nhấn **Enter**
* Chúng ta sẽ thấy 1 EC2 Instance có tên **DevAxWindowsHost**

![Create CloudFormation stack](/images/2-prepare/2.2-createstack/createstack-010.png?featherlight=false&width=90pc)


#### Kiểm tra AWS RDS được tạo
1. Truy cập [**Amazon RDS console**](https://console.aws.amazon.com/rds/).
* Click **Databases**.
* Chúng ta sẽ thấy 1 Databases mới.

![Create CloudFormation stack](/images/2-prepare/2.2-createstack/createstack-011.png?featherlight=false&width=90pc)
