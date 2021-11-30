# Access EC2 from Session manager and send SSH logs to CloudWatch


## Introduction

What is a Session Manager ?
Session Manager is a fully managed AWS Systems Manager capability that lets you manage your Amazon Elastic Compute Cloud (Amazon EC2) instances, on-premises instances, and virtual machines (VMs) through an interactive one-click browser-based shell or through the AWS Command Line Interface (AWS CLI).
Session Manager provides secure and auditable instance management without the need to open inbound ports, maintain bastion hosts, or manage SSH keys.

Session Manager also makes it easy to comply with corporate policies that require controlled access to instances, strict security practices, and fully auditable logs with instance access details, while still providing end users with simple one-click cross-platform access to your managed instances.

![image](https://user-images.githubusercontent.com/82836111/144142717-ae24f36f-f938-45a6-8951-1c841a45ab71.png)

### Step 1 
Create a role with SSM full access permission policy. See week 1 to create roles.
Navigate to Cloudwatch and create a log group to capture the logs
![image](https://user-images.githubusercontent.com/82836111/144142920-db03c3d8-2a56-4032-8bc0-5df8131f5e8d.png)

### Step 2
Launch or Modify an instance (without a keypair) to attach the SSM role.
Ensure the security group only allows HTTP from anywhere. 
![image](https://user-images.githubusercontent.com/82836111/144143004-8b93edb2-a433-4b19-9876-6ee858bd1078.png)

### Step 3
Navigate to Systems Manager > Sessions Manager and cick configure preferences.
Settings:
![image](https://user-images.githubusercontent.com/82836111/144143128-04d488e4-8b19-4da7-8e25-0feee7af2dab.png)

### Step 4
Start a session in Sessions manager and enter some commands. Terminate the session and click Session history to access the Cloudwatch Logs.
![image](https://user-images.githubusercontent.com/82836111/144143205-d4bbd07b-ed6b-468d-ac34-cf926af23699.png)


