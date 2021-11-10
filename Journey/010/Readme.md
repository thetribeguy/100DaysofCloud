## Day 10 - Creating and Subscribing to SNS Topics, Adding SNS event for S3 bucket


## Introduction
What is SNS?

SNS stands for Simple Notification Service. Provides a low-cost infrastructure for the mass delivery of messages, predominantly to mobile users.
SNS acts as a single message bus that can message to a variety of devices and platforms. SNS uses the publish/subscribe model for push delivery of messages.

![image](https://user-images.githubusercontent.com/82836111/140993237-63b3ff85-d4f8-4b6c-8525-d70ddd609412.png)

## Step 1 - Create SNS Topic

Navigate to SNS dashboard, click create topic.

Select the Type as Standard. 

Under Details:

Name : Enter mysnsnotification

Display name : Enter mysnsnotification

![image](https://user-images.githubusercontent.com/82836111/141161608-46df1312-20dd-4dca-9782-1fbe9929f10b.png)

Press create topic

![image](https://user-images.githubusercontent.com/82836111/141161675-78ca17b2-54f2-44b0-b8f9-a0ac3a9ec878.png)

Copy this ARN.

## Step 2 - Subscribe to SNS topic
Once the SNS topic is created, scroll down below and click on create subscription.
Under Details: 

Protocol : Select Email

Endpoint : Enter  <your Mail Id>

Note: Make sure you give a valid email address as you will receive an SNS notification to this email address.

Check your Spam box if you don't see the email in your Inbox.

You will receive an email confirming your subscription to your email.
  
  ![image](https://user-images.githubusercontent.com/82836111/141161835-3d2ece2b-5a9e-4ccf-ba02-df7c62a80530.png)

  Click on confirm.
  
Go to your S3 bucket of choice and copy it ARN as well.

## Step 3 - Update SNS Topic Access Policy
  
Navigate back to the SNS page.

Click on Topics. Click on mysnsnotification. Click on Edit at the top right corner to edit the Access Policy of the SNS topic.

Expand Access Policy and Update the bucket policy as shown below:

SNS Topic ARN in the Resources section below

S3 bucket ARN in the Condition section below

{
  "Version": "2008-10-17",
  "Id": "__default_policy_ID",
  "Statement": [
    {
      "Sid": "__default_statement_ID",
      "Effect": "Allow",
      "Principal": {
        "AWS": "*"
      },
      "Action": [
        "SNS:GetTopicAttributes",
        "SNS:SetTopicAttributes",
        "SNS:AddPermission",
        "SNS:RemovePermission",
        "SNS:DeleteTopic",
        "SNS:Subscribe",
        "SNS:ListSubscriptionsByTopic",
        "SNS:Publish",
        "SNS:Receive"
      ],
      "Resource": "YOUR SNS TOPIC ARN",
      "Condition": {
        "ArnLike": {
          "aws:SourceArn": "YOUR BUCKET ARN"
        }
      }
    }
  ]
}
  
  Save.


## Step 4 - Create S3 Event
  
Navigate back to the S3 page.

Click on the S3 bucket that you have created in the above step.

Go to the Properties tab and scroll down to Event notifications.

Click on Create event notification.

Event name  : Enter myemaileventforput.

Event types : Check PUT
  
  ![image](https://user-images.githubusercontent.com/82836111/141162342-fbb4f0cf-cb24-4e0f-81b7-07541677d99f.png)
  
  Under Destination select SNS Topic 

Under SNS topic select topic name created earlier.

Click on Save changes.
  
  ![image](https://user-images.githubusercontent.com/82836111/141162399-9b65586d-3c9e-4040-84c8-1f0fdceef8e3.png)

## Step 5 - Testing the SNS Notification
  
  Open your bucket and upload a file. You should receive an email notification
  ![image](https://user-images.githubusercontent.com/82836111/141162554-83caada1-334a-4495-acd3-17286273a00d.png)





