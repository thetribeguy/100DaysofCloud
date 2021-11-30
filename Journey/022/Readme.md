# Install CloudWatch Logs Agent on EC2 Instance and View CloudWatch Metrics

![image](https://user-images.githubusercontent.com/82836111/143962761-8014da02-6f3a-4072-be81-8e3e8cfa4f7f.png)

### Step 1 - Download the CW agent

Create an IAM role with the CloudWatchAgentServerPolicy and attach it to an EC2. SSH into this instance.
View IAM roles, EC2, and SSH steps in week 1.

After you have SSH into your instance, run the following command to Download the Cloudwatch Unified Agent:
wget https://s3.amazonaws.com/amazoncloudwatch-agent/amazon_linux/amd64/latest/amazon-cloudwatch-agent.rpm
![image](https://user-images.githubusercontent.com/82836111/143962909-1b42ad48-06a8-4371-aa8f-e113c2aa7b26.png)


### Step 2 - Install the Cloudwatch Agent

use the following command:
sudo rpm -U ./amazon-cloudwatch-agent.rpm
![image](https://user-images.githubusercontent.com/82836111/143962980-45d109f6-997d-446d-a6ed-3ae44b586509.png)

### Step 3 - Configure the CW agent
Open the setup wizard using the command"
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
![image](https://user-images.githubusercontent.com/82836111/143963031-afec2a83-28fb-42c7-8193-2baa60fc8dfc.png)

Enter these values asked during setup:

On which OS are you planning to use the agent? : Enter 1

Are you using EC2 or On-Premises? : Enter 1

Which user are you planning to run the agent? : Enter 1

Do you want to turn on the StatsD daemon? : Enter 2

Do you want to monitor metrics from CollectD? : Enter 2

Do you want to monitor any host metrics? Enter 1

Do you want to monitor CPU metrics per core? Enter 1

Do you want to add ec2 dimensions into all of your metrics if the info is available? : Enter 1

Would you like to collect your metrics at high resolution? : Enter 1 (1s)

Which default metrics config do you want?: Enter 2

Are you satisfied with the above config? Enter 1

Do you have any existing CloudWatch log Agent configuration file to import for migration? : Enter 2

Do you want to monitor any log files? : Enter 2

Do you want to store the config in the SSM parameter store? : Enter 2

Start the Agent:

sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json -s
![image](https://user-images.githubusercontent.com/82836111/143963061-1adca843-28a4-48c0-865c-735fe3652e72.png)


Check Agent Status

systemctl status amazon-cloudwatch-agent
![image](https://user-images.githubusercontent.com/82836111/143963076-98a37902-765f-4c66-becb-407003a0f52f.png)



Navigate to Cloudwatch on the AWS console and in the Metrics section, the agent should be listed there with the metrics included.
