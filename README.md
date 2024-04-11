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

**IAM Permissions:** IAM (Identity and Access Management) permissions are configured to grant appropriate access to the necessary AWS resources for the Lambda functions and other components.

# step-by-step instructions for setting up the event-driven architecture on AWS:

# 1. Set Up Amazon S3 Bucket:
 
Create an Amazon S3 bucket.

# 2. Create an Amazon SNS Topic:
 
Create an Amazon SNS topic.

# 3. Create Amazon SQS Queues:
 
Create two Amazon SQS queues.

# 4. Create Two Lambda Functions:
 
Develop or configure Lambda functions to process events triggered by S3 uploads or messages sent to SQS queues.

Ensure that Lambda functions are appropriately configured with the necessary permissions to interact with other AWS services.

# 5. Configure IAM Permissions:

Define IAM policies to grant appropriate permissions to Lambda functions and other components.

Follow the principle of least privilege to ensure that each component has only the necessary permissions to perform its tasks.

# 6. Test the System:

Upload objects to the S3 bucket to trigger events or send messages to the SQS queues to test the event-driven architecture.

Monitor the system's behaviour to ensure that events are processed correctly and notifications are triggered as expected.
