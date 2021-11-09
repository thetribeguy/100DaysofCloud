## Day 8 - Accessing S3 with IAM roles
![image](https://user-images.githubusercontent.com/82836111/140813045-7f925c4f-894b-4898-ba8b-9450cb1f5d15.png)


## Introduction

IAM Policy
An IAM (Identity and access management)  policy is an entity in AWS, that enables you to manage access to AWS services and resources in a secure fashion.

Policies are stored on AWS in JSON format and are attached to resources as identity-based policies.

You can attach an IAM policy to different entities such as an IAM group, user, or role.

IAM policies gives us the power of restricting users or groups to only use the specific services that they need.

IAM Policy
An IAM (Identity and access management) policy is an entity in AWS, that enables you to manage access to AWS services and resources in a secure fashion.

Policies are stored on AWS in JSON format and are attached to resources as identity-based policies.

You can attach an IAM policy to different entities such as an IAM group, user, or role.

IAM policies gives us the power of restricting users or groups to only use the specific services that they need.


### Step 1 - Create a Role

Navigate to the IAM dashboard > roles > create a role.
For AWS Service, choose EC2 and S3fullaccess for permissions.
Enter tags and then create role.

### Step 2 - Connect to S3

SSH into the instance you created from Day 5.

Once logged in, switch to the root user: sudo su

Run the folowing command to find your S3 bucket via CLI: aws s3 ls

![Screen Shot 2021-11-09 at 10 39 25 AM (2)](https://user-images.githubusercontent.com/82836111/140955514-8101c548-f5de-4b2f-97fe-7c2c5cb95d4b.png)

You will see output similar to the image above, which shows that we are able to access the S3 bucket with the help of role attached to the EC2 instance.

Create a new text file and upload it to the bucket via AWS CLI (using the following set of commands):

touch test.txt (this creates text file)

aws s3 mv test.txt s3://<your_bucket_name> (this moves it to your s3 bucket)

Note : You need to enter your bucket name.

Check for the new file in the S3 bucket.

You can also list the files uploaded to S3 bucket via CLI from the EC2 instance with the following command:

aws s3 ls s3://<your_bucket_name>








