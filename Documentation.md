# Purpose of Deployment
To familiarize myself with using Jenkins for the CI pipeline and deploying applications with AWS Elastic Beanstalk. The application files had an error in them, so I was also able to learn how to look through the logs on AWS Elastic Beanstalk to identify and resolve the issue.

# Steps to Production
## 1. Using Jenkins to build and test application
I downloaded the files from the Kura Labs repository and uploaded them to my newly created repository. I, then, connected my repository to Jenkins and ran the pipeline. The build was successful. 

The console output for the build shows that it is installing the required packages. The test phase ran a test on the code, and it outputted the results to a file. 

## 2. Deploying Application using AWS Elastic Beanstalk
I then created the roles, so that Elastic Beanstalk can set up the cloud infrastructure and EC2 can interact with other AWS resources. 

I created the application on Elastic Beanstalk and used the roles I previously made available to the application, so that it can use other AWS services. Additionally, I selected the default VPC and selected an availability zone for my EC2 instance, which was also configured to be a t2.micro with 10GB of volume. 

Elastic Beanstalk then created my application with degraded health status. I got an error for a 502 bad gateway on the Nginx server. 

## 3. Looking for the issue

I looked at the last 100 lines of the log files, and I noticed an error “ModuleNotFoundError: No module named application.” This means that the application files are pointing to a file named application; however, there is no file named application. I assume this is in reference to the app.py file - which contains the application code, so I renamed it to application.py. 

<img width="1219" alt="Screen Shot 2023-08-16 at 9 50 40 PM" src="https://github.com/nalDaniels/Deployment1.1/assets/135375665/25d24d99-bfd4-44e3-a27d-4f7730431853">


## 4. Re-Deploy

I selected “upload and deploy” to update the zipped file that was being deployed. The deployment was successful

<img width="906" alt="Screen Shot 2023-08-15 at 9 04 22 PM" src="https://github.com/nalDaniels/Deployment1.1/assets/135375665/317e2afe-f1e7-458e-be01-ab3c57484f0f">

# Deployment 1.1 CI/CD Pipeline
![_Plan - Deployment 1 1 drawio](https://github.com/nalDaniels/Deployment1.1/assets/135375665/1662903d-4411-4f2a-813d-1ab1306b2116)

