+++
title = "Cài đặt Database "
date = 2020
weight = 4
chapter = false
pre = "<b>2.4. </b>"
+++
#### Cài đặt Database 
1. Truy cập máy ảo window, mở command prompt
2. Chạy lệnh dưới đây, thay **<rds_host>** bằng **RDS endpoint**
```
mysql -u root --password=labpassword -h <rds_host>
```
![Connect to the Windows Instance](/images/2-prepare/2.4-setupdatabase/setupdatabase-001.png?featherlight=false&width=60pc)
3. Chạy lệnh dưới đây để chọn cơ sở dữ liệu tên là **travelbuddy**
```
use travelbuddy
```
![Connect to the Windows Instance](/images/2-prepare/2.4-setupdatabase/setupdatabase-002.png?featherlight=false&width=60pc)
4. Chạy lệnh dưới đây để xem các table có trong cơ sở dữ liệu.
```
show tables;
```
* Bạn sẽ thấy 2 table có trong database
![Connect to the Windows Instance](/images/2-prepare/2.4-setupdatabase/setupdatabase-003.png?featherlight=false&width=60pc)