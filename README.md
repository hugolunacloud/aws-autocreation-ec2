# aws-autocreation-ec2

Creating a Lambda function to automate the process of creating EC2 instances on AWS can save time and increase efficiency in business operations. This can be especially useful for businesses that require frequent scaling of their infrastructure, such as e-commerce websites or SaaS platforms. By automating the creation of EC2 instances, businesses can quickly respond to changes in demand and optimize their resource allocation. Additionally, automating this process can reduce the potential for human error and improve overall system reliability.


Create a an SSH key to access the Ec2:
Creating an SSH key is important to securely access the EC2 instance in AWS. It provides a secure and efficient way to authenticate and connect.C2 instance

Access the AWS Console;
Go to the EC2 service;
Select the "Key Pairs" option in the side menu;
Click on "Create Key Pair";
Choose a name for the key and download the .pem file.




Create a Lambda function:


Access the AWS Console;
Go to the Lambda service;
Click on "Create Function";
Choose "Author from scratch";
Name the function and choose Python as the language;
Choose "Create a new role with basic Lambda permissions" in the "Execution role" option;
Click on "Create function".



Add permission to create EC2 instances:


When creating a Lambda function from scratch, it only comes with CloudWatch Recording authorization. If you want to create an EC2 instance using the Lambda function, you'll need to change the policy on AIM to allow for the necessary permissions in the JSON parameters.


On the Lambda function page, go to the "Permissions" tab;
Click on "Add permission";
Configure the following options:
Service: EC2;
Actions: All EC2 actions;
Resources: All resources;
Effect: Allow.


Insert the Python code into the Lambda function:

Before put the code on the function a small explanation about the code: 

import os and import boto3 import the os and boto3 modules, which will allow us to interact with the AWS services.
AMI = os.environ['AMI'], INSTANCE_TYPE = os.environ['INSTANCE_TYPE'], KEY_NAME = os.environ['KEY_NAME'], and SUBNET_ID = os.environ['SUBNET_ID'] set the values of the environment variables that were set up when the Lambda function was created. These environment variables are used to provide the necessary information for creating an EC2 instance, such as the AMI ID, instance type, key name, and subnet ID.
instance = ec2.create_instances(...) creates a new EC2 instance using the parameters defined in the environment variables.






On the Lambda function page, go to the "Function code" tab;
Insert the Python code that will create the EC2 instance, including the variables that define the instance type, operating system, etc.;
Save the changes.
Execute the Lambda function:
On the Lambda function page, click on "Test";
Configure the test options, such as the event name, and run;
Check if the EC2 instance was successfully created.




















































