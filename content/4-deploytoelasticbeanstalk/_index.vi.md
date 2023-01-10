+++
title = "Triển khai trên ElasticBeanstalk "
weight = 4
chapter = false
pre = "<b>4. </b>"
+++
#### Triển khai trên ElasticBeanstalk 

Bây giờ chúng ta biết rằng ứng dụng đang chạy tốt, chúng ta sẽ tạo một môi trường mới trong AWS bằng **Elastic Beanstalk** và lưu trữ ứng dụng web **TravelBuddy** ở đó để người dùng có thể truy cập vào Internet. Elastic Beanstalk loại bỏ gánh nặng cấp phép và quản lý các ứng dụng web-based. Ứng dụng của bạn có thể được di chuyển sang Elastic Beanstalk mà không cần bất kỳ sửa đổi nào, vì vậy đây là cách dễ nhất để di chuyển ứng dụng đang tồn tại.

#####  Xây dựng tập tin WAR
1. Dừng máy chủ Tomcat đang chạy
* Click **teminate icon**

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-001.png?featherlight=false&width=90pc)

2. Click chuột phải vào thư mục project
* Click **Export**
* Click **WAR file**

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-002.png?featherlight=false&width=90pc)

3. Trong phần **WAR Export**
* Click **Browser**
* Chọn vị trí lưu phù hợp cho tập tin.
* Click **Finish**

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-003.png?featherlight=false&width=90pc)


##### Tạo ứng dụng Elastic beanstalk
1. Truy cập [**AWS Elastic Beanstalk console**](https://console.aws.amazon.com/elasticbeanstalk/).
* Click **Create Aplication**.

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-004.png?featherlight=false&width=90pc)

2. Tại mục **Application name**, nhập ```TravelBuddy```
* Chọn **Tomcat** là platform

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-005.png?featherlight=false&width=90pc)

3. Trong phần **Application code**, chọn **Upload your code**
* Trong phần **Source code origin**
* Chọn **Local file**
* Click **Choose file**
* Chọn tập tin **travelbuddy.war** đã tạo ở bước trước
* Click **Configure more options**

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-006.png?featherlight=false&width=90pc)

4. Trong phần **Presets**, Click **High availability**

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-007.png?featherlight=false&width=90pc)

{{% notice info %}} 
Điều này sẽ thay đổi cấu hình để hỗ trợ nhiều máy chủ web phía sau Elastic Load Balancer và triển khai auto-scaling.
{{% /notice %}}

5. Trong phần **Network**, Click **Edit**

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-008.png?featherlight=false&width=90pc)


6. Trong phần **VPC**, chọn **CdkStack/DevAxNetworkVPC**

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-009.png?featherlight=false&width=90pc)


7. Trong phần **Load balancer settings**, 
* Chọn **Public** cho **Visibility**
* Tại mục **Load balancer subnets**, chọn 2 Public Subnets 

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-010.png?featherlight=false&width=90pc)

8. Trong mục **Instance subnets**, chọn 2 Private subnets.

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-011.png?featherlight=false&width=90pc)

* Kéo màn hình xuống dưới sau đó Click **Save**
9. Trong phần **Security**, Click **Edit**

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-012.png?featherlight=false&width=90pc)

10. Trong phần **EC2 key pair**, chọn key pair **KPforDevAxInstances** 
* Click **Save**

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-013.png?featherlight=false&width=90pc)

11. Trong phần **Instances**, Click **Edit**

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-014.png?featherlight=false&width=90pc)

12. Tại mục **EC2 security groups**, chọn security group có tên **DBSecurityGroup**
* Click **Save**

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-015.png?featherlight=false&width=90pc)

13. Trong phần **Capacity**, Click **Edit**

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-016.png?featherlight=false&width=90pc)

14. Tại mục **Instance type**, chọn **t3.medium**

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-017.png?featherlight=false&width=90pc)

* Kéo màn hình xuống dưới sau đó Click **Save**
15. Trong phần **Software**, Click **Edit**

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-018.png?featherlight=false&width=90pc)

16. Trong bảng **Environment properties**, và điền các thông tin như hình
| Name &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | Value                                                        |
| --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| JDBC_CONNECTION_STRING                                                                                                            | jdbc:mysql://**[RDSEndpoint]**:3306/travelbuddy?useSSL=false |
| JDBC_UID                                                                                                                          | root                                                         |
| JDBC_PWD                                                                                                                          | labpassword                                                  |
* Click **Save**


![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-019.png?featherlight=false&width=90pc)

17. Kéo màn hình xuống dưới sau đó Click **Create app**
{{% notice note %}} 
Elastic Beanstalk sẽ tiến hành tạo Môi trường mới để chạy trang web TravelBuddy của bạn. Quá trình này sẽ mất vài phút trong khi AWS Elastic Beanstalk tạo Elastic Load Balancer, EC2 instance, Launch configuration, Security Groups,…
{{% /notice %}}

18. Khi quá trình triển khai hoàn tất
* Click **Environments**
* Chúng ta sẽ thấy URL của trang web TravelBuddy được khởi chạy trên Elastic Beanstalk

![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-020.png?featherlight=false&width=90pc)
