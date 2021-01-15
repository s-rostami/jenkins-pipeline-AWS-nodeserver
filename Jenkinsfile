pipeline {
    agent any
    stages {
        stage('Submit Stack') {
            steps {
            sh "aws cloudformation create-stack --stack-name jenkins-nodeserver --template-body file://ec2-node_server.yaml --region 'us-east-1' --capabilities CAPABILITY_IAM"
              }
             }
            }
            }
