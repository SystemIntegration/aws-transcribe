# AWS Transcribe Service Configuration with CloudFormation, Lambda Function, and S3 Bucket Trigger

This guide will walk you through the process of setting up AWS Transcribe service to automatically transcribe audio files uploaded to an S3 bucket using a Lambda function defined as Infrastructure as Code (IAC) using CloudFormation, and triggered by S3 events.

### Prerequisites
Before you begin, make sure you have the following:
An AWS account.
AWS CLI installed and configured with necessary permissions.
Audio files that you want to transcribe.
Basic understanding of AWS services.
### Steps

1. Create an S3 Bucket
    1.1. Open the AWS Management Console.
    1.2. Navigate to the S3 service.
    1.3. Click on "Create bucket" and follow the prompts to create a new bucket. Choose a unique name and the appropriate region.

2. Define Lambda Function in CloudFormation
    2.1. Download a CloudFormation template “transcribe.yml” from the repository.

3. Upload Lambda Function Code to S3
    3.1. Copy code from the repository file name. “lambda_function.py”
    3.2. Create a ZIP package of your Lambda function code (e.g., lambda_function.zip).
    3.3. Upload the ZIP package to the S3 bucket you specified in the CloudFormation template.

4. Create CloudFormation Stack
    4.1. Open the AWS Management Console.
    4.2. Navigate to the CloudFormation service.
    4.3. Click on "Create stack".
    4.4. Choose "Upload a template file" and upload the “transcribe.yml” template you Downloaded.
    4.5. Follow the prompts to create the stack. 

5. Configure S3 Trigger
    5.1. Once the CloudFormation stack is created, navigate to the Lambda function you just created.
    5.2. Add a trigger to the Lambda function.
    5.3. Choose "S3" as the trigger type.
    5.4. Configure the trigger:
    - Bucket: Select the S3 bucket you created earlier.
    - Event type: Choose "All object create events".
    - Prefix: Leave this field empty to trigger on all object creations.
    
    5.5. Click on "Add" to add the trigger.
    
### Usage
- Upload audio files to the configured S3 bucket.
- The Lambda function defined in the CloudFormation stack will be triggered automatically for each uploaded file.
- The Lambda function will start a Transcribe job for each file.
- Monitor the progress of transcription jobs in the AWS Transcribe console.
### Cleanup
- Remember to clean up your resources if you no longer need them to avoid incurring unnecessary charges.

As always, adapt the instructions to your specific requirements and refer to AWS documentation for the most up-to-date guidance.








