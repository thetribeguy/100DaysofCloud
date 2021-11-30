# AWS Access control alerts with CloudWatch and CloudTrail
![image](https://user-images.githubusercontent.com/82836111/144146438-b8b1c627-fd9d-4e1b-8be9-afb24957a0f2.png)


## Introduction
Cloudwatch
AWS Cloudwatch is the service that is used to monitor and collect the metrics from services periodically. This helps provide a clear picture for the users to understand how the resources are performing.

It collects data in the form of logs, events and metrics and provides you with an organized view of AWS resources, services and applications that run on AWS.

You can use CloudWatch to detect anomalous behavior in your environments and to set alarms, You can visualize data from the logs and take actions to troubleshoot the issue.

You can monitor AWS resources such as Amazon EC2, Amazon RDS, Amazon DynamoDB tables, and many others using CloudWatch.

You can monitor resource utilization in your account by setting up rules and events tto stop or terminate underutilized resources, reducing unnecessary cost.

In Autoscaling, servers are stopped or launched based on the events we create in CloudWatch.

CloudWatch also offers a feature to store logs for the services running in our account. For example, the logs for lambda functions will be stored within log groups in CloudWatch. Here we can get a detailed error log from any specific function.

CloudTrail
AWS CloudTrail is a service that helps us monitor, survey, and audit our AWS Account. 

With the help of AWS CloudTrail, the user will be able to log, monitor, and retain account activity associated with actions across the AWS infrastructure. 

CloudTrail provides complete account activity of the Amazon Web Services. CloudTrail also manages the functions performed with the help of the AWS Management Console, program line tools, AWS SDKs, and various other AWS services.


### Step 1 
Navigate to CloudTrail and click create trail
Under Create Trail, enter these details:

Trail name    : Enter My_cloudtrail
Storage Location   : Select Create a new S3 Bucket
Trail log bucket and folder  :  Leave it as default
Log file SSE-KMS encryption  :  Uncheck Enabled
Additional Settings:
Log file validation  : Uncheck Enabled
SNS notification delivery  :  Leave it as default
CloudWatch Logs  :  Check Enabled

![image](https://user-images.githubusercontent.com/82836111/144146589-0ae5cadc-99ee-447d-bfdc-70a1694b8d64.png)

Log group : Leave it as default (i.e New and default log group name)

IAM Role : Select New and give the Role name as whiz_role, default the rest of the settings and create trail.

### Step 2
Navigate to CloudWatch > Log Groups and click actions for the group you just created.
Under Create filter pattern, provide the pattern you need to filter on. For this lab, we are going to filter for stopped instances.

Filter pattern                 : Enter the pattern { $.eventName= "StopInstances" }

Select log data to test  : Select the cloudtrail log  in drop-down.
![image](https://user-images.githubusercontent.com/82836111/144146759-a8ca873a-3b75-4d7d-be86-4d5d43be68e5.png)

Next we will create a filter using the following details:

Filter name: Enter stoppedInstancecount

Metric details:

Metric namespace  : Enter CloudTrailMetrics

Metric name            : Enter EC2stoppedInstanceEventCount

Metric value            : Enter 1

Default value           : Leave default
Clik Next and create.

### Step 3
Select the log group and select metric filters at the bottom. select create alarm.
![image](https://user-images.githubusercontent.com/82836111/144146840-0f4cee80-e25c-4808-a8f1-676de300c483.png)

Specify the metric conditions as follows:

Namespace : CloudTrailMetrics (default)

Metric name : EC2stoppedInstanceEventCount (default)

Statistic        : sum (default)

Period          : 5 minute (default)

Conditions:

Threshold type: Select Static

Whenever EC2stoppedInstanceEventCount is : greater/equal than 1.

Next we'll configure actions

Alarm state trigger                                              : Select 

Select an SNS topic                                            : select Create new topic

Create a new topic                                              : Enter the topic name as My_Ec2count_topic

Email endpoints that will receive the notification :  Enter your Email address to receive the alert
Confirm in your email. Press Create alarm.

### Step 4
Stop one of your instances to test.
![image](https://user-images.githubusercontent.com/82836111/144146974-56d4f35b-bc5c-4b42-af08-f54cdfda742e.png)




### Step 2
