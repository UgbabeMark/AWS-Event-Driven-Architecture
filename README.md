  # AWS Event-Driven Architecture

  __Project: Event-Driven Architecture with S3, SNS, SQS and Lambda on AWS__

**Overview**

This project showcases an implementation of an **event-driven architecture (EDA) on AWS.** 

This approach fosters scalability, loose coupling, and fault tolerance by leveraging asynchronous communication between services.


# Overview of Resources Utilized

**Amazon S3 Bucket:** An S3 bucket is created to store objects and trigger events based on object uploads.

**Amazon SNS Topic:** An SNS (Simple Notification Service) topic is created to publish messages and notify subscribed endpoints or other AWS services.

**Amazon SQS Queues:** SQS (Simple Queue Service) queues are created to store messages and decouple the components of the system.

**Lambda Functions:** Lambda functions are created to process events triggered by S3 uploads or messages sent to SQS queues.

**IAM Permissions:** IAM (Identity and Access Management) permissions are configured to grant appropriate access to the necessary AWS resources    for the Lambda functions and other components.

# step-by-step instructions for setting up the event-driven architecture on AWS:

# 1. Set Up Amazon S3 Bucket:

  Create an Amazon S3 bucket.

  Keep all Settings Default.

  ![Enrollment](Images/S3bucket.png)
  
  ![Enrollment](Images/s3bucket1.png)

# S3 Event Notification Configureation

  Select s3 bucket, go to properties and choose event notification.

  Create event Notification.

  Enter event Name and choose Event Type.

  ![Enrollment](Images/S3event.png)

  Select destination (snsTopic) and chosse from your sns Topic.
  
  # ![Enrollment](Images/s3eventt.png)


# 2. Create an Amazon SNS Topic:
 
  Create an Amazon SNS topic.

  ![Enrollment](Images/snsTopic.png)

  # SNS configuration

  **SNS Access Policy**

  Edit Policy with provided sns access policy and save changes.
  
  ![Enrollment](Images/snsaccess.png)

  **SNS Subscription**
  
  Create subscription For Queue1
  
  ![Enrollment](Images/topic1.png)

  Create subscription For Queue2
  
  ![Enrollment](Images/topic2.png)

 # ![Enrollment](Images/subscr.png)

  
# 3. Create Amazon SQS Queues:

   Create two Amazon SQS queues.

  ![Enrollment](Images/sqs.png)  
 
   Kepp all settings default and create Topic. Reemeber to do this on the second Topic.
 
 # ![Enrollment](Images/sqs1.png)

 **SQS Access Policy**

 ![Enrollment](Images/SQS.png)

 Repeat Thesame proceedure as for SNS and replace all itemin < >. and save Changes.

# Configure Lambda Function Trigger

Lambda Trigger is created for Queue1 and Queue2


![Enrollment](Images/tri1.png)

Select the function that matches with queue 1

![Enrollment](Images/tri2.png)

Select the function that matches with queue 2
![Enrollment](Images/tri3.png)

lambda trigger for queue 1 Enabled 

![Enrollment](Images/tri4.png)

lambda trigger for queue1 2Enabled 

![Enrollment](Images/tri5.png)

  
# 4. Create Two Lambda Functions:
 
  Lambda functions to process events triggered by S3 uploads or messages sent to SQS queues.

  Ensure that Lambda functions are appropriately configured with the necessary permissions to interact with other AWS services.
  
  ![Enrollment](Images/role5.png)
  
  
  # ![Enrollment](Images/role6.png)

  In the Code Section of your lambda function: replace line 4 of code = print(json.dumps(event)) and Deploy.Thses should be repeated on both        lambda function.

 # ![Enrollment](Images/function.png)
  

# 5. Configure IAM Permissions:

  Define IAM policies to grant appropriate permissions to Lambda functions.

  **Policy:**

  ![Enrollment](Images/Policy1.png)
  
  Select JSON and edit with the Lambda_Policy Provide.
  
  Replace all item in the <>. which includes region and so on. 
  
  This should also be repeated for the second Policy as show in the image below.

  **Policy 1**
  
  ![Enrollment](Images/Policy2.png)

  **Policy 2**
  ![Enrollment](Images/Policy3.png)

  Name and Create Policy 1
  ![Enrollment](Images/Policy4.png)

  Name and Create Policy 2
  ![Enrollment](Images/Policy5.png)

 # **IAM Role for Lambda function**
 
  Remember to Create 2 roles for your 2 Lambda functions.

  Repeat all Procedures for the second Lambda Role

  Select Role from IAM and create Role
  
  ![Enrollment](Images/role1.png)

  Select trusted entity and use Case
  
  ![Enrollment](Images/role2.png)

  Add Permissions : Choose from the the policy you created. 
  
  ![Enrollment](Images/role3.png)

  Name, Review and Create Role.
  
 # ![Enrollment](Images/role4.png)
  

# 6. Test the System:

  Upload objects to the S3 bucket to trigger events to the SQS queues to test the event-driven architecture.
  
  Add File to your bucket
  
  ![Enrollment](Images/Upload.png)

  Upload Sucessful 
  
  ![Enrollment](Images/upload1.png)

  Confirm your SQS trigger and Select Monitor to view
  
  ![Enrollment](Images/upload2.png)

  Select Cloudwatch to view Logs
  
  ![Enrollment](Images/upload3.png)

  Select file in Log streams 
  
  ![Enrollment](Images/upload4.png)

  Report:
  # ![Enrollment](Images/upload6.png)


**Copy objects to the S3 bucket to trigger events o the SQS queues to test the event-driven architecture.**

  Select file to be copied, Click Action and Choose Copy
  
  ![Enrollment](Images/copyy1.png)

  Destination for Copy is S3://<bucketname>/filename

  in this case is used /new/ as filename then select Copy
  
  ![Enrollment](Images/Copy2.png)

  Copy Confirmation
  
  ![Enrollment](Images/Copy3.png)

  Repeat procedure to confirm your sqs trigger and Select monitor to view Cloudwatch Log.

  Report:
  ![Enrollment](Images/Copy4.png)

  Monitor the system's behaviour to ensure that events are processed correctly and notifications are triggered as expected.
