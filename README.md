# Architect-and-build-end-to-end-aws-web-application
Deploy a web application using AWS Services. The web application calculates the exponent of a given number.

This repository containts code for architecting and deploying a web application using these aws services:
1. AWS Amplify
2. AWS Lambda
3. Amazon API Gateway
4. Amazon DynamoDB
5. AWS Identity & Access Management (IAM)

## STEP 1
### Website hosting using AWS Amplify

1. Navigate to AWS Amplify within AWS Console.

2. Select create new app and select the option "Deploy without Git provider"

![Amp1](https://github.com/user-attachments/assets/1ea65f23-aaba-4420-b146-0c8ce2a4cff4)

3. Upload html file for web page in zip format and select "Save and deploy"

![Amp2](https://github.com/user-attachments/assets/8349b1a0-bd09-48e3-b754-5e9de85a8ff4)

4. Once deployment is successful, click the url under "Domain" and this should be the output on your webpage.

![Amp3](https://github.com/user-attachments/assets/d49d4e4c-3ce7-4efb-962c-4eb883696cc1)

## STEP 2
### Upload code to perform mathematical function on AWS Lambda.
1. Navigate to AWS Lambda service, select "Create function" and select "author from scratch"

![Lambda1](https://github.com/user-attachments/assets/023cde30-e23f-46cd-9eb7-7bad7592bc78)

2. Create new python file and insert code into it. Select "Deploy" and then configure a test event using the drop down menu next to the test button.

![lambda-edit-1](https://github.com/user-attachments/assets/c919f02e-3c18-4617-a581-43040bd8371d)

3. Edit default event to suit the parameters of your code.

![lambda-edit-2](https://github.com/user-attachments/assets/4ea3b82c-21cb-41e8-8abe-14d0ddeae317)


4. Run test on your code to confirm its functionality.

![lambda3](https://github.com/user-attachments/assets/d928b8ed-a35a-46c1-9864-964961bb24de)

## STEP 3
### Create API using API Gateway
1. Navigate to API Gateway and create REST API.

![api1](https://github.com/user-attachments/assets/d5530851-019f-4de8-b94c-b4b7dc4f0360)

2. Within API resources, create method of the POST type and attach the previously created lambda function to the method.  

![api2](https://github.com/user-attachments/assets/8c111ed0-89f1-4834-b37b-8e25157b1968)

3. Enable CORS (Cross-origin resource sharing) to allow web application in one domain to access resources in another domain.(Web app is in one domain and Lambda is in another.)
![api3](https://github.com/user-attachments/assets/820e1b3b-07e9-40b3-a4ef-60edc2d44361)

4. Deploy API and save its Invoke URL
   
![api4](https://github.com/user-attachments/assets/669a57f9-cdfb-401b-9031-1b136242e47d)

6. Set parameters in the json section and test API.
   
 ![api5](https://github.com/user-attachments/assets/13a5b7cd-61c8-43a6-ba0d-66a8f07d6ba1)

## STEP 4
### Incorporate Database to store result using Dynamo DB

1. Navigate to DynamoDB and create table.
2. Take note of ARN of database.

## STEP 5
### To allow Lambda function write to Database table, we must use IAM to grant the permissions.

1. Navigate to Lambda. Select previously created function and then the "Configuration" tab. Then proceed to select the link under "Execution role". This would navigate to the IAM console.
![LAMBDA-IAM](https://github.com/user-attachments/assets/ea891147-4dca-40e7-b950-b325f30dac17)

2. Under Permissions tab choose Add permission and select "Create inline policy"

![IAM1](https://github.com/user-attachments/assets/a5190102-9a37-47f0-bb39-7a8ac2a7dc76)

3. Insert your own execution policy into the JSON section and substitute your database ARN into the JSON to grant your Lambda function access to your database then select review and then Create policy.

![IAM2](https://github.com/user-attachments/assets/99971d91-3004-423d-98ba-a1a3dbb8cb9b)

##  STEP 6
### Return to Lambda 

1. Edit code to include database functionality.(We will add the ability to write to the table and the time as well)

![lambda4newcode](https://github.com/user-attachments/assets/1e2b22dd-c5cc-45ac-be8d-caf0ece3556d)

2. Deploy and test Lambda function to confirm Lambda functionality.

![lambda5newcodetest](https://github.com/user-attachments/assets/c39a6857-a71e-40dd-a969-f82c3d58efe8)

3. Return to DynamoDB. Select previously created table and choose "Explore items". We have now verified that the results of running Lambda function is stored in Database.
 
![dynamo2check](https://github.com/user-attachments/assets/113afa5c-4bf4-46b8-a1f9-9062f241edec)

## STEP 7
### To connect Amplify and API gateway so app can access all other functionality.

1.  Substitute API's Invoke URL into HTML document previously used for the web app. 

![FINAL EDIT TO HTML](https://github.com/user-attachments/assets/be9595ca-dea5-4a5c-a089-cddf0e9a6687)

2. Zip, redeploy within AWS Amplify and run final functionality checks.

![RESULT](https://github.com/user-attachments/assets/74cb341a-f9ae-4e9b-b7de-500a0901897b)



   
