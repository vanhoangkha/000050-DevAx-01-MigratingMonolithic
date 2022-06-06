+++
title = "Deploy Application to ElasticBeanstalk "
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

#### Deploy to ElasticBeanstalk

Now that we know the app runs, you will create a new environment in AWS using Elastic Beanstalk and host our TravelBuddy web application there so that it can be accessed by users on the Internet. Elastic Beanstalk removes the burden of provisioning and managing web-based applications. Your application can be migrated to Elastic Beanstalk without any modification, so this is the easiest way to migrate the existing application.

#####  Build a WAR file
1. Stop the Tomcat server running locally
* Click **teminate icon**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-001.png?featherlight=false&width=90pc)
2. Right click on the folder project
* Click **Export**
* Click **WAR file**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-002.png?featherlight=false&width=90pc)
3. In the **WAR Export** section
* Click **Browser**
* Select a suitable location to store the WAR file. You will need to access this file again.
* Click **Finish**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-003.png?featherlight=false&width=90pc)

##### Create the Elastic beanstalk application
1. Go to [**AWS Elastic Beanstalk console**](https://console.aws.amazon.com/elasticbeanstalk/).
* Click **Create Aplication**.
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-004.png?featherlight=false&width=90pc)
2. In the **Application name** section, type ```TravelBuddy```
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-005.png?featherlight=false&width=90pc)
3. In the **Platform** section, Select **Tomcat**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-006.png?featherlight=false&width=90pc)
4. In the **Application code** section, select **Upload your code**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-007.png?featherlight=false&width=90pc)
5. In the **Source code origin** section
* Select **Local file**
* Click **Choose file**
* Select file **travelbuddy.war** we created
* Click **Configure more options**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-008.png?featherlight=false&width=90pc)
6. In the **Presets** section, Click **High availability**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-009.png?featherlight=false&width=90pc)
{{% notice info %}} 
This will change the configuration to support multiple web servers behind an Elastic Load Balancer and implement auto-scaling.
{{% /notice %}}
7. In the **Network** section, Click **Edit**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-010.png?featherlight=false&width=90pc)
8. In the **VPC** section, select **CdkStack/DevAxNetworkVPC**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-011.png?featherlight=false&width=90pc)
9. In the **Load balancer settings** section
* Select **Public** for **Visibility**
* In the **Load balancer subnets** section, select 2 Public Subnets 
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-012.png?featherlight=false&width=90pc)
10. In the **Instance subnets** section, select 2 Private subnets.
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-013.png?featherlight=false&width=90pc)
* Drag the screen down, then Click **Save**
11. In the **Security** section, Click **Edit**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-014.png?featherlight=false&width=90pc)
12. In the **EC2 key pair** section, select key pair **KPforDevAxInstances** 
* Click **Save**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-015.png?featherlight=false&width=90pc)
13. In the **Instances** section, Click **Edit**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-016.png?featherlight=false&width=90pc)
14. In the **EC2 security groups** section, select the security group named **DBSecurityGroup**
* Click **Save**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-017.png?featherlight=false&width=90pc)
15. In the **Capacity** section, Click **Edit**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-018.png?featherlight=false&width=90pc)
17. In the **Instance type** section, select **t3.medium**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-019.png?featherlight=false&width=90pc)
* Drag the screen down, then Click **Save**
19. In the **Software** section, Click **Edit**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-020.png?featherlight=false&width=90pc)
20. In the **Environment properties** table, add the information like the below table
| Name &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | Value                                                        |
| --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| JDBC_CONNECTION_STRING                                                                                                            | jdbc:mysql://**[RDSEndpoint]**:3306/travelbuddy?useSSL=false |
| JDBC_UID                                                                                                                          | root                                                         |
| JDBC_PWD                                                                                                                          | labpassword                                                  |
* Click **Save**
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-021.png?featherlight=false&width=90pc)
21. Drag the screen down, then Click **Create app**
{{% notice note %}} 
Elastic Beanstalk will now proceed with creating the new Environment to run your TravelBuddy website. This will take a few minutes while an Elastic Load Balancer, EC2 instance, Launch configuration, Security Groups and more are created for you by AWS Elastic Beanstalk.
{{% /notice %}}
22. Once the deployment is complete
* Click **Environments**
* We will see the URL of TravelBuddy app
![Deploy to ElasticBeanstalk](/images/4-deploytoelasticbeanstalk/deploytoelasticbeanstalk-022.png?featherlight=false&width=90pc)