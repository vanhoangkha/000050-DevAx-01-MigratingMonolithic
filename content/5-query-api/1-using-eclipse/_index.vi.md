+++
title = "Sử dụng Eclipse IDE"
weight = 1
chapter = false
pre = "<b>5.1. </b>"
+++

#### Sử dụng Eclipse IDE
1. Tải tập tin **EC2Report.zip** và giải nén.
{{%attachments /%}}
2. Trong Eclipse IDE, chọn **File -> Import...** 
3. Dưới mục *Select an import wizard* chọn **Maven**, chọn **Existing Maven Projects** và chọn **Next**.
4. Chọn **Browse** và trỏ tới thư mục EC2Report đã giải nén
5. Xem đoạn code tại tập tin *EC2Report/src/main/java/idevelop/samples/EC2Manager.java*. Tìm ***ReportEC2Environment()*** method
6. Xem cách các thông tin xác thực được truy xuất bằng ProfileCredentialsProvide() bằng cách chỉ định *devaxacademy* profile.
Sau đó, credentials object được sử dụng trong **AmazonEC2ClientBuilder**.
Đừng quên chỉnh sửa Region cho đúng với region đang thực hiện bài thực hành.
7. Khởi chạy ứng dụng bằng cách nhấp chuột phải vào ứng dụng và chọn **Run As -> JUnit Test**.
![QueryAPI](../../../../images/5/1.png?width=90pc)
8. Bạn sẽ nhận được kết quả tương tự như hình dưới. Kết quả nhận được hiển thị số lượng EC2 instance trong tài khoản người dùng IAM.
![QueryAPI](../../../../images/5/2.png?width=90pc)
#### Bài tập tùy chọn
9. Khám phá tập tin ***pom.xml*** và đảm bảo rằng bạn hiểu cách mà quản lý phụ thuộc hoạt động
10. Thử sử dụng Bảng điều khiển AWS EC2 để tìm thông tin mà bạn đang thấy trong kết quả đầu ra từ bộ kiểm tra EC2Manager. Thông tin nào khác có trong bảng điều khiển AWS EC2 mà chúng tôi không hiển thị trong đầu ra thử nghiệm của mình? Ví dụ: xem lại **instance** object được trả về từ lời gọi **describeInstancesRequest.getReservations()** trong trình gỡ lỗi.
11. Cập nhậtkết quả đầu ra của ứng dụng để hiển thị các Thẻ được liên kết với mỗi EC2 instance. Sau đó, trong bảng điều khiển AWS EC2, gán thẻ cho các máy ảo và xem chúng được hiển thị như thế nào trong kết quả đầu ra ứng dụng EC2Manager.
12. Lập trình tạo một máy ảo mới trong tài khoản của bạn. Bạn cần xác định ImageId, Keypair và security groups. Tham khảo [tài liệu](http://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/run-instance.html) hoặc sử dụng đoạn mã dưới đây
```java
// At the top
import com.amazonaws.services.ec2.model.Instance;
import com.amazonaws.services.ec2.model.InstanceNetworkInterfaceSpecification;
import com.amazonaws.services.ec2.model.Reservation;
import com.amazonaws.services.ec2.model.RunInstancesRequest;
import com.amazonaws.services.ec2.model.RunInstancesResult;

// In your method
System.out.println("Creating EC2 Server...");
RunInstancesRequest runInstancesRequest =
			new RunInstancesRequest();

runInstancesRequest.withImageId("ami-fd9cecc7")
					.withInstanceType("t2.small")
					.withMinCount(1)
					.withMaxCount(1)
					.withKeyName("devaxacademy")
					.withNetworkInterfaces(new InstanceNetworkInterfaceSpecification()
							.withAssociatePublicIpAddress(true)
							.withDeviceIndex(0)
							.withSubnetId("subnet-XXX")
							.withGroups("sg-XXX"));

							
RunInstancesResult result = ec2.runInstances(runInstancesRequest);

```