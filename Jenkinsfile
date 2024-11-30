pipeline {
    agent any
    environment {
        DOCKER_TAG = 'mishan202/nodeapp:v2' // Replace with your Docker image tag
    }

    stages {
        stage('SCM Checkout') {
            steps {
                retry(3) {
                    git branch: 'main', url: 'https://github.com/Mishan20/GitHub-Docker-and-Jenkins-CI-CD-Pipeline.git'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                sh '/usr/local/bin/docker build -t mishan202/nodeapp-cuban:${BUILD_NUMBER} .'
            }
        }
    }

    post {
        always {
            sh 'docker logout || echo "Logout failed (non-critical)"'
        }
    }
}