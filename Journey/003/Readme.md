

# Day 2 - Launching EC2 Machine and Connecting through Browser-Based SSH

## Introduction

![image](https://user-images.githubusercontent.com/82836111/139876923-b148f003-c9b6-472d-808d-7082a8d54e26.png)

### Step 1 — Create a VPC

Navigate to "VPC" dashboard, and create a VPC with the default settings.

### Step 2

Navigate to "EC2" dashboard
Click on Instances in the left side panel and click on  Launch Instance.

Search and Choose Amazon Linux 2 AMI: ![image](https://user-images.githubusercontent.com/82836111/139877494-7f8ea5ed-c229-48fb-80d9-f56243bf96b0.png)


### Step 3 

Choose an Instance Type:tmicro (or any free tier) and then click on next.
Associate this Instance with the VPC you just created.
Click on Next: Add Storage
Add Storage: No need to change anything in this step. Click on Next: Add Tags
Add tags if neccesary 

Click on Next: Configure Security Group

### Step 4
Assign a security group: Check ( Create a new security group )

Security group name: *your choice*

Description: Enter a description of Security group 

To add SSH:
Source: Custom (Allow specific IP address) or Anywhere (From ALL IP addresses accessible).

### Step 5 - Launch
After that, click on Review and Launch

Key Pair : Since we are using Browser-based SSH, we do not need a key pair. Select Proceed without a key pair, check the acknowledgement and click on Launch Instances.

Review and Launch : Review all settings and click on Launch. You instance should be running shortly.

### Step 6 - Connect instance
By using EC2 Instance Connect, we can directly connect to our instance from the console.

Select your instance.

Click on Connect.

You will see 4 types of Connection methods. Choose EC2 Instance Connect (browser-based SSH connection) and click on Connect.
Your Instance will be connected to SSH through your Browser.

### Step 7 - Try commands

Switch to root user: sudo -s

Run updates using the following command: 

yum -y update

To find your current working directory, enter the command pwd

Enter the exit command to go back to ec2-user then again exit to log out.

In this way, you can connect to your instance using SSH from your console without using a key pair.



## Social Proof

✍️ Show that you shared your process on Twitter or LinkedIn

[link](link)
