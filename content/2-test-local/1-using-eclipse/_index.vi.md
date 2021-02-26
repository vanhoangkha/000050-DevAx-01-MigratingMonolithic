+++
title = "Sử dụng Eclipse IDE"
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++

#### Sử dụng Eclipse IDE

1. Mở IDE Eclipse.
2. Chọn **File** và chọn **Import...**
3. Dưới dòng *Select an import wizard* chọn **Maven**, chọn thư mục **Existing Maven Projects** và chọn **Next**
![Eclipse](../../../images/2/1.png?width=90pc)
1. Chọn **Browse** và lựa chọn thư mục TravelBuddy, sau đó chọn **Select Folder**
2. Chọn **Finish**
3. Bạn sẽ cần phải đợi Maven tải xuống tất cả các tài nguyên cần thiết. Tỷ lệ phần trăm tải xuống hoàn tất sẽ được hiển thị ở góc dưới cùng bên phải.
4. Đi đến **Project Explorer** và mở đường dẫn *TravelBuddy/src/main/webapp/WEB-INF/spring/appServlet*
5. Mở file **servlet-context.xml**, xem mã nguồn dưới dạng **Source** và xác định vị trí của đoạn code bên dưới![Eclipse](../../../../images/2/2.png?width=90pc)
{{% notice note %}}
Không chỉnh sửa đoạn mã nguồn trên, nhưng lưu ý rằng mã này sử dụng các biến môi trường để định cấu hình máy chủ và tên người dùng / mật khẩu cho cơ sở dữ liệu MySQL. Khi bạn thực thi mã này trên máy chủ, các biến môi trường này cho phép bạn, tại thời điểm thực thi, truy cập đúng máy chủ.
{{% /notice %}}
{{% notice warning %}}
Bạn phải đặt các biến môi trường này nếu không ứng dụng sẽ bị lỗi.
{{% /notice %}}
{{% notice tip %}}
Trong bài thực hành này, bạn sẽ đặt các biến này để cho phép thực thi cục bộ với quyền truy cập từ xa vào RDS instance đang chạy cơ sở dữ liệu TravelBuddy. Sau đó, sau khi chuyển ứng dụng sang AWS Elastic Beanstalk, bạn sẽ học cách đặt các biến này làm thông số cấu hình trong môi trường Elastic Beanstalk.
{{% /notice%}}
#### Cấu hình biến môi trường của cơ sở dữ liệu để thực thi cục bộ

Bây giờ bạn sẽ cấu hình máy chủ **Tomcat v9.x** cục bộ để chạy TravelBuddy trên máy tính cục bộ dùng để phát triển mã nguồn.\
9. Trong Eclipse, chọn **Window** > **Show view** > **Servers**. Bạn có thể cần chọn **Other…** để chọn chế độ xem **Servers** nếu nó không được cung cấp trong danh sách ngay từ đầu.
![Eclipse](../../../../images/2/3.png?width=90pc)
10.  Trong cửa sổ **Servers** , chọn **No servers are available. Click this link to create a new server…**\
11.  Mở **Apache**, chọn **Tomcat v9.x Server**, và chọn **Next**.
![Eclipse](../../../../images/2/4.png?width=50pc)
12.  Chọn **Browse...** và trỏ tới thư mục cài đặt *Tomcat v9.x Server*. Trong workspace, máy chủ Tomcat được đặt trong thư mục ẩn, vì vậy hãy sao chép và dán đường dẫn sau vào thanh địa chỉ *C:\ProgramData\Tomcat9*, sau đó nhấp vào **Select Folder**\
13.  Chọn **Finish**
![Eclipse](../../../../images/2/5.png?width=50pc)
14.  Trong **Project Explorer**, mở **Servers > Tomcat v9.x Server at localhost-config**.\
15.  Mở tập tin **context.xml** và dán đoạn mã nguồn sau vào trước dòng cuối(</Context>)\
16.  Thay <RDSEndpoint> bằng giá trị của **RDS Endpoint** và lưu file lại
![Eclipse](../../../../images/2/6.png?width=90pc)
17.  Click chuột phải vào thư mục project và chọn **Run As...**, chọn **Run on Server**. 
![Eclipse](../../../../images/2/7.png?width=90pc)
Nếu không thấy **Run on Server**, click chuột phải vào thư mục project, chọn **Maven** và chọn **Update Project...** và chọn **OK**.\
18.   Chọn **Tomcat v9.0 server** và chọn **Finish**.\
19.   Ứng dụng sẽ khởi động trong Java Spring giống như một ứng dụng Spring bình thường. Bạn sẽ thấy các thông báo xuất hiện trong cửa sổ bảng điều khiển, bao gồm việc khám phá các Request Handler Mappings cho các đường dẫn khác nhau được ứng dụng hiển thị. \
Trong giây lát, trình duyệt tích hợp IDE sẽ xuất hiện và bạn sẽ thấy ứng dụng TravelBuddy được mở. Ứng dụng sẽ hiển thị dữ liệu được truy xuất từ RDS instance đang chạy trong AWS.
{{%notice tip%}}
Bạn có thể truy cập tới ứng dụng web TravelBuddy bằng trình duyệt với địa chỉ http://localhost:8080/travelbuddy/
{{%/notice%}}
**Lưu ý những điều dưới đây:**
- Ứng dụng đang chạy trên máy chủ tomcat cục bộ của bạn
- Ứng dụng sử dụng cơ sở dữ liệu Amazon RDS MySQL.