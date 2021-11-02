

# Day 4 - Create AMI from EC2

## Prerequisite

Complete Day 3 

## What is AMI?

AMI stands for Amazon Machine Image. It's a master image for the creation of virtual servers i.e., EC2 instances in the AWS environment.

AMIs are categorized according to region, operating system, system architecture (32 or 64 bit), launch permissions and whether they are backed by Amazon EBS or by the Instance Store.

AMI includes a template for the root volume required for an instance; typical example might contain an operating system, an application server and applications.

Any data on the instance store volumes persists as-long-as the instance is running i.e., the data gets deleted once the instance is terminated.

After the introduction of Amazon EBS, Amazon introduced AMIs that are backed by Amazon EBS i.e., the root device for an instance launched from the AMI is an Amazon EBS volume created from an EBS Snapshot.

Amazon recommends using EBS backed AMIs, because they launch faster and use persistent storage.


### Step 1 

Navigte to EC2 dashboard and select your instance created with the test.html page . Click on Actions. Under Image and templates, click on Create Image

![image](https://user-images.githubusercontent.com/82836111/139907460-2fc69473-99b2-4d90-a433-c4669fb79287.png)

Navigte to EC2 dashboard and select your instance. Click on Actions. Under Image and templates, click on Create Image


### Step 2

In the pop up window, enter a name for the image. Leave other details as default. Click on Create image.

After this AMI is availble, Now we can use this Image AMI to create brand new instances.

## Step 3

Select the AMI and press launch
![image](https://user-images.githubusercontent.com/82836111/139907822-a74bbf04-ad46-48c9-9bf1-c73662c4662f.png)

Choose an instance type. 
Configure Instance Details: 

Auto-assign Public IP: Select Enable

Launch without a key pair andN avigate to the instances menu and copy the IPv4 Public IP address of the created EC2 instance.
Enter the IP Address in the Browser.

It should show your test apache page and the /test.html page.

