## Day 7 - Configuring S3
![image](https://user-images.githubusercontent.com/82836111/140799029-e4fb5cdf-6f8d-4282-b7e4-1b052df99a01.png)


## Introduction

S3 stands for Simple Storage Service. It provides object storage through a web service interface. Each object is stored as a file with its metadata included and is given an ID number. Objects uploaded to S3 are stored in containers called Buckets, whose names are unique and they organize the Amazon S3 namespace at the highest level. 


### Step 1 - Create a bucket

From the AWS console main page, search and navigate to S3.
In the right menu, click create bucket
Bucket settings for Block Public Access: Uncheck the option, Block all public access and select the check box option of Acknowledgment.
Leave all settings as default and press create.

### Step 2 - Upload an object
Click on your bucket you just created.
Click on objects and press upload, and upload an image file.
![image](https://user-images.githubusercontent.com/82836111/140804009-52eccb45-9e45-4835-ab25-a33c16149232.png)

### Step 2 - Enable access

Under Objects, click on your file you uploaded. You will see the image details like Owner, size, link, etc.

A URL will be listed under Object URL:
![image](https://user-images.githubusercontent.com/82836111/140804676-8c58d9be-5b85-48fd-acb7-7abb8d360937.png)

You will see an AccessDenied message, which means the object is not publicly accessible.
![image](https://user-images.githubusercontent.com/82836111/140804709-13848956-7c8b-414e-931a-73644e2c8fb4.png)

Now go to the image page in the bucket and press the permissions tab. Scroll down to Access Control List
Click on the Edit button on the Right side of it.
Add read access to everyone and save changes.

Open image Object URL in a new tab or return to the browser tab that displayed Access Denied and refresh the page.

You can see your image is loaded successfully and publicly accessible now.

Now scroll a little bit below and check I understand the effects of these changes on this object. Checkbox.





