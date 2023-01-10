+++
title = "Clean up resources"
date = 2020
weight = 7
chapter = false
pre = "<b>7. </b>"
+++
You clean up resources in the following order:

#### Delete Elastic Beanstalk application we created
1. Go to [**AWS Elastic Beanstalk console**](https://console.aws.amazon.com/elasticbeanstalk/).
* Click **Applications**.
* Select **TravelBuddy**
* Click **Action**
* Click **Delete application**

![Clean up reources](/images/7-cleanup/cleanup-001.png?featherlight=false&width=90pc)

2. Type ```TravelBuddy``` to confirm, then click **Delete** to delete

![Clean up reources](/images/7-cleanup/cleanup-002.png?featherlight=false&width=90pc)


#### Terminate EC2 Instance
1. Go to [**Amazon EC2 console**](https://console.aws.amazon.com/ec2/).
* On the left navigation bar, click **Intances**.
* Select **DevAxWindowsHost**. 
* Click **Instance state**
* Click **Terminate instance**

![Clean up reources](/images/7-cleanup/cleanup-003.png?featherlight=false&width=90pc)

2. Click **Terminate**

![Clean up reources](/images/7-cleanup/cleanup-004.png?featherlight=false&width=90pc)


#### Delete Users
1. Go to [**AWS IAM Console**](https://console.aws.amazon.com/iamv2/).
* Click **Users**.
* Select **awsstudent**. 
* Click **Delete**

![Clean up reources](/images/7-cleanup/cleanup-005.png?featherlight=false&width=90pc)

2. Type ```awsstudent``` to confirm, then click **Delete**

![Clean up reources](/images/7-cleanup/cleanup-006.png?featherlight=false&width=90pc)

#### Delete CloudFormation Stack
1. Go to [AWS CloudFormation Console](https://console.aws.amazon.com/cloudformation/).
* Select **aws-stack-for-Devax**.
* Click **Delete**

![Clean up reources](/images/7-cleanup/cleanup-007.png?featherlight=false&width=90pc)

2. Click **Delete stack**

![Clean up reources](/images/7-cleanup/cleanup-008.png?featherlight=false&width=90pc)

#### Delete Key Pairs
1. Go to [**Amazon EC2 console**](https://console.aws.amazon.com/ec2/).
* On the left navigation bar, click **Key Pairs**.
* Select **KPforDevAxInstances**. 
* Click **Actions**
* Click **Delete**

![Clean up reources](/images/7-cleanup/cleanup-009.png?featherlight=false&width=90pc)

2. Type ```Delete``` to confirm, then click **Delete** to delete

![Clean up reources](/images/7-cleanup/cleanup-010.png?featherlight=false&width=90pc)

#### Delete S3 bucket
1. Go to [**giao diện quản trị dịch vụ S3**](https://s3.console.aws.amazon.com/s3/).
* Click **Buckets**
* Select S3 bucket was created to save file **Module1.template.yaml** when we create the CloudFormation stack.
* Click **Empty**.

![Clean up reources](/images/7-cleanup/cleanup-011.png?featherlight=false&width=90pc)

2. Type ```permanently delete``` to confirm, then click **Empty** to delete the data of the S3 bucket.

![Clean up reources](/images/7-cleanup/cleanup-012.png?featherlight=false&width=90pc)

* Click **Exit** to back S3 interface.
3. Click **Delete**.

![Clean up reources](/images/7-cleanup/cleanup-013.png?featherlight=false&width=90pc)

4. Type the name of the bucket then click **Delete bucket** to delete S3 bucket.

![Clean up reources](/images/7-cleanup/cleanup-014.png?featherlight=false&width=90pc)

5. Do the same for S3 bucket **elasticbeanstalk-us-east-1**
{{% notice note %}} 
You may edit the **bucket policy** of S3 bucket **elasticbeanstalk-us-east-1** to have permission to delete
{{% /notice %}}