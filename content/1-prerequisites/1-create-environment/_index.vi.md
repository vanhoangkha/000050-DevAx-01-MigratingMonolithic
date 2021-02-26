+++
title = "Chuẩn bị môi trường"
weight = 1
chapter = false
pre = "<b>1.1. </b>"
+++

#### Chuẩn bị môi trường
Trong bài thực hành này, chúng ta sẽ sử dụng CloudFormation template đã cung cấp và cài đặt sẵn các tài nguyên cần thiết.

1. Trước tiên, cần tạo một Keypair cho các máy ảo trong bài thực hành. Truy cập EC2 console, chọn **Keypairs**
2. Chọn **Create key pair**
![CloudFormation](../../../images/1/1.png?width=90pc)
3. Nhập tên keypair **KPforDevAxInstances**, chọn định dạng tập tin **pem** và chọn **Create key pair**
![CloudFormation](../../../images/1/2.png?width=90pc)
4. Một cửa sổ xuất hiện để chọn nơi lưu trữ tập tin keypair. Bạn cần lưu trữ keypair này để truy cập vào máy ảo EC2 trong các bước sau
5. Tải CloudFormation template
{{%attachments /%}}
6. Truy cập **AWS CloudFormation**
![CloudFormation](../../../images/1/3.png?width=90pc)
7. Chọn **Create stack**, chọn **With new resources (standard)**
![CloudFormation](../../../images/1/4.png?width=90pc)
8. Tại mục **Prerequisite - Prepare template** chọn **Template is ready**
9. Tại mục **Template source**, chọn **Upload a template file**, nhấp chọn **Choose file** và trỏ tới file template đã tải xuống ở bước 5. Chọn **Next**
![CloudFormation](../../../images/1/5.png?width=90pc)
10. Nhập tên stack tại mục **Stack name**
11. Chọn keypair **KPforDevAxInstances** cho mục **EEKeyPair** và chọn **Next**
![CloudFormation](../../../images/1/6.png?width=90pc)
12. Chọn **Next** tại trang **Configure stack options**
![CloudFormation](../../../images/1/7.png?width=90pc)
13.  Chọn **Create stack**
![CloudFormation](../../../images/1/8.png?width=90pc)
14. Chúng ta cần chờ một vài phút để các tài nguyên được khởi tạo và cấu hình.
Tiếp theo hãy cùng khám phá các tài nguyên mà CloudFormation template đã định nghĩa.
![Diagram](../../../images/1/0.png?width=90pc)
