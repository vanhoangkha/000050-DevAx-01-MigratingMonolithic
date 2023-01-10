+++
title = "Truy vấn API dùng Eclipse IDE"
date = 2020
weight = 6
chapter = false
pre = "<b>6. </b>"
+++
#### Truy vấn API dùng Eclipse IDE

Chúng ta sẽ sử dụng Java SDK để kiểm tra môi trường AWS của mình và truy vấn thông tin máy ảo EC2. Điều này cung cấp cho chúng ta một số trải nghiệm về cách chúng ta có thể sử dụng AWS SDK để thao tác trực tiếp các tài nguyên trong tài khoản AWS của chúng ta, để tạo công cụ của riêng chúng ta hoặc kiểm soát việc tạo và quản lý tài nguyên theo chương trình.

{{%attachments title="EC2Report File" style="orange" pattern="EC2Report.zip"/%}}

1. Tải tập tin **EC2Report.zip** và giải nén. 
2. Trong Eclipse IDE
* Click **File** 
* Click **Import**

![Update the application](/images/6-queryapi/queryapi-001.png?featherlight=false&width=90pc)

3. Trong phần **Import**
* Click **Maven**
* Click **Existing Maven Projects**
* Click **Next**

![Update the application](/images/6-queryapi/queryapi-002.png?featherlight=false&width=90pc)

4. Trong phần **Import Maven Projects**, Chọn **Browse** 
* Trỏ tới thư mục **EC2Report** đã giải nén
* Click **Finish**

![Update the application](/images/6-queryapi/queryapi-003.png?featherlight=false&width=90pc)

5. Trong Eclipse IDE, mở tập tin **EC2Report/src/main/java/idevelop/samples/EC2Manager.java**
* Tìm **ReportEC2Environment()** method
* Chỉnh sửa Region cho đúng với region đang thực hiện bài thực hành.
* Lưu file.
{{% notice tip %}} 
Xem cách các thông tin xác thực được truy xuất bằng ProfileCredentialsProvide() bằng cách chỉ định devaxacademy profile. Sau đó, credentials object được sử dụng trong AmazonEC2ClientBuilder
{{% /notice %}}

![Update the application](/images/6-queryapi/queryapi-004.png?featherlight=false&width=90pc)

6. Khởi chạy ứng dụng bằng cách nhấp chuột phải vào ứng dụng  và Click **Run As**
* Click **JUnit Test**

![Update the application](/images/6-queryapi/queryapi-005.png?featherlight=false&width=90pc)

7. Bạn sẽ nhận được kết quả tương tự như hình dưới. Kết quả nhận được hiển thị số lượng EC2 instance trong tài khoản người dùng IAM. 

![Update the application](/images/6-queryapi/queryapi-006.png?featherlight=false&width=90pc)


#### Bài tập tùy chọn
1. Khám phá tập tin **pom.xml** và đảm bảo rằng bạn hiểu cách mà quản lý phụ thuộc hoạt động
2. Thử sử dụng Bảng điều khiển AWS EC2 để tìm thông tin mà bạn đang thấy trong kết quả đầu ra từ bộ kiểm tra EC2Manager. Thông tin nào khác có trong bảng điều khiển AWS EC2 mà chúng tôi không hiển thị trong đầu ra thử nghiệm của mình? Ví dụ: xem lại **instance** object được trả về từ lời gọi **describeInstancesRequest.getReservations()** trong trình gỡ lỗi.
3. Cập nhậtkết quả đầu ra của ứng dụng để hiển thị các Thẻ được liên kết với mỗi EC2 instance. Sau đó, trong bảng điều khiển AWS EC2, gán thẻ cho các máy ảo và xem chúng được hiển thị như thế nào trong kết quả đầu ra ứng dụng EC2Manager.
4. Lập trình tạo một máy ảo mới trong tài khoản của bạn. Bạn cần xác định ImageId, Keypair và security groups. Tham khảo [tài liệu](http://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/run-instance.html) hoặc sử dụng đoạn mã dưới đây
```
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