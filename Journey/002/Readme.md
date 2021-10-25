
# Day 2 - Create IAM users, groups, roles, and policy

## Introduction

What is IAM?
Stands for Identity and Access Management.

Web service that helps the user securely control access to AWS resources.

Used to control who is authenticated and authorized to use AWS resources.

The primary resources in IAM are users, groups, roles, policies, and identity providers.

IAM Group is a collection of IAM Users. You use groups to specify permissions for a collection of users, which can make those permissions easier to manage for those users.

IAM roles are like IAM Users in that they are both identities with permission policies that determine what the owner can access.

IAM can be used from the AWS CLI, AWS SDK and AWS Management Console.

![image](https://user-images.githubusercontent.com/82836111/138775539-57400b41-3a31-4efa-a1b4-ea1c698acbfa.png)


### Step 1 — Create IAM user

Click on "Services" and search/select "IAM" 

Select "Users" in the left panel and click on the "Add User" to create a new IAM user.

### Step 2

In the Set user details Section, 

User name: Enter *name of your choice*

Click on "add another user" and provide the name, *of your choice*

### Step 3 

In Select AWS access type section,

Access key - Programmatic access: Uncheck

PAssword - AWS Management Console access: Check

Console password: 

Auto Generated password : Uncheck

Check Custom password and Enter *Password of your choice*

Require password reset: Uncheck

Click on Next: Permissions
![image](https://user-images.githubusercontent.com/82836111/138776144-c2da7d6b-d422-4fe8-a0c9-61e93844bbee.png)

No need to anything here. Click on Next: Tags

### Step 4
In Add Tags page:

This is an optional step, but really helpful to search, manage and filter the resources. Provide the below details

Key: Enter Dev-Team

Value: Enter Developers

Click on Next:Review 

Review the details and click on the Create users.

![image](https://user-images.githubusercontent.com/82836111/138776217-80a7976c-5fca-40f2-9e43-854670712485.png)

Note: Ignore the above error if it appears while creating Users and click Close.

Repeat the steps to create IAM users by name Ted, Rita with following details,

Custom password: Enter *your choice*

Key: Enter HR-Team

Value: Enter HR

### Step 5 - Create User Group
Select the User groups in the left panel and click on the Create group.

Set Group Name:
User group name: Enter Dev-Team

Scroll down and select your two IAM names under Add Users to the group.

Scroll down to Attach permissions Policies section and,

Search for AmazonEC2ReadOnlyAccess in the search box and select the policy AmazonEC2ReadOnlyAccess.

Search for AmazonS3ReadOnlyAccess in the search box and select the policy AmazonS3ReadOnlyAccess.

Review all details and click on Create group.

### Step 6 - Create Roles
In the IAM dashboard, on the left side, select Roles.
Click on Create role.
For Select type of trusted entity, choose EC2. Then click Next: Permissions
![image](https://user-images.githubusercontent.com/82836111/138777478-519d06c0-db02-47a0-a187-75b3e151365b.png)

In Attach permissions policies, type EC2 in the Filter Policies and select AmazonEC2FullAccess
![image](https://user-images.githubusercontent.com/82836111/138777530-dabe4e5b-383d-4785-b84e-be936ba88644.png)

Click Next: tags (optional), then next: review.
Enter a role name, and choose create role.

Note:

When you set up an AWS service environment, you must define a role for the service to assume. You can attach this Role to the AWS services. This service role must include all the permissions required for the service to access the AWS resources that it needs.

This allows EC2 to perform actions on our behalf.

### Step 7 - Create Policies

In the IAM menu, select policies.
Click on Create policy.

Under Visual Editor, select choose a service. 

Type EC2 in the search box and select EC2.
![image](https://user-images.githubusercontent.com/82836111/138778409-92ecd289-7e18-47d4-85ba-fb90cdbeb841.png)

In the Actions, specify the actions allowed in EC2. For this service, We'll choose List and Read.
![image](https://user-images.githubusercontent.com/82836111/138778441-20abfe7f-1699-4be9-8853-bf695b510d3e.png)

Click on Resources, scroll down and choose All resources so that there is no need to specify the resource ARN.
Now scroll up and If you click on the JSON, you can see the policy we created.

Click on Next: Tags. No changes needed.

Click on Next: Review.

Review:

Name : Enter EC2Policy

Description : Enter EC2 Full Read and List access

In the Summary, you can see the Access level.

Review the policy and then click on Create policy.
![image](https://user-images.githubusercontent.com/82836111/138778510-e6de8878-57b9-41ea-874f-e819c1862522.png)



## Social Proof

✍️ Show that you shared your process on Twitter or LinkedIn

[link](link)
