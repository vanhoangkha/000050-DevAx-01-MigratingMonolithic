+++
title = "Cài đặt Database"
weight = 3
chapter = false
pre = "<b>1.3. </b>"
+++

#### Kết nối tới cơ sở dữ liệu
1. Truy cập máy ảo window, mở command prompt
2. Nhập câu lệnh sau vào command prompt, thay <rds_host> bằng địa chỉ RDS endpoint
```bash
mysql -u root --password=labpassword -h <rds_host>
```
{{%notice tip%}}
Mật khẩu cho MySQL instance là *labpassword*, hiển thị ở trên
{{%/notice%}}
#### Xem dữ liệu trong cơ sở dữ liệu
3. Bạn sẽ thấy dấu nhắc lệnh *mysql>*
4. Một cơ sở dữ liệu đã được cài đặt sẵn tên  là ***travelbuddy***. Chúng ta cần chọn cơ sở dữ liệu này bằng lệnh 
```bash
use travelbuddy
```
Bạn sẽ thấy thông báo *Database changed*

5.  Sử dụng câu lệnh sau để xem các table có trong cơ sở dữ liệu.
```bash
show tables;
```
Bạn sẽ thấy 2 table có trong database
![Database](../../../images/1/21.png?width=90pc)