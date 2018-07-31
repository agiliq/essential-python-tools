Amazon Web Services
-----------------------

`AWS <https://aws.amazon.com/>`_ is a cloud platform service from amazon, used to create and deploy any type of application in the cloud.

 AWS is a Cloud platform service offering compute power, data storage, and a wide array of other IT solutions and utilities for modern organizations. AWS was launched in 2006, and has since become one of the most popular cloud platforms currently available.

We should have an account in `AWS <https://aws.amazon.com/>`_ to use aws services.
It offers many featured services for compute, storage, networking, analytics, application services, deployment, identity and access management, directory services, security and many more cloud services.

To use AWS for python, check `https://aws.amazon.com/developer/language/python/ <https://aws.amazon.com/developer/language/python/>`_

We can use `Boto3 <https://github.com/boto/boto3>`_ (python package) which provides interfaces to Amazon Web Services, it makes us easy to integrate our Python application, library, or script with AWS services 

Boto3 is the Amazon Web Services (AWS) Software Development Kit (SDK) for Python, which allows Python developers to write software that makes use of services like Amazon S3(Simple storage service) and Amazon EC2(Elastic Compute Cloud). 
 
.. Boto provides an easy to use, object-oriented API as well as low-level direct service access.




Amazon Elastic Cloud Compute (EC2)
++++++++++++++++++++++++++++++++++++++++++
`Amazon Elastic Compute Cloud (Amazon EC2) <https://aws.amazon.com/ec2/>`_ is a web service that provides resizeable computing capacity.

We use Amazon EC2 to launch a virtual servers and also configure security , networking, and manage storage. It enables us to scale up or down depending the requirement.

+ It provides virtual computing environments called as `instances`
+ Various configurations of CPU, memory, storage, and networking capacity are available for our instances, known as instance types.





Amazon Elastic Beanstalk
++++++++++++++++++++++++++++++++++
`AWS Elastic Beanstalk <https://aws.amazon.com/elasticbeanstalk/>`_ is a service for deploying and scaling web applications and services.
Elastic Beanstalk will also run instances (Computing environments) EC2, and it has some additional components like Elastic Load Balancer, Auto-Scaling Group, Security Group.

We pay only for the EC2 instances or S3 buckets and aws-DB we use and the other features like Elastic Load Balancer, Auto-Scaling Group, Security Group in Elastic Beanstalk do not cost anything.





Amazon Lambda
++++++++++++++++++++++++++++++++++
`Amazon Lambda <https://aws.amazon.com/lambda/>`_ is a computing service which automatically manages the server. AWS Lambda executes our code only when needed and scales automatically, from a few requests per day to thousands per second.

We only pay for the compute time we comsume , and there will be no charge if the code is not running.

The initial purpose of lambda is to simplify building on-demand applications that are responsive to events.
AWS starts a Lambda instance within milliseconds of an event.




Deployment in AWS services:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Once we connect with the server using ssh , then the deployment will be same for all services. Which is same as in the example mentioned in the next chapter



.. A comparision of the aws-services
++++++++++++++++++++++++++++++++++++++++

