+++
title = "Cập nhật ứng dụng TravelBuddy"
weight = 1
chapter = false
pre = "<b>4.1. </b>"
+++


Bây giờ chúng ta sẽ tạo một thay đổi đơn giản đổi với mã nguồn ứng dụng TravelBuddy.

#### Sửa đổi TravelBuddy
1. Trong Eclipse IDE, mở tập tin *TravelBuddy/src/main/webapp/WEB-INF/views/index.jsp*
2. Tìm từ khóa **Alpaca**
3. Thay đổi tiêu đề thành **Go pack** 
4. Lưu tập tin
![Update](../../../../images/4/1.png?width=90pc)
#### Triển khai các thay đổi sử dụng AWS EBCLI

5. Trong terminal, đảm bảo rằng bạn đang trong thư mục của **TravelBuddy project**
6. Build phiên bản mới của ứng dụng TravelBuddy bằng Maven
``` bash
cd \<into the directory that has the project's pom.xml file\>
mvn package
```
7. Chuyển sang thư mục chứa tập tin WAR và khởi tạo nội dung để triển khai Elastic Beanstalk bằng công cụ eb vừa cài đặt.
```bash
cd target\\travelbuddy
eb init --profile devaxacademy
```
8. Với **Select a default region**, nhập số tương ứng với region đang chứa các tài nguyên cho bài thực hành này.
9. Với **Select an application to use**, nhập số tương ứng với ứng dụng TravelBuddy và nhấn Enter. Bạn không cần lo lắng nếu xuất hiện thông báo *TravelBuddy and hit enter. If you receive a message Cannot setup CodeCommit because there is no Source Control setup, continuing with initialization*.
10. Chạy lệnh dưới đây để tải bản mới nhất của ứng dụng lên môi trường Beanstalk
```bash
eb deploy --profile devaxacademy
```
Bây giờ, hãy đợi cho việc triển khai hoàn tất. Bạn có thể theo dõi tiến trình trong cửa sổ terminal. Bạn cũng sẽ thấy tiến trình cập nhật liên quan trong bảng điều khiển AWS Elastic Beanstalk sau khi quá trình tải lên hoàn tất. Khi quá trình cập nhật kết thúc, hãy xác minh thay đổi bạn đã thực hiện đối với trang index.jsp hiện đã có trên trang web hiển thị công khai.

Làm mới tab trình duyệt đang hiển thị trang web TravelBuddy và kiểm tra xem văn bản cập nhật có xuất hiện hay không
