pipeline {
    agent any
    
    environment {
        IP = '54.164.88.209'
    }
    
    stages {
        stage('EC2 Provision') {
            steps {
                sh '''
                aws cloudformation create-stack --stack-name jenkins-nodeserver2 --template-body file://ec2-node_server.yaml --region 'us-east-1' --capabilities CAPABILITY_IAM
                aws ec2 wait instance-status-ok --filters "Name=instance-status.status,Values=initializing" --region 'us-east-1'
                '''
                }
            }
        stage('IP address look up') {
            steps {
                echo "IP = ${env.IP}"
                script {    
                    env.IP3 = sh(script:'aws ec2 describe-instances --filters "Name=tag:Name,Values=node_server3" --query Reservations[*].Instances[*].PublicIpAddress --region \'us-east-1\' --output text', returnStdout: true).trim()}
                echo "IP3 = ${env.IP3}"
                withEnv(["IP=foopbar"]){
                    echo "IP = ${env.IP}"
                }
            }
        }
        stage('SSH into EC2') {
            steps {
                sshagent (credentials: ['46c9fdad-0c60-4bec-9460-38cd3ffcca40']) {
                    sh 'ssh -o StrictHostKeyChecking=no -l ubuntu ${env.IP3} uname -a'
                    }
                }
            }
        stage('build image') {
            steps {
                echo 'creating an image'
                sh "aws ec2 create-image --instance-id i-04edd61f33d1320e2 --name 'My Jenkins Server Image' --region 'us-east-1'"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
