+++
title = "Query the API use Eclipse IDE"
date = 2020
weight = 6
chapter = false
pre = "<b>6. </b>"
+++
#### Query the API use Eclipse IDE

You will use the Java SDK to inspect your AWS environment, and query for EC2 instance information. This gives you some experience in how you can make use of the AWS SDKs to manipulate resources in your AWS account directly, to create your own tooling, or control resource creation and management programmatically.

{{%attachments title="EC2Report File" style="orange" pattern="EC2Report.zip"/%}}

1. Download the source **EC2Report.zip** and extract. 
2. In the Eclipse IDE
* Click **File** 
* Click **Import**
![Update the application](/images/6-queryapi/queryapi-001.png?featherlight=false&width=90pc)
3. In the **Import** section
* Click **Maven**
* Click **Existing Maven Projects**
* Click **Next**
![Update the application](/images/6-queryapi/queryapi-002.png?featherlight=false&width=90pc)
4. In the **Import Maven Projects** section, select **Browse** 
* Choose the unzipped **EC2Report.zip** folder
* Click **Finish**
![Update the application](/images/6-queryapi/queryapi-003.png?featherlight=false&width=90pc)
5. In the Eclipse IDE, open the file **EC2Report/src/main/java/idevelop/samples/EC2Manager.java**
* Find **ReportEC2Environment()** method
* Change the region to your region you do this lab in.
* Save file.
![Update the application](/images/6-queryapi/queryapi-004.png?featherlight=false&width=90pc)
6. To run the app, right click on the application root in the IDE and click **Run As**
* Click **JUnit Test**
![Update the application](/images/6-queryapi/queryapi-005.png?featherlight=false&width=90pc)
7. This output shows a number of EC2 instances in the target account 
![Update the application](/images/6-queryapi/queryapi-006.png?featherlight=false&width=90pc)

#### Optional task
1. Explore the **pom.xml** file to ensure you understand how the dependency management works.
2. Try using the AWS EC2 Console to locate the same information that you are seeing in the output from the EC2Manager test suite. What other information is present in the AWS EC2 console that we are not showing in our test output? For example, review the **instance** object returned from the call to **describeInstancesRequest.getReservations()** in the debugger.
3. Update the output of the application to show the Tags associated with each EC2 instance. Then, in the AWS EC2 console, assign tags to the instances and see how they are reflected in the EC2Manager application output.
4. Programmatically create a new instance in your account. You will need to determine an ImageId, Keypair and security groups. Refer to  [the document](http://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/run-instance.html) as inspiration for how to code this up. If you want to action this, use the code below.
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