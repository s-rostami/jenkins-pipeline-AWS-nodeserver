# jenkins-pipeline-AWS-nodeserver
___

In this project, jenkins pipeline is used to deploy a node server on an EC2 instance using cloudformation and an avalable custom image.

Tasks required for this project:

 - rolls
 - policy for cloudformation
 - jenkins worker + aws cli
 - cli and access ID
 - using an EC2 with jenkins installed already
 
 Steps:
 - Install Jenkins using marketplace AMI(Jenkins Certified by Bitnami), use t2.micro to avoid any charges
 - Takeing the user ID and password for the jenkins: the user ID is shown on the "Usage instruction" and for the password can be found on the EC2 system log which can be find under instance, monitor and trubleshooting and get system logs.
 - Login into the jenkins by opening new tab and using the public IP of the ec2 and the loging information.
 - Install cloudformation plugins for the jenkins
 
 

