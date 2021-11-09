## Day 9 - Create a static website via S3
![image](https://user-images.githubusercontent.com/82836111/140965848-39185507-0910-47ea-a73a-9d55a0104289.png)


## Introduction
What is a Static Website?

These are the most basic types of websites and are the easiest to create. A static web page is a web page that is delivered to the user's web browser exactly as stored. It holds fixed content, where each page is coded in HTML and displays the same information to every visitor. No web programming or database design is required when working with them.


### Step 1 - Enable hosting
Using the bucket you created,
Click your S3 bucket name and navigate to the Properties tab at the top of the screen.

Scroll down to the Static website hosting and click Edit.

In the Static website hosting dialog box, choose the following options

Static website hosting : Select Enable

Hosting type : choose Host a static website

Index document    : Type index.html

Error document    : Type error.html

Click on Save changes.

![image](https://user-images.githubusercontent.com/82836111/140966223-78bc6f41-595d-4a1b-89be-9763aec9a558.png)

### Step 2 

Copy the Endpoint from properties > static website hosting to your clipboard and save it somewhere for later use. 

It will look similar to: http://bucketname.s3-website-us-east-1.amazonaws.com

Next, download the two example HTML files below and upload them to your s3 bucket.
Download index.html (https://play.whizlabs.com/site/download_file3?file=sample.html)
Download error.html (https://play.whizlabs.com/site/download_file4?file=error.html)

![image](https://user-images.githubusercontent.com/82836111/140966490-2788fae5-9acf-407a-8955-1d17a8b58ba0.png)

### Step 3

Click the Permissions tab to configure your bucket.

In the Permissions tab, Edit the Bucket Policy.

You will be able to see a Blank policy editor.

Before creating the policy, you will need to copy the ARN (Amazon Resource Name) of your bucket.

Copy the ARN of your bucket to the clipboard. It is displayed at the top of the policy editor. it looks like   ARN:“arn:aws:s3:::your-bucket-name".

In the policy below, update the bucket ARN on the Resource key value and copy the policy code.
{ 

   "Id":"Policy1",

   "Version":"2012-10-17",

   "Statement":[ 

      { 

         "Sid":"Stmt1",

         "Action":[ 

            "s3:GetObject"

         ],

         "Effect":"Allow",

         "Resource":"replace-this-string-with-your-bucket-arn/*",

         "Principal":"*"

      }

   ]

}

![image](https://user-images.githubusercontent.com/82836111/140966594-747ae571-baf5-49ed-abad-84f1ae5e7544.png)
Save changes.

Now copy the static website URL (that we saved earlier) and run it in your browser. You will be able to see the index.html file's text. 

![image](https://user-images.githubusercontent.com/82836111/140966729-dcdc579a-1c04-4ff7-aefe-02ac4805138e.png)

Copy the static website URL (which we saved earlier) , but this time, add some random characters to the end of the url to break it. When satisfied, hit enter. You will be redirected to the error.html page automatically.

![image](https://user-images.githubusercontent.com/82836111/140966712-60d29728-6628-4f0d-9e97-5a3fec076e24.png)








