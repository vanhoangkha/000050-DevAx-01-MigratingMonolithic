+++
title = "Kiểm tra ở máy chủ cục bộ bằng Eclipse IDE"
date = 2020
weight = 3
chapter = false
pre = "<b>3. </b>"
+++
#### Kiểm tra ở máy chủ cục bộ bằng Eclipse IDE
Trong phần này, chúng ta sẽ mở project, cập nhật cấu hình kết nối cơ sở dữ liệu, sau đó khởi chạy project trong môi trường phát triển cục bộ để kiểm tra xem project đang xây dựng và kết nối với cơ sở dữ liệu một cách chính xác.
1. Mở **IDE Eclipse**
![Test Locally](/images/3-testlocally/testlocally-001.png?featherlight=false&width=90pc)
2. Trong phần **Menu**, Click **File**
* Click **Import...**
![Test Locally](/images/3-testlocally/testlocally-002.png?featherlight=false&width=90pc)
3. Trong phần **Import**, Click **Maven**
* Click **Existing Maven Projects**
* Click **Next**
![Test Locally](/images/3-testlocally/testlocally-003.png?featherlight=false&width=90pc)
4. Trong phần **Import Maven Projects**
* Click **Browse**
* Chọn thư mục **TravelBuddy** 
* Click **Finish**
![Test Locally](/images/3-testlocally/testlocally-004.png?featherlight=false&width=90pc)
{{% notice note %}} 
Bạn sẽ cần phải đợi Maven tải xuống tất cả các tài nguyên cần thiết. Tỷ lệ phần trăm tải xuống hoàn tất sẽ được hiển thị ở góc dưới cùng bên phải.
{{% /notice %}}
5. Đi đến Project Explorer và Mở file có đường dẫn **TravelBuddy/src/main/webapp/WEB-INF/spring/appServlet/servlet-context.xml**
* Click **Source**
* xác định vị trí của đoạn code
```
<beans:bean id="dataSource" class="org.apache.tomcat.jdbc.pool.DataSource"
		destroy-method="close">		
		<beans:property name="driverClassName" value="com.mysql.jdbc.Driver" />
		<beans:property name="url" value="${JDBC_CONNECTION_STRING}" />
		<beans:property name="username" value="${JDBC_UID}" />
		<beans:property name="password" value="${JDBC_PWD}" />	
		<beans:property name="jdbcInterceptors" value="com.amazonaws.xray.sql.mysql.TracingInterceptor" />
</beans:bean>
```
![Test Locally](/images/3-testlocally/testlocally-005.png?featherlight=false&width=90pc)
{{% notice note %}} 
Không chỉnh sửa đoạn mã nguồn trên, nhưng lưu ý rằng mã này sử dụng các biến môi trường để định cấu hình máy chủ và tên người dùng / mật khẩu cho cơ sở dữ liệu MySQL. Khi bạn thực thi mã này trên máy chủ, các biến môi trường này cho phép bạn, tại thời điểm thực thi, truy cập đúng máy chủ.
{{% /notice %}}
{{% notice warning %}} 
Bạn phải đặt các biến môi trường này nếu không ứng dụng sẽ bị lỗi.
{{% /notice %}}
{{% notice tip %}} 
Trong bài thực hành này, bạn sẽ đặt các biến này để cho phép thực thi cục bộ với quyền truy cập từ xa vào RDS instance đang chạy cơ sở dữ liệu TravelBuddy. Sau đó, sau khi chuyển ứng dụng sang AWS Elastic Beanstalk, bạn sẽ học cách đặt các biến này làm thông số cấu hình trong môi trường Elastic Beanstalk.
{{% /notice %}}
6. Trong phần **Menu**, Click **Window**
* Click **Show view**
* Click **Servers**
{{% notice note %}} 
Bạn có thể cần chọn **Other…** để chọn chế độ xem **Servers** nếu nó không được cung cấp trong danh sách ngay từ đầu.
{{% /notice %}}
![Test Locally](/images/3-testlocally/testlocally-006.png?featherlight=false&width=90pc)
7. Trong phần **Servers**
* Click **No servers are available. Click this link to create a new server…**
![Test Locally](/images/3-testlocally/testlocally-007.png?featherlight=false&width=90pc)
8. Trong phần **Define a New Server**
* Click **Apache**
* Click **Tomcat v9.x Server**
* Click **Next**
![Test Locally](/images/3-testlocally/testlocally-008.png?featherlight=false&width=90pc)
9. Trong workspace, máy chủ Tomcat được đặt trong thư mục ẩn, vì vậy hãy sao chép và dán đường dẫn sau vào thanh địa chỉ ```C:\ProgramData\Tomcat9```
* Click **Finish**
![Test Locally](/images/3-testlocally/testlocally-009.png?featherlight=false&width=90pc)
10. Mở file có đường dẫn **Servers > Tomcat v9.x Server at localhost-config/context.xml**
* Dán đoạn mã nguồn sau vào trước dòng **</ Context>**
```
<!-- Environment variables -->
<Parameter name="JDBC_CONNECTION_STRING"  value="jdbc:mysql://<RDSEndpoint>:3306/travelbuddy?useSSL=false"  override="false"/>
<Parameter name="JDBC_UID"  value="root"  override="false"/>
<Parameter name="JDBC_PWD"  value="labpassword"  override="false"/>
```
{{% notice note %}} 
Thay **< RDSEndpoint>** bằng giá trị của **RDS endpoint**
{{% /notice %}}
* Lưu file lại
![Test Locally](/images/3-testlocally/testlocally-010.png?featherlight=false&width=90pc)
11. Click chuột phải vào thư mục project
*  Click **Run As**
*  Click **Run on Server**
![Test Locally](/images/3-testlocally/testlocally-011.png?featherlight=false&width=90pc)
{{% notice note %}} 
Nếu không thấy **Run on Server**, click chuột phải vào thư mục project, chọn **Maven** và chọn **Update Project…** và chọn **OK**.
{{% /notice %}}
12. Trong phần **Run On Server**
* Chọn **Tomcat v9.0 server at localhost**
* Click **Finish**
![Test Locally](/images/3-testlocally/testlocally-012.png?featherlight=false&width=90pc)
13. Trong giây lát, trình duyệt tích hợp IDE sẽ xuất hiện và bạn sẽ thấy ứng dụng TravelBuddy được mở. Ứng dụng sẽ hiển thị dữ liệu được truy xuất từ RDS instance đang chạy trong AWS. 
![Test Locally](/images/3-testlocally/testlocally-013.png?featherlight=false&width=90pc)