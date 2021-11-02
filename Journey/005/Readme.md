 Day 5 - Connecting EC2 through putty/terminal

## Prerequisite

Complete Days 1-4

### Step 1 

Create a new EC2 instance with the same settings as before but this time, on the last step of launching, create and download a key pair.

### Step 2

Open the terminal. (macbook)

Navigate to the location where your key pair is downloaded and stored on your local machine. For example, if the key.pem file you downloaded dring set up, is located on the desktop, in the terminal you would navigate to the desktop using: cd /desktop (CD = change directory). Run the pwd command to see which directory you are currently in.cd

To update Permissions, run the following command

chmod 400 keypair (Enter your key pair name)

SSH and connect to the EC2 Instance, enter the following command:

Syntax: ssh -i keypair ec2-user@publicIPAddress (enter the public address)

Sample: ssh -i keypair ec2-user@107.21.198.65

Up next, type yes and then hit enter. You will be successfully logged on to the EC2 Instance.
![Screen Shot 2021-11-02 at 1 29 29 PM (2)](https://user-images.githubusercontent.com/82836111/139915730-6c490d4c-720d-4b0d-8ce4-c47684e5b407.png)
