pipeline {
    agent any
    
    environment {
        IP = '54.164.88.209'
    }
    
    stages {
        stage('EC2 Provision') {
            steps {
                sh '''aws cloudformation create-stack --stack-name jenkins-nodeserver1 --template-body file://ec2-node_server.yaml --region 'us-east-1' --capabilities CAPABILITY_IAM'''
                }
            }
        stage('IP address look up') {
            steps {
                echo 'IP address look up'
                sh '''aws ec2 describe-addresses --filters "Name=tag-key,Values=node-server" --region 'us-east-1' --output text'''
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
