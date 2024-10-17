pipeline {
    agent any

        environment {
        EC2_IP = '3.86.67.65'
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
                sshagent([SSH_CREDENTIALS]) {
                    sh '''scp -o StrictHostKeyChecking=no index.html ubuntu@${EC2_IP}:${REMOTE_DIR}'''
                }
            }
        }
    }
}
 post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
