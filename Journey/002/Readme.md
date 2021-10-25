
# Day 2 - Create IAM users and groups

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


## Social Proof

✍️ Show that you shared your process on Twitter or LinkedIn

[link](link)
