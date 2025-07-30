pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/manikanta63043/jenkins-web-app.git'
            }
        }

        stage('Docker Compose Down (Cleanup)') {
            steps {
                sh 'docker-compose down || true'
            }
        }

        stage('Pull Images from Docker Hub') {
            steps {
                sh 'docker pull mani67890/multi-tier-backend:1.0'
                sh 'docker pull mani67890/multi-tier-frontend:1.0'
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed!'
        }
        success {
            echo 'Deployment successful!'
        }
    }
}
