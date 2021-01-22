pipeline {
    agent any
    stages {
        stage('Submit Stack') {
            steps {
                sh 'aws cloudformation create-stack --stack-name jenkins-nodeserver --template-body file://ec2-node_server.yaml --region 'us-east-1' --capabilities CAPABILITY_IAM'
              }
            }
        stage('ip address look-up'){
            steps {
                sh 'aws ec2 describe-instances --filters Name=tag-key ,Values=node-server --query "Reservations[*].Instances[*].PublicIpAddress" --output text'
              }
         }
      }
}
