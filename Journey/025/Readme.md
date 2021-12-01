# Finding vulnerabilities on EC2 instance using Amazon Inspector

What is Amazon Inspector
Amazon Inspector allows us to find vulnerabilities on configured EC2 instances.

There are 2 types of assessment runs are performed, Network assessment and Host assessment

Network assessment has Network Reachability package rule while Host assessment has three types of package rule i.e. Common vulnerabilities and exposures, Center for Internet Security (CIS) Benchmarks, Security best practices for Amazon Inspector.

There are mainly three types of Severity levels for rules in Amazon Inspector i.e. High, Medium, and Low.

Informational severity of findings is just best practices recommended by Amazon Inspector. 
![image](https://user-images.githubusercontent.com/82836111/144154237-6751a9e1-7335-434d-80ca-f3733a69562a.png)


### Step 1 

Launch a default instance with the following security group setting:
Configure Security Group:

Security group name: Inspector-SG
Description: Security group for Inspector EC2
To add All traffic,
Choose Type: SSH
Source: Custom (Allow specific IP address) or Anywhere (From ALL IP addresses accessible).

Another rule:
Choose type: Custom TCP Rule
Port Range: 20
Source: Custom and 0.0.0.0/0

Another rule:
Choose type: Custom TCP Rule
Port Range: 21
Source: Custom and 0.0.0.0/0


Choose type: Custom TCP Rule
Port Range: 23
Source: Custom and 0.0.0.0/0
Launch

### Step 2
SSH into the instance and install the AWS Agent
Download the agent installation script by running one of the following commands:

wget https://inspector-agent.amazonaws.com/linux/latest/install

curl -O https://inspector-agent.amazonaws.com/linux/latest/install

To install the agent, run the following command:

sudo bash install

### Step 3
Navigate to inspector (classic version)
Click on the Cancel button present on the right bottom corner, to see the options. Run weekly, Run once and Advanced setup is for quick setup.
![image](https://user-images.githubusercontent.com/82836111/144154616-a918cb5b-aa7a-47da-ad30-872de46bda69.png)
On the Leftside bar, click on the Assessment targets.

Click on the Create button.

Fill in the details, Name: Demo

All instances: Select Include all EC2 instances in this AWS account and region.

Install Agents: Selected by Default

Click on the Save button, to create an Assessment Target.
![image](https://user-images.githubusercontent.com/82836111/144154640-9e3d856d-2c0a-4f41-bf75-2edec379c06f.png)
and press OK on the popup.

### Step 4
Click Assessment template and create.
![image](https://user-images.githubusercontent.com/82836111/144154694-de324571-2481-44c8-b1f4-6b5b33c0494f.png)
![image](https://user-images.githubusercontent.com/82836111/144154709-624fdfb6-3086-4f32-9493-08f6fdf6da51.png)

It's created, in the next step. You will run the template to find the vulnerabilities on the created EC2 instance.
![image](https://user-images.githubusercontent.com/82836111/144154753-70910ab0-72a5-4a8a-b12d-6dc7c7379b64.png)

### Step 5
Select the template and click Run
To see the Assessment Run and its result, click on the Assessment runs present on the left sidebar.

Click on the number of findings to know about the vulnerabilities found by Inspector on the EC2 instance.
![image](https://user-images.githubusercontent.com/82836111/144154793-ebb0049b-7a3d-45a7-b3cd-2d535ba1a642.png)
![image](https://user-images.githubusercontent.com/82836111/144154800-a1587a32-1afb-44cb-9e7a-65f717730782.png)

### Step 6
Click on the Assessment runs, present on the left sidebar.

Choose the Download report button. 
![image](https://user-images.githubusercontent.com/82836111/144154838-98443ba6-6b25-4b88-ade6-fb1691b7f65a.png)
After you click on the Download report option, you will be prompted with a screen to select the report type and format.

Keep the option default, Report type as Findings report, and report format as PDF. Click on the Generate Report button.






Install Agents: Selected by Default
