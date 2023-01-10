+++
title = "Setup the Database"
date = 2020
weight = 4
chapter = false
pre = "<b>2.4. </b>"
+++
#### Setup the Database 
1. Connect to the Windows Instance, open the command prompt
2. Execute the below command, change **<rds_host>** by **RDS endpoint**
```
mysql -u root --password=labpassword -h <rds_host>
```

![Connect to the Windows Instance](/images/2-prepare/2.4-setupdatabase/setupdatabase-001a.png?featherlight=false&width=90pc)

![Connect to the Windows Instance](/images/2-prepare/2.4-setupdatabase/setupdatabase-001.png?featherlight=false&width=60pc)

3. Execute the below command to select the database named **travelbuddy**
```
use travelbuddy
```

![Connect to the Windows Instance](/images/2-prepare/2.4-setupdatabase/setupdatabase-002.png?featherlight=false&width=60pc)

4. Execute the below command to watch the tables in the database .
```
show tables;
```
* We will see 2 tables in the database

![Connect to the Windows Instance](/images/2-prepare/2.4-setupdatabase/setupdatabase-003.png?featherlight=false&width=60pc)
