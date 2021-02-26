+++
title = "Cập nhật ứng dụng"
date = 2021
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

Bạn vừa triển khai trên môi trường AWS Elastic Beanstalk. Giả sử rằng người quản lý của bạn vừa thông báo cho bạn rằng chủ doanh nghiệp yêu cầu thay đổi ứng dụng và bạn cần thực hiện thay đổi mã nguồn ứng dụng, tạo tệp WAR mới và đẩy tệp đó vào môi trường ứng dụng Beanstalk.

AWS Elastic Beanstalk có nhiều cách khác nhau để bạn có thể thực hiện việc này, nhưng nếu bạn chưa quen với Elastic Beanstalk, bạn có khả năng sử dụng phương pháp thủ công. Mặc dù phương pháp này có thể được sử dụng nhưng bạn cần phải viết tài liệu để bất kỳ nhân viên vận hành nào cũng có thể áp dụng các bản cập nhật một cách chính xác.

Một phương pháp ưu tiên sẽ là tự động hóa việc triển khai, nhưng bạn sẽ tự động hóa việc triển khai Elastic Beanstalk như thế nào?

Để giải quyết vấn đề này, chúng tôi chuyển sang dòng lệnh và sử dụng một công cụ được tạo riêng để tự động hóa việc triển khai các ứng dụng Beanstalk.