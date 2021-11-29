
# Encrypt an S3 bucket using AWS KMS and monitor the activities with CloudTrail

## Introduction

Amazon S3
A lot of companies today need the ability to simply and securely collect, store, and analyze their data at a massive scale. 

Amazon S3 is an object storage built to store and retrieve any amount of data from anywhere be it Websites, Mobile applications, Commercial applications, and data from IoT sensors or devices. 

It is designed to deliver 99.999999999% durability and stores data for millions of applications.

Amazon S3 provides comprehensive security with Server-Side Encryption, Customer-Side Encryption, Bucket policies and ACLs.

AWS Key Management Service (KMS)
AWS KMS is a managed service that makes it easy for us to create and control the encryption keys used to encrypt our data, and uses Hardware Security Modules (a hardware used for encryption keys) to protect the security of our keys.

AWS KMS is integrated with several other AWS services to help us protect the data we store while working with these services. 

AWS KMS is also integrated with AWS CloudTrail to provide us with the logs of all key usage to help us meet our regulatory and compliance needs.

AWS CloudTrail
AWS CloudTrail is a service that enables governance, compliance, operational auditing, and risk auditing of your AWS account. 

With CloudTrail, we can log, continuously monitor, and retain account activity related to actions across your AWS infrastructure. 

CloudTrail provides a history of all events and API calls made within our AWS account, including actions taken through the AWS Management Console, AWS SDKs, command line tools, and other AWS services. 

This event history helps us with security analysis, resource change tracking, and troubleshooting.

Whenever a service or resource has been deleted accidentally, the first place we go and look at is AWS CloudTrail.

![image](https://user-images.githubusercontent.com/82836111/143958901-8faf28fe-1d7e-4ed7-a52d-525ff75e5dab.png)



### Step 1 — Create a customer managed KMS key

Navigate to KMS and press "create a key"

Under configure key:
Key type : Select Symmetric

Click on Next

Under Add labels:

Alias : Enter whiz-kms-key

Description : Enter KMS key to encrypt S3 Objects

Click on Next

Under Define key administrative permissions:

Key administrators : Select the role that is associated with the account you are working with.

Next

Define Key usage permissions : Select the role that is associated with the account you are working with.

Review and Finish

### Step 2 

Navigate to CloudTrail  by clicking on Services in the AWS Management Console, and selecting CloudTrail under Management & Governance section.

Click on the menu section (three lines) on the left side panel and click on Trails.

Click on Create Trail button.

Under General details:

Trail name : Enter whiz-kms-trail

Storage location : Choose Use existing S3 bucket

Trail log bucket name : Click on Browse and choose the S3 bucket that you have created earlier(i.e whizlabs-cloudtrail-kms)

Log file SSE-KMS encryption : Uncheck Enabled

![image](https://user-images.githubusercontent.com/82836111/143959840-aca833b6-a0d6-46f4-887a-d3d4e5cb94a0.png)

Leave the rest as default and click on Next.

Choose log events:

Event type : Check both Management events and Data events.

![image](https://user-images.githubusercontent.com/82836111/143959875-f680eb80-bd2b-4ad3-ae84-3468529525dd.png)
![image](https://user-images.githubusercontent.com/82836111/143959887-f054876e-5472-4e62-aecc-672df69c685f.png)

All current and future S3 buckets : Uncheck both Read and Write

Individual bucket selection : Click on Browse and choose the S3 bucket that we have created earlier(i.e whizlabs-cloudtrail-kms)

Make sure you have checked both Read and Write next to the Browse.

![image](https://user-images.githubusercontent.com/82836111/143959912-64d7e78d-52d3-41ab-b064-d3f9088effaf.png)

Click on Next

Review everything and click on Create Trail button.

You have successfully created a CloudTrail and can find yours under Trails.

![image](https://user-images.githubusercontent.com/82836111/143959941-1de74225-3a9e-4ee7-8218-4bbe0264b614.png)

### Step 3

Navigate to an S3 bucket 
Click on the Upload button.

Click on Add files and choose a picture from your local PC.

Scroll down to Properties and click on it to expand.

Scroll down to Server-side encryption settings:

Server-side encryption : Select Specify an encryption key

Encryption key type : Select AWS Key Management Service key(SSE-KMS)

AWS KMS key : Select Choose from your AWS KMS keys and from the drop-down menu select the KMS key we have created i.e whiz-kms-key

Click on the Upload button.

Click on close and you will see your uploaded picture under the objects section.

Note the Last Modified time in the notepad.

### Step 4

Click on the picture you have uploaded and click on Open on the top right side of your screen.
![image](https://user-images.githubusercontent.com/82836111/143960069-14390f4d-edf5-4755-8af7-467aec8ca657.png)

The picture opens in a new tab/window.

What happens behind the scenes?

Amazon S3 sends the encrypted data key to AWS KMS.

AWS KMS decrypts the key by using the appropriate master key and sends the plaintext key back to Amazon S3.

Amazon S3 decrypts the cipher text and removes the plaintext data key from memory as soon as possible.

Close the tab/window that displayed your picture.

Now copy the Object URL and paste it into a new tab of your browser and hit Enter. [In my case : https://whizlabs-cloudtrail-kms.s3.amazonaws.com/Sharingan.png]

You will see a page with the message “Access denied.” And that is because by default, the public access is blocked.
![image](https://user-images.githubusercontent.com/82836111/143960085-02a88284-37f9-4d67-aff3-5fc40a038ec2.png)

Go back to the bucket, click on the Permissions section.
![image](https://user-images.githubusercontent.com/82836111/143960123-d145b430-5894-472d-a50f-6db7fd692eb4.png)

Under Block public access, click on Edit and uncheck Block all public access and click on Save changes.

In the next screen, Type confirm and click on Confirm button.

You have successfully edited Block Public Access settings.

Now go to the Objects tab and click on your object.

On the top right corner, select Make public from the Object actions drop-down menu and click on Make public again.

Click on close.

Now refresh the tab where you have pasted the Object URL earlier.

You should see a message something like this:
![image](https://user-images.githubusercontent.com/82836111/143960143-a327b61e-6db8-41e2-ab1e-f9d74e4455f3.png)

This is because the picture is encrypted and you are not able to view it using the public link. If you are uploading or accessing objects encrypted by SSE-KMS, you need to use AWS Signature Version 4 for added security.

### Step 5

Go back to your S3 bucket and you will be able to find one more object with the name AWSLogs/.
![image](https://user-images.githubusercontent.com/82836111/143960205-484485ad-b3c0-4bd9-80a7-6ff59a841389.png)

Click on it and click on the next directory too representing your account number.

Now click on the CloudTrail/ directory and click on us-east-1/.

In case if you do not see any objects under CloudTrail/, please wait for 5 minutes and refresh the objects.

Now click on the <year>, <month> and <date> one after the other.

You will be able to see CloudTrail logs.
  ![image](https://user-images.githubusercontent.com/82836111/143960223-d8897a8f-004a-4a6b-8233-5d05ae62464c.png)
Click on the log file whose Last modified time is greater than the timestamp of the picture when it is uploaded.(Refer your notepad)

If there is no log file whose Last modified time is greater than the timestamp of the picture when it is uploaded, wait for 5 more minutes.

Click on the latest log file from the list.

Click on Open.

Press Ctrl+F and search for the Key Id you have saved in the notepad and the picture name you have created.

If you are unable to find them, copy the object URL of the picture you have uploaded again and paste it in the browser and note down the time.

Wait for some time and now search for the logs whose time is greater than that of what you just noted down.

Now you will be able to find the Key ID in the log record.






