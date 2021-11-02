

# Day 3 - Create and Publish a web page via EC2

## Prerequisite

Complete Day 2 - Launcing EC2

### Step 1 — Create a VPC

Go through steps of launcing EC2 or make a new one. (Day 2)

### Step 2 - Install an Apache Server

Switch to root user: sudo su

Now run the updates using the following command: yum -y update

Install the Apache web server: yum install httpd

When prompted, press "Y" to confirm.

Start the web server: systemctl start httpd

Now enable httpd: systemctl enable httpd

Check the web server status: systemctl status httpd

You can see the active status is running.

You can test that your web server is properly installed and started by entering the public IPv4 address of your EC2 instance in the address bar of a web browser. If your web server is running, then you see the Apache test page. If you don't see the Apache test page, then verify whether you followed the above steps properly and check your inbound rules for the security group that you created.

Make sure the URL Protocol is http not https.

![Screen Shot 2021-11-02 at 11 49 23 AM (2)](https://user-images.githubusercontent.com/82836111/139900878-138d6fa0-7d36-45c4-9b2a-3c6dbc25956d.png)


### Step 3 - Create and publish web page

After installing apache server, navigate to the html folder where we will put our html page to be published. Use command: cd /var/www/html/

Create a sample test.html file using nano editor: nano test.html

Enter sample HTML content provided below in the file and save the file with Ctrl+X. Click Y to confirm the save, then press Enter to confirm filename.

<HTML> Hi its Ayo's page </HTML>

Restart the web server by using the following command:  systemctl restart httpd

Now enter the file name, i.e., /test.html after the public IPv4 Address which you got when you created the ec2 instance in the browser, and you can see your HTML content.

Make sure URL Protocol is http not https.

Sample URL: 52.90.56.138/test.html

![Screen Shot 2021-11-02 at 12 10 42 PM (2)](https://user-images.githubusercontent.com/82836111/139898841-449f0676-3631-4d65-bb41-a86521bded3a.png)


