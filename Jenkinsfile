pipeline {
    agent any

        environment {
        EC2_IP = '54.224.111.208'
        SSH_CREDENTIALS = 'ec2-ssh-credentials'
        REMOTE_DIR = '/var/www/html/'
    }
    stages {
        stage('Pull from GitHub') {
            steps {
                git branch: 'main', url: 'https://github.com/ashiknay33/Reception-Invitation.git'
            }
        }
        stage('Deploy to EC2') {
            steps {
                shagent([SSH_CREDENTIALS]) {
                    sh '''scp -o StrictHostKeyChecking=no index.html ububtu@${EC2_IP}:${REMOTE_DIR}'''
                }
            }
        }
    }
}

