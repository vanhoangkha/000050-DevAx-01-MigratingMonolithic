+++
title = "Chuyển đổi Ứng dụng Monolith"
date = 2021
weight = 1
chapter = false
+++

# Chuyển đổi Ứng dụng Monolith

Trong bài thực hành này, bạn sẽ tìm hiểu cách triển khai ứng dụng web **TravelBuddy** để chạy trên AWS

Bạn sẽ học cách sử dụng AWS SDKs để truy vấn và thao tác với môi trường AWS thông qua code thông qua 2 bài tập.


#### Nội dung
Sau khi hoàn thành bài thực hành, bạn sẽ có thể:

- Sử dụng AWS Console để triển khai và xác minh các tài nguyên AWS sử dụng AWS CloudFormation template.
- Sử dụng công cụ AWS Tools cho Eclipse để triển khai ứng dụng Java tới môi trường Elastic Beanstalk.
- Cài đặt và cấu hình công cụ AWS Elastic Beanstalk CLI
- Sử dụng AWS Elastic Beanstalk CLI để triển khai bản cập nhật tới một môi trường Elastic Beanstalk đã có.
- Sử dụng AWS SDK để truy vấn và chỉnh sửa môi trường AWS environment thông qua code

#### Kiến thức kỹ thuật cần có
Để có thể hoàn thành bài thực hành này, bạn nên làm quen với môi trường phát triển ứng dụng Eclipse, ngôn ngữ lập trình Java, ngôn ngữ dòng lệnh/terminal.

#### Môi trường
Tất cả tài nguyên cần thiết để bắt đầu bài thực hành được cung cấp trong CloudFomation template, sử dụng template này để khởi tạo các tài nguyên cho bài thực hành.
Sơ đồ sau mô tả các tài nguyên được triển khai trong bài thực hành.

![Diagram](../../../images/1/0.png?width=50pc)

#### Nội dung

1. [Chuẩn bị](1-prerequisites/)
2. [Kiểm tra tại máy chủ cục bộ](2-test-local/)
3. [Triển khai ứng dụng](3-deploy-app/)
4. [Cập nhật ứng dụng](4-update-app/)
5. [Truy vấn API](5-query-api/)
6. [Kết luận](6-conclusion/)
7. [Tham khảo](7-resources/)