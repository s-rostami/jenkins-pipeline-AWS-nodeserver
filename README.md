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
 - Create a new free style job
 - define the github repository which contains the cloudformation template file and also the branch.
 - under the build enviroment section, aws cloudformation stack creation selected and the name of the template was defined.
 - jenkins calls the cloudformation api using access key and the secret key. So to minimize the security risk, new IAM user was created which has only access to cloudformation and S3 bucket. 
 - jenkins pipeline needs AWS CLI to run the cloudformation. there are two methods avalble to install AWS CLI on the jenkins instance:
   1- SSH into the instance and install AWS CLI
   2- use ssh AWS system session manager 
   
 - make sure ssm agent is installed on the ec2 instance
 - add ssm policy to the role
 
 - ssh connect to the instance and install awscli and then check the cli with "aws configure"
 - update the policies of the jenkins server ec2 role and add cloudformation and s3 policies
 - Jenkinsfile: aws cli commands for creation of the stack needs to be defined in this file.
 - in the cloudformation template, a new role for access to dynamodb database is created. 
 - due to creating the new role, CAPABILITY_IAM was added to the cli command line in jenkins file.
 changed
 
 

