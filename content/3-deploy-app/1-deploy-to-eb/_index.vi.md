+++
title = "Triển khai trên ElasticBeanstalk"
weight = 1
chapter = false
pre = "<b>3.1. </b>"
+++

Bây giờ chúng ta biết rằng ứng dụng đang chạy tốt, bạn sẽ tạo một môi trường mới trong AWS bằng Elastic Beanstalk và lưu trữ ứng dụng web TravelBuddy ở đó để người dùng có thể truy cập vào Internet. Elastic Beanstalk loại bỏ gánh nặng cấp phép và quản lý các ứng dụng web-based. Ứng dụng của bạn có thể được di chuyển sang Elastic Beanstalk mà không cần bất kỳ sửa đổi nào, vì vậy đây là cách dễ nhất để di chuyển ứng dụng đang tồn tại.
Đầu tiên, chúng ta cần xây dựng một tập tin WAR
1. Dừng máy chủ Tomcat đang chạy. Trong Eclipse, chọn **Window**, chọn **Show View** và chọn **Servers**. Nhấp chuột phải và chọn **Stop**
2. Nhấp chuột phải vào project TravelBuddy và chọn **Export**, chọn WAR File (dưới mục Web). Chọn **Next**.
![DeployApp](../../../../images/3/1.png?width=90pc)
3. Chọn **Browse...** và chọn vị trí lưu phù hợp cho tập tin.
4. Chọn *Overwrite existing file* nếu cần
5. Chọn **Finish**
![DeployApp](../../../../images/3/2.png?width=90pc)
{{% notice tip%}}
Ngoài ra, nếu muốn, bạn có thể sử dụng Maven từ dòng lệnh để tạo tệp WAR, bằng cách sử dụng terminal theo hướng dẫn bên dưới:
{{%/notice%}}
   6. Sử dụng lệnh *cd* để di chuyển tới thư mục chứa tập tin *pom.xml*\
   7. Sử dụng lệnh *mvn package* để đóng gói và tạo tập tin WAR, tập tin được tạo sẽ có tên *travelbuddy.war* và nằm trong thư mục *target*
#### Tạo ứng dụng Elastic beanstalk
8. Truy cập AWS Console, vào AWS Elastic Beanstalk.
9. Chọn **Create Application**
![DeployApp](../../../../images/3/3.png?width=90pc)
10. Nhập *TravelBuddy* tại mục **Application name**
![DeployApp](../../../../images/3/4.png?width=90pc)
11. Với **Platform**, chọn **Tomcat**
![DeployApp](../../../../images/3/5.png?width=90pc)
12. Với **Application Code** chọn **Upload your code**
13. Trong cửa sổ *Source code origin*, chọn **Local file** và chọn **Choose file**
14. Trỏ tới tập tin *travelbuddy.war* đã tạo ở bước trước và chọn **Open**
15. Sau khi tập tin đã được tải lên thành công, chọn **Configure more options**.
![DeployApp](../../../../images/3/6.png?width=90pc)
16. Cửa sổ *Configure Travelbuddy-env* xuất hiện, với **Configuration Presets** chọn **High availability**. 
![DeployApp](../../../../images/3/7.png?width=90pc)
Điều này sẽ thay đổi cấu hình để hỗ trợ nhiều máy chủ web phía sau Elastic Load Balancer và triển khai auto-scaling

#### Cấu hình mạng
17. Tìm thẻ **Network** và chọn **Edit**
18. Trong trang **Modify Network**, tại mục **VPC** chọn **CdkStack/DevAxNetworkVPC**
![DeployApp](../../../../images/3/8.png?width=90pc)
19. Trong mục **Load balancer settings**, chọn **Public** cho **visibility**
20. Trong mục **Load balancer subnets**, đánh dấu chọn 2 Public Subnets
![DeployApp](../../../../images/3/9.png?width=90pc)
21. Trong mục **Instance subnets**, đánh dấu chọn 2 Private subnets.
22. Chọn **Save**
![DeployApp](../../../../images/3/10.png?width=90pc)

#### Cấu hình instances và bảo mật

23.  Tìm thẻ **Security** và chọn **Edit**
24.  Bên dưới mục **Virtual Machine Permissions**, với **EC2 key pair**, chọn key pair **KPforDevAxInstances** đã tạo.
25.  Chọn **Save**
![DeployApp](../../../../images/3/11.png?width=90pc)
26.  Tìm thẻ **Instances** và chọn **Edit**
27.  Dưới mục **EC2 security groups**, chọn security group có tên **DBSecurityGroup**
![DeployApp](../../../../images/3/12.png?width=90pc)
28. Tìm thẻ **Capacity** và chọn **Edit**
29. Dưới mục **Instance type**, chọn **t3.medium** và chọn **Save**
![DeployApp](../../../../images/3/13.png?width=90pc)
#### Cấu hình phần mềm

30. Tìm thẻ **Software** và chọn **Edit**
31. Cuộn xuống bảng **Environment properties**, và điền các thông tin như hình
![DeployApp](../../../../images/3/14.png?width=90pc)
32. Chọn **Save**

#### Tạo môi trường ElasticBeanstalk

33. Chọn **Create app**
![DeployApp](../../../../images/3/15.png?width=90pc)
34. Elastic Beanstalk sẽ tiến hành tạo Môi trường mới để chạy trang web TravelBuddy của bạn. Quá trình này sẽ mất vài phút trong khi AWS Elastic Beanstalk tạo Elastic Load Balancer, EC2 instance, Launch configuration, Security Groups,...
35. Khi quá trình triển khai hoàn tất, chọn Environment URL bên cạnh **URL** ở đầu trang.
Bạn sẽ được đưa tới trang web TravelBuddy được khởi chạy trên Elastic Beanstalk, với các chuyến bay và khách sạn đặc biệt được lấy từ cơ sở dữ liệu MySQL chạy trên cơ sở dữ liệu RDS-hosted MySQL.
