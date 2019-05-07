# Lab Guide #

This lab guide is prepared to assist you ingest, store, transform, create insights on unstructured data using AWS serverless services. Most of the demos make use of AWS Console, however all the labs can be automated via Cloudformation templates, AWS CLI or AWS API.

## Lab Pre-requisites

In order to complete this immersion day lab, please follow the preparation steps:

### You have Administrator rights on your account

#### 1. Install Kinesis Data Generator (KDG) tool

  Launch the KDG tool in your account using the following link:

  <a href="https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=Kinesis-Data-Generator-Cognito-User&templateURL=https://s3-us-west-2.amazonaws.com/kinesis-helpers/cognito-setup.json" target="_blank"><img src="../images/launchStack.svg" /></a>

  Follow the KDG Guide on https://awslabs.github.io/amazon-kinesis-data-generator/web/help.html to install and configure the KDG on your AWS account. You simply need to use the CloudFormation template to create KDG to us-west-2 (Oregon) region.  (Note: If multiple persons are joining the immersion day from the same company, it is sufficient one creates this stack, and shares the user/passwd with the team members).

#### 2. Create roles and policies for use in later labs

  We prepared a CloudFormation template that creates the IAM roles and policies you’d need to run the labs.
  
  Launch the roles CloudFormation stack in your account using the following link:

  <a href="https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=<yourintials>-sdlimmersion" target="_blank"><img src="../images/launchStack.svg" /></a>

  For the Choose a template option select **"Upload a template to S3"** and upload the template "serverlessDataLakeImmersionIAMcfPA16.json" from the scripts folder of this repository. 

  ![Upload template](../images/templateUpload.png)

  For the stack name update: &lt;yourinitials&gt;-sdlimmersion with your initials (e.g. fs-sdlimmersion for Frank Sinatra).

  ![Upload template](../images/rolesStackName.png)

### You *do not* have Administrator rights on your account

Work with an administrator in your account and complete requirements in the Lab Prep document.
 
## Expected Costs

You are responsible for the cost of the AWS services used while running this lab. As of the date of publication, the baseline cost for running this solution as-is should be around:
  - Kinesis Firehose: < 1$
  -	Athena: < 5$
  -	Glue < 1 $
  -	S3 < 1$ 
  -	Glue Deveper Endpoint < 2 $  (Glue Pricing is 0.44 per DPU-Hour, billed per second, with a 10-minute minimum for each provisioned development endpoint)
  -	Sagemaker Notebook < 2$

Important note: 
-	Glue Developer Endpoint: Billing for a development endpoint is based on the Data Processing Unit (DPU) hours used during the entire time it remains in the READY state. To stop charges, delete the endpoint. To delete, choose the endpoint in the list, and then choose Action, Delete.

Cost Management advice: Whenever you are creating a cloud resource, tag it. Try setting following tag fields during the labs:
-	project: serverlessdatalake
-	costcenter: awsimmersionday
