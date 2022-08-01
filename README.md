##Check for Bucket Size more than 1GB and send out Email on Monthly Basis

#Introduction
Amazon S3 is object storage built to store and retrieve any amount of data from anywhere. It’s a simple storage service that offers industry leading durability, availability, performance,
security, and virtually unlimited scalability at very low costs.
In this Article, we will go through how we can receive email notifications for S3 Buckets whose size has reached 1GB or more.
Individual Amazon S3 objects can range in size from a minimum of 0 bytes to a maximum of 5 TB. The largest object that can be uploaded in a single PUT is 5GB.
Just for the User to know if 1GB of S3 Bucket is utilized so they can clean-up with older data. Because all objects in your S3 bucket incur storage costs, you should delete objects that you no longer need.

The following are the steps to follow to set Email Notifications:
1. Create a Lambda function, where you will check for all the S3 and send mail every month if it reaches 1GB.
2. Create an SNS Topic which will be called by the Lambda function.

## Step-by-Step Explanation:
1. Create a Lambda function:
      * Open Lambda Console, Create Function
      * Enter the function Name, Select Python 3.9, create a IAM role with following policies and attach the same to the Lambda function. S3FullAccess and SNSFullAccess.
      * Click on Create Function, will redirect to the Function page with Basic Lambda Code, copy the below Lambda code and paste it in the console
      * This is the Lambda function which will call the SNS.
      * [Refer this file](https://github.com/KAJOLMEHTAA/AWS_S3_Bucket/tree/main/s3_bucket.py)

2. SNS Topic:
      * Open SNS Topic Console, Create Topic
      * Under the Topic Create Subscription, Protocol as Email and Specify the Email ID where you want to receive notification for Instance expiration, in Endpoint.
