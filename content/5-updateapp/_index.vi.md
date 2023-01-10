+++
title = "Cập nhật ứng dụng "
date = 2020
weight = 5
chapter = false
pre = "<b>5. </b>"
+++
#### Cập nhật ứng dụng 
Chúng ta vừa triển khai trên môi trường AWS Elastic Beanstalk. Giả sử rằng người quản lý của bạn vừa thông báo cho bạn rằng chủ doanh nghiệp yêu cầu thay đổi ứng dụng và bạn cần thực hiện thay đổi mã nguồn ứng dụng, tạo tệp WAR mới và đẩy tệp đó vào môi trường ứng dụng Beanstalk.

AWS Elastic Beanstalk có nhiều cách khác nhau để bạn có thể thực hiện việc này, nhưng nếu bạn chưa quen với Elastic Beanstalk, bạn có khả năng sử dụng phương pháp thủ công. Mặc dù phương pháp này có thể được sử dụng nhưng bạn cần phải viết tài liệu để bất kỳ nhân viên vận hành nào cũng có thể áp dụng các bản cập nhật một cách chính xác.

Một phương pháp ưu tiên sẽ là tự động hóa việc triển khai, nhưng bạn sẽ tự động hóa việc triển khai Elastic Beanstalk như thế nào?

Để giải quyết vấn đề này, chúng ta chuyển sang dòng lệnh và sử dụng một công cụ được tạo riêng để tự động hóa việc triển khai các ứng dụng Beanstalk.

1. Sửa đổi project **TravelBuddy**
* Trong Eclipse IDE, mở tập tin **TravelBuddy/src/main/webapp/WEB-INF/views/index.jsp**
* Tìm từ khóa **Alpaca** và thay đổi thành **Go pack**
* Lưu tập tin

![Update the application](/images/5-updateapp/updateapp-001.png?featherlight=false&width=90pc)

2. Trong Eclipse IDE, nhấn tổ hợp phím **Ctrl**+**Alt**+**Shift**+**T** để mở terminal

![Update the application](/images/5-updateapp/updateapp-002.png?featherlight=false&width=90pc)

3. Trong phần **Launch Terminal**
* Tại mục **Choose terminal**, chọn **Local Terminal**
* Click **OK**

![Update the application](/images/5-updateapp/updateapp-003.png?featherlight=false&width=90pc)

4. Trong terminal, đưa vị trí của bạn về thư mục của TravelBuddy project

![Update the application](/images/5-updateapp/updateapp-004.png?featherlight=false&width=90pc)

5. Chạy lệnh dưới đây để Build phiên bản mới của ứng dụng TravelBuddy bằng Maven
```
mvn package
```

![Update the application](/images/5-updateapp/updateapp-005.png?featherlight=false&width=90pc)

6. Chạy lệnh dưới đây để chuyển sang thư mục chứa tập tin WAR và khởi tạo nội dung để triển khai Elastic Beanstalk
```
cd target\\travelbuddy
eb init --profile devaxacademy
```

![Update the application](/images/5-updateapp/updateapp-006.png?featherlight=false&width=90pc)

7. Với **Select a default region**, nhập số tương ứng với region đang chứa các tài nguyên cho bài thực hành này.
* Với **Select an application to use**, nhập số tương ứng với ứng dụng TravelBuddy và nhấn Enter. Bạn không cần lo lắng nếu xuất hiện thông báo **Cannot setup CodeCommit because there is no Source Control setup, continuing with initialization**.
* Chạy lệnh dưới đây để tải bản mới nhất của ứng dụng lên môi trường Beanstalk
```
eb deploy --profile devaxacademy
```

![Update the application](/images/5-updateapp/updateapp-007.png?featherlight=false&width=90pc)

{{% notice note %}} 
Bây giờ, hãy đợi cho việc triển khai hoàn tất. Bạn có thể theo dõi tiến trình trong cửa sổ terminal. Bạn cũng sẽ thấy tiến trình cập nhật liên quan trong bảng điều khiển AWS Elastic Beanstalk sau khi quá trình tải lên hoàn tất. Khi quá trình cập nhật kết thúc, hãy xác minh thay đổi bạn đã thực hiện đối với trang index.jsp hiện đã có trên trang web hiển thị công khai.
{{% /notice %}}
8. Truy cập trang Web, chúng ta sẽ thấy văn bản đã được cập nhật

![Update the application](/images/5-updateapp/updateapp-008.png?featherlight=false&width=90pc)
