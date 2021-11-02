## Day 6 - Creating Cloudwatch Dashboard for EC2
![image](https://user-images.githubusercontent.com/82836111/139921479-34024d99-c033-4bbd-a0f8-e50bc21f2746.png)


## Prerequisite

Complete Days 1-5

### Step 1 

Navigate to Cloudwatch and click Dashboards.
Click on create dashboard and enter a name.


### Step 2
On the next page, select line widget
![image](https://user-images.githubusercontent.com/82836111/139922487-39de5565-50d2-46b1-ab7e-c747c857ff19.png)

Select metrics
You will see a metric graph. Under All metrics, search and choose EC2 (since we are going to watch the metrics of EC2 which we created earlier).

Under EC2, choose Per-Instance Metrics and select any of your Instace Ids and press create widget.
![image](https://user-images.githubusercontent.com/82836111/139922646-b5f7f11d-e3c3-4b9f-b8bd-7be316ac24a7.png)

You have created a custom dashboard.





