pipeline {
    agent any
    
    environment {
        IP = '54.164.88.209'
    }
    
    stages {
        stage('EC2 Provision') {
            steps {
                sh 'aws cloudformation create-stack --stack-name jenkins-nodeserver --template-body file://ec2-node_server.yaml --region 'us-east-1' --capabilities CAPABILITY_IAM'
                }
            }
        stage('IP address look up') {
            steps {
                echo 'IP address look up'
                sh 'aws ec2 describe-instances --filters Name=tag-key ,Values=node-server --query "Reservations[*].Instances[*].PublicIpAddress" --output text'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
