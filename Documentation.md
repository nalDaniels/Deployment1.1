# Purpose of Deployment
To familiarize myself with using Jenkins for the CI pipeline and deploying applications with AWS Elastic Beanstalk. The application files had an error in them, so I was also able to learn how to look through the logs on AWS Elastic Beanstalk to identify and resolve the issue.

# Steps to Production
## 1. Using Jenkins to build and test application
I downloaded the files from the Kura Labs repository and uploaded them to my newly created repository. I       then connected my repository to Jenkins and ran the pipeline. The build was successful. 

The console output for build shows that it is installing the required packages. The test phase ran a test on the code and it outputted the results to a file. 

I then created the roles so that Elastic Beanstalk can set up the cloud infrastructure and EC2 can interact with other AWS resources. 

I created the application on Elastic Beanstalk and used the roles I made available to the application, so that it can use other AWS services. Additionally, I selected the default VPC and selected an availability zone for my EC2 instance, which was also configured to be a t2.micro with 10GB of volume. 

Elastic Beanstalk then created my application with a degraded health status. I got an error for a 502 bad gateway on the nginx server. 

Looking for the issue

I looked at the last 100 lines of the log files, and I noticed a repeated error “ModuleNotFoundError: No module named application.” I assume this is in reference to the [app.py](http://app.py) file - which it contains the code for the application, so I am going to rename it to application.py. 

Deploy

I selected “upload and deploy” to update the zipped file that was being deployed. I
