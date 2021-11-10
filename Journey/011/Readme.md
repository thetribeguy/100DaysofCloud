## Day 11 - Build Amazon VPC with Public and Private Subnets (from Scratch)


## Introduction

What is VPC?
VPC stands for Virtual Private Cloud. It’s a custom-defined virtual network within the AWS Cloud. Users can logically create their personal network, designing and implementing a separate and independent network that would operate in the AWS Cloud. Primary components are : Subnets, IP addresses, NAT Devices (Instances & Gateways), Route Tables, Internet & Virtual Private Gateways, Access Control Lists, Security groups, VPC Endpoints. A subnet is a segment of the VPC IP address range, where we can launch EC2 Instances, RDS, and other AWS resources.

![image](https://user-images.githubusercontent.com/82836111/141201126-e45c56ac-5acc-4700-ad4e-a3dbac3cb391.png)


##
### Step 1 - Creating New VPC

Navigate to VPC dashboard and click create VPC.

Name tag: Enter a VPC name for identification to your VPC. Ex: MyVPC

IPv4 CIDR block: Enter 10.0.0.0/16

IPv6 CIDR block: No need to change this, make sure No IPv6 CIDR Block is checked.

Tenancy: No need to change this, make sure Default is selected.
Click create VPC

![image](https://user-images.githubusercontent.com/82836111/141201290-ff0b60ad-003c-4b39-9309-05b05aa89ab7.png)

##
### Step 2 - Creating Subnets

For the Public Subnet, click on Subnets from the left menu and click on Create subnet.

VPC ID : Select MyVPC from the list you created earlier.

Subnet Name   : Enter Name MyPublicSubnet

Availability Zone  : Select us-east-1a

IPv4 CIDR block  : Enter the range 10.0.1.0/24

Click on Create subnet.

For the Private Subnet, click on Create subnet again.  

VPC ID : Select MyVPC from the list you created earlier.

Subnet Name   : Enter Name MyPrivateSubnet

Availability Zone  : Select us-east-1b

IPv4 CIDR block  : Enter the range 10.0.2.0/24

Click on Create subnet.

![Untitled](https://user-images.githubusercontent.com/82836111/141201528-a5430b0d-3c60-4fe3-82f4-25f9f1661e44.jpg)

##
### Step 3 - Create and configure Internet Gateway

Click on Internet Gateways from the left menu and click .

Name Tag : Enter MyIGW

![image](https://user-images.githubusercontent.com/82836111/141201684-5663a90a-9ebe-44a5-8355-735bac630987.png)
Select the Internet gateway you created from the list

Click on Actions > Attach to VPC.

Select MyVPC which you created from the list and click on Attach internet gateway.

##
### Step 4 - Create Route Tables

Go to Route Tables from the left menu and click on Create route table.

Name Tag: Enter PublicRouteTable.

VPC: Select MyVPC from the list.

Click on Create route table.

Repeat the same steps to create a route table for the Private subnet.

Name Tag: Enter PrivateRouteTable.

VPC: Select MyVPC from the list.

Click on Create route table.

![image](https://user-images.githubusercontent.com/82836111/141201869-9c66b041-83a2-43fd-a668-45a02d97c738.png)

Click on one PublicRouteTable and go to the Subnet Associations tab.

Click on Edt and Select MyPublicSubnet from the list. Click on Save associations.

Click on one PrivateRouteTable and go to the Subnet Associations tab.

Click on edit and Select MyPrivateSubnet from the list. Click on Save associations.

##
### Step 5 - Add a route to allow Internet traffic to the VPC.

Select PublicRouteTable.

Go to Routes tab, click on https://play.whizlabs.com/frontend/web/media/2019/07/10/lab7_task_14_edit_routes_button.png and on the next page, click on .

Specify the following values: 

Destination: Enter 0.0.0.0/0

Target: Select Internet Gateway from the dropdown menu to select MyInternetGateway.

Click on Save changes.

You have successfully completed and learned how to create public and private subnets.

You have learned how to create an Internet Gateway and associate it to VPC.

You now understand how public and private subnets are different (through associating Internet Gateway or not).

The instances launched inside the public subnet will be able to access the internet and instances launched inside the private subnet will not have access to the internet.

