pipeline {
    agent any
    stages {
        stage('Pull from GitHub') {
            steps {
                git branch: 'main', url: 'https://github.com/ashiknay33/Reception-Invitation.git'
            }
        }
        stage('Deploy to EC2') {
            steps {
                sshagent(['ec2-ssh-credentials']) {
                    sh '''scp -o StrictHostKeyChecking=no index.html ec2-user@3.91.235.155:/var/www/html/index.html'''
                }
            }
        }
    }
}

